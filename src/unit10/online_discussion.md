Unit 10 Discussion Forum: OpenFaaS

Task:

Implement a serverless function using OpenFaaS (an open-source serverless platform). Develop and deploy a simple function (e.g., a greeting service or a calculator) and explore how serverless architecture optimises cloud operations.

Deliverable: A technical discussion of how you deployed the serverless function using OpenFaaS, along with the function code.

-----------------------------

Number of replies: 0
This task involved implementing and deploying a serverless greeting function using OpenFaaS, an open-source Function-as-a-Service (FaaS) platform designed for cloud-native environments. OpenFaaS enables developers to package functions as containers and deploy them via a gateway, abstracting infrastructure management while maintaining portability across platforms (OpenFaaS, 2024a).

The deployment began by installing OpenFaaS on a Kubernetes cluster using Helm. After authenticating with the faas-cli, a new function was created using the Python Flask template:

faas-cli new greet --lang python3-flask-debian

This generated the handler and YAML configuration files. The function logic was implemented in handler.py, returning a personalised greeting. The YAML file was configured with the container image and registry details, after which the function was built and deployed:

faas-cli up -f greet.yml

The function became accessible via the OpenFaaS gateway and could be invoked through HTTP requests. This highlights how serverless platforms simplify deployment by abstracting infrastructure concerns, allowing developers to focus solely on application logic.

From a cloud operations perspective, OpenFaaS demonstrates key advantages of serverless architecture. Firstly, it supports event-driven execution, ensuring compute resources are utilised only when required, improving cost efficiency. Secondly, it provides auto-scaling mechanisms based on request rate and CPU utilisation, enabling dynamic adaptation to workload demand (OpenFaaS, 2024b). This contrasts with traditional virtual machine provisioning, where resources are often statically allocated and underutilised.

Critically, compared with services such as Amazon Lambda, OpenFaaS offers greater control and portability due to its container-based model, making it suitable for hybrid or on-premise deployments. However, this flexibility comes at the cost of increased operational responsibility, as users must manage the underlying Kubernetes infrastructure. Additionally, serverless platforms can suffer from cold start latency, which may impact performance for latency-sensitive applications (Jonas et al., 2023).

Despite these limitations, serverless computing significantly reduces operational overhead and accelerates development cycles. Recent cloud-native research emphasises that serverless architectures enhance scalability, resilience, and resource efficiency, making them a key paradigm in modern cloud operations (CNCF, 2025). Overall, this implementation demonstrates that OpenFaaS provides an effective balance between flexibility and automation, optimising both deployment and operational efficiency.

_______________________________________________

Function Code (handler.py)

def handle(req):

    name = req.strip() if req.strip() else "student"

    return f"Hello, {name}. Welcome to OpenFaaS!"

_______________________________________________

References:

CNCF (2025) Cloud Native Annual Survey 2024.

Jonas, E., Schleier-Smith, J., Sreekanti, V., Tsai, C. et al. (2023) Cloud Programming Simplified: A Berkeley View on Serverless Computing.

OpenFaaS (2024a) OpenFaaS Documentation. Available at: https://docs.openfaas.com/

OpenFaaS (2024b) Autoscaling Functions in OpenFaaS. Available at: https://docs.openfaas.com/architecture/autoscaling/

