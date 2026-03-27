Unit 7 Formative Discussion: Security Audit

Task:

Perform a security audit of a cloud application deployed on OpenStack using OpenVAS (an open-source vulnerability scanner). Identify security risks and suggest mitigations based on industry standards such as ISO/IEC 27001.

Deliverable: Post an outline of a security audit, detailing the vulnerabilities found, any mitigation strategies, and compliance adherence recommendations.

---------------------
My post:

A security audit was conducted on a cloud-based application deployed within an OpenStack environment using OpenVAS, an open-source vulnerability scanning tool. The purpose of this audit was to identify potential vulnerabilities within the cloud infrastructure and evaluate mitigation strategies in line with recognised security standards such as ISO/IEC 27001 and regulatory requirements including the General Data Protection Regulation (GDPR).

The OpenVAS scan identified several security risks. One key issue was the presence of unnecessary open ports, including SSH (port 22) and HTTP (port 80), which increase the system’s attack surface. If these services are not properly restricted, attackers may attempt brute-force attacks or exploit network services. This risk can be mitigated by implementing stricter firewall rules and OpenStack security groups, restricting access to authorised IP addresses and applying the principle of least privilege.

Another vulnerability identified was outdated software packages running on the virtual machine. Unpatched systems often contain known vulnerabilities that attackers can exploit. Regular patch management, automated updates and vulnerability monitoring are therefore necessary to reduce exposure to security threats.

The audit also identified reliance on password-based authentication without additional security controls. Implementing multi-factor authentication (MFA) and stronger identity and access management policies would significantly improve system security and reduce the likelihood of credential-based attacks.


From a compliance perspective, these mitigation measures align with ISO/IEC 27001 security controls, particularly those relating to access control, cryptography and operational security. Additionally, implementing encryption and strong access management supports GDPR Article 32, which requires organisations to implement appropriate technical and organisational measures to protect personal data (European Union, 2016).


Overall, this audit demonstrates that vulnerability scanning tools such as OpenVAS are valuable for identifying security weaknesses in cloud environments. Continuous monitoring, proper configuration management and adherence to recognised security frameworks are essential for maintaining a secure and compliant cloud infrastructure.

References

European Union (2016) General Data Protection Regulation (GDPR). 

International Organization for Standardization (2022) ISO/IEC 27001:2022 Information security, cybersecurity and privacy protection — Information security management systems. Geneva: ISO.

NIST (2020) Security and Privacy Controls for Information Systems and Organizations (SP 800-53). Gaithersburg: National Institute of Standards and Technology.

OpenVAS (2024) OpenVAS vulnerability scanner documentation. 
