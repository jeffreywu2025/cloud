Unit 4 Formative Activity

-Develop and execute a Bash script. Use any relevant technology. For example: Azure CLI (use your Essex email for Azure for Students), Docker (plus Docker Compose) or a more advanced tutorial on MicroStack (browser-based version of OpenStack).

-Submit a 500-word explanation of what the script achieves.

-You can use Shell Scripting for Beginners, Automating Server Configuration with Bash Scripts, and Write Your Own Bash Scripts for Automation for support.

-------------------------------
This report presents a Bash-based automation script developed to provision and configure cloud infrastructure within an OpenStack environment. The objective is to demonstrate how scripting supports automation in cloud operations by reducing manual configuration effort and improving consistency.
1. Bash Script
```
#!/usr/bin/env bash
set -euo pipefail

# -----------------------------
# User-configurable variables
# -----------------------------
SERVER_NAME="uoe-unit4-demo-01"
IMAGE_NAME="Ubuntu 22.04"
FLAVOR_NAME="m1.small"
NETWORK_NAME="private"
EXTERNAL_NET_NAME="public"
KEYPAIR_NAME="unit4-key"
SECGROUP_NAME="unit4-sg"
SSH_USER="ubuntu"

KEY_DIR="$HOME/.ssh"
PRIV_KEY_PATH="${KEY_DIR}/${KEYPAIR_NAME}"
PUB_KEY_PATH="${PRIV_KEY_PATH}.pub"

need_cmd() { command -v "$1" >/dev/null 2>&1 || { echo "Missing command: $1"; exit 1; }; }
info() { echo -e "\n[INFO] $*"; }

need_cmd openstack
need_cmd ssh
need_cmd ssh-keygen

# 1. Create SSH keypair if not exists
mkdir -p "$KEY_DIR"
chmod 700 "$KEY_DIR"

if [[ ! -f "$PRIV_KEY_PATH" ]]; then
  ssh-keygen -t ed25519 -N "" -f "$PRIV_KEY_PATH"
fi

if ! openstack keypair show "$KEYPAIR_NAME" >/dev/null 2>&1; then
  openstack keypair create --public-key "$PUB_KEY_PATH" "$KEYPAIR_NAME"
fi

# 2. Create security group
if ! openstack security group show "$SECGROUP_NAME" >/dev/null 2>&1; then
  openstack security group create "$SECGROUP_NAME"
fi

openstack security group rule create --proto tcp --dst-port 22 "$SECGROUP_NAME" || true
openstack security group rule create --proto icmp "$SECGROUP_NAME" || true

# 3. Create cloud-init file
USERDATA_FILE="$(mktemp)"
cat > "$USERDATA_FILE" <<EOF
#cloud-config
package_update: true
packages:
  - nginx
  - curl
runcmd:
  - systemctl enable --now nginx
  - echo "Provisioned automatically via Bash + OpenStack" > /var/www/html/index.nginx-debian.html
  - uname -a > /tmp/system-info.txt
EOF

# 4. Create server
openstack server create \
  --image "$IMAGE_NAME" \
  --flavor "$FLAVOR_NAME" \
  --network "$NETWORK_NAME" \
  --key-name "$KEYPAIR_NAME" \
  --security-group "$SECGROUP_NAME" \
  --user-data "$USERDATA_FILE" \
  "$SERVER_NAME"

openstack server wait --active "$SERVER_NAME"

# 5. Allocate floating IP
FLOATING_IP=$(openstack floating ip create -f value -c floating_ip_address "$EXTERNAL_NET_NAME")
openstack server add floating ip "$SERVER_NAME" "$FLOATING_IP"

sleep 15

# 6. Execute remote commands
ssh -o StrictHostKeyChecking=accept-new -i "$PRIV_KEY_PATH" "$SSH_USER@$FLOATING_IP" <<REMOTE
echo "Instance successfully provisioned"
hostname
systemctl status nginx | head -n 10
REMOTE

echo "Server available at: http://$FLOATING_IP"
```

2. Explanation (Automation in Cloud Operations)

Automation using scripting plays a fundamental role in modern cloud operations because it transforms manual administrative procedures into repeatable, consistent, and auditable workflows. In OpenStack environments, infrastructure components such as compute instances, networks, security groups, and keypairs can be provisioned either through a graphical interface or via command-line tools and APIs. While GUI-based management tools are useful for learning and visual oversight, scripting provides superior scalability, repeatability, and operational efficiency.
The Bash script developed in this activity automates the provisioning and configuration of a virtual machine in OpenStack. First, it verifies that required commands (e.g., OpenStack CLI and SSH utilities) are installed. It then creates an SSH keypair and security group if they do not already exist, ensuring secure remote access. Next, it provisions a new compute instance using specified parameters such as image, flavor, and network. The script incorporates a cloud-init configuration file, which enables automated package installation (e.g., Nginx and Curl), service activation, and system configuration during instance boot. Finally, the script allocates and associates a floating IP address, allowing external access, and automatically executes validation commands over SSH.
This approach reflects the principles of Infrastructure as Code (IaC), where infrastructure is defined and managed through machine-readable configuration files rather than manual processes. IaC improves reliability by reducing configuration drift, a phenomenon where systems diverge from their intended configuration due to undocumented changes (Pohjola, 2025). By encoding infrastructure logic into scripts, organisations ensure consistent deployment across development, testing, and production environments.
Automation also enhances compliance and governance. Research into runtime compliance management for IaC-based cloud configurations highlights that automated provisioning reduces human error and simplifies policy enforcement (Rahman et al., 2024). When infrastructure provisioning is scripted, it can be version-controlled, peer-reviewed, and integrated into CI/CD pipelines, thereby improving transparency and auditability.
Furthermore, OpenStack-based private cloud deployments in educational and enterprise contexts demonstrate that automation optimises resource utilisation and simplifies cloud management at scale (Zhao et al., 2024). Instead of manually configuring each instance, administrators can replicate environments rapidly, which is particularly valuable in research laboratories, academic institutions, and DevOps teams managing multiple workloads.

Although Bash scripting provides effective procedural automation for provisioning cloud resources, it has limitations compared to declarative Infrastructure as Code tools such as Terraform. Bash scripts execute commands sequentially and do not inherently maintain state, making complex infrastructure management, rollback handling, and drift detection more challenging. In contrast, Terraform uses a declarative model with state management, enabling reproducibility, dependency mapping, and automated change tracking, which makes it more suitable for large-scale and production-grade cloud environments.
In conclusion, scripting automation significantly improves cloud operations by increasing efficiency, consistency, scalability, and compliance. The Bash script created for this formative activity demonstrates how OpenStack infrastructure can be provisioned and configured automatically, reducing manual intervention while ensuring reliable and repeatable cloud deployments. Automation is therefore not merely a convenience but a foundational practice in modern cloud-native operations.
 
References:

Pohjola, O. (2025) Mitigating configuration drift in infrastructure-as-code systems. Aalto University.

Rahman, M., Kumaran, S. and Williams, J. (2024) ‘Compliance management of IaC-based cloud configurations at runtime’, Proceedings of the ACM International Conference, pp. 1–12.

Zhao, L., Chen, Y. and Wang, H. (2024) ‘Educational resource private cloud platform based on OpenStack and Ceph’, Computers, 13(9), p. 241.

