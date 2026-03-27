Unit 6 Development Team Project: Cloud Infrastructure and Framework Report

Coursework Task

In groups of 3-4, students are to select a specific cloud infrastructure framework (e.g., AWS CloudFormation, Microsoft Azure Resource Manager, Google Cloud Deployment Manager) and create a report addressing the following:

1.Overview: Briefly describe the chosen cloud framework, highlighting its core features and purpose.

2.Service Model Analysis: Explain how the framework supports different cloud service models (e.g., IaaS, PaaS, SaaS).

3.Deployment Types: Discuss how the framework can be applied across public, private, and hybrid cloud environments.

4.Infrastructure Design: Outline the steps for designing a basic infrastructure using the chosen framework, including key components (compute, storage, networking).

5.Case Study or Real-World Example: Provide a real-world example where this framework was used and evaluate its impact on organisational efficiency and cost.

-------------------
1. Overview

AWS CloudFormation is an Infrastructure as Code (IaC) service that enables organisations to define and manage cloud infrastructure using YAML or JSON templates rather than manual configuration. These templates describe AWS resources and their relationships, allowing environments to be provisioned automatically and consistently.
CloudFormation introduces repeatability and governance into infrastructure deployment. Manual provisioning in complex environments can lead to configuration drift, inconsistent security settings, and undocumented changes. Misconfigurations remain a significant cause of cloud security incidents (Hashizume et al., 2013). By defining infrastructure declaratively, CloudFormation embeds change control within version-managed templates, improving traceability and reducing risk.
It also supports lifecycle management through stack updates and automated rollback mechanisms. This aligns with NIST cloud characteristics such as measured service and rapid elasticity (Mell and Grance, 2011). By ensuring infrastructure changes are predictable and auditable, CloudFormation strengthens governance and compliance.
CloudFormation integrates with version control systems and CI/CD pipelines, positioning it within DevOps practices. Treating infrastructure as code alongside application logic enables automated releases and consistent configuration across environments.

2. Service Model Analysis

CloudFormation operates across the three cloud service models defined by NIST: Infrastructure as a Service (IaaS), Platform as a Service (PaaS), and Software as a Service (SaaS) (Mell and Grance, 2011). Its strongest alignment is with IaaS.
At the IaaS layer, CloudFormation provisions core resources including virtual machines, storage, networking, and identity controls. IaaS provides consumers with control over operating systems and applications while abstracting physical infrastructure (Mell and Grance, 2011). CloudFormation enhances this model by transforming infrastructure management into a repeatable, version-controlled process, improving consistency and auditability.
CloudFormation also automates deployment of PaaS services such as managed databases and serverless functions. PaaS abstracts infrastructure management so developers can focus on application logic (Zhang, Cheng and Boutaba, 2010). While CloudFormation does not provide a platform itself, it orchestrates these services within structured templates.
Regarding SaaS, CloudFormation provisions infrastructure required to support SaaS architectures, including load balancing and monitoring. Its relationship to SaaS is infrastructural rather than service-defining.

3. Deployment Types: Public, Private and Hybrid

AWS CloudFormation provisions public cloud resources such as EC2, S3, VPC and RDS declaratively using JSON or YAML templates (AWS, 2024). This infrastructure-as-code (IaC) model standardises configuration, reduces drift and enables version-controlled deployments supporting scalable services. Research indicates structured IaC adoption improves reliability and reduces risk when supported by governance maturity models (Mora et al., 2024). However, cost optimisation and resilience depend on disciplined template design, as poorly modularised configurations can propagate inefficiencies and architectural antipatterns (Neamt, 2024).

Although AWS does not offer a traditional on-premises private cloud, CloudFormation supports private-like environments through VPC isolation, dedicated hosts and AWS Outposts, extending services into customer data centres while maintaining lifecycle control (AWS, 2025a). Outposts addresses data-residency and latency requirements without sacrificing automation consistency. Nevertheless, its AWS-native architecture may constrain interoperability compared with IaC alternatives like Terraform, reinforcing provider dependency within multi-cloud strategies (Neamt, 2024).

In hybrid contexts, CloudFormation orchestrates AWS resources alongside on-premises systems via Site-to-Site VPN or Direct Connect within unified templates defining networking, routing and IAM policies. Hybrid effectiveness depends on organisational DevOps maturity and policy-as-code integration; without structured governance, automation may formalise silos rather than eliminate them (Mora et al., 2024; Multi-IaC-Eval, 2025).

4. Infrastructure Design Using AWS CloudFormation

Infrastructure design begins with a JSON or YAML template defining parameters, resources and outputs, enabling version-controlled stack deployment and CI/CD integration (AWS, 2024).

The networking layer establishes a VPC with public and private subnets, an Internet Gateway, route tables and security groups enforcing isolation and traffic controls. Compute resources such as EC2 instances or Auto Scaling groups are deployed within defined subnets alongside IAM roles implementing least-privilege access.

Storage components, including S3 buckets and RDS instances, embed encryption, backup and retention policies within templates to ensure compliance consistency. CloudWatch alarms and stack outputs enhance operational visibility. While this template-driven approach reduces manual errors, sustained effectiveness requires review pipelines and governance processes preventing configuration drift in large-scale, multi-team environments (Mora et al., 2024; Multi-IaC-Eval, 2025).

5. Case Study or Real World Example 

A clear real-world application of AWS CloudFormation is demonstrated in GoDaddy’s cloud migration strategy and the development of its Public Cloud Portal. As part of its transition to AWS, GoDaddy implemented CloudFormation alongside AWS Service Catalog and Systems Manager to automate the creation of standardised landing zones and multi-account architectures (GoDaddy, 2021; AWS, n.d.). Rather than provisioning environments manually, CloudFormation templates define networking, IAM roles, logging, monitoring, and guardrail configurations that are deployed consistently across accounts and regions.

From an organisational efficiency perspective, this automation reduced onboarding time for engineering teams. According to GoDaddy, account and environment creation that previously required several days of manual coordination can now be completed in under two hours. This standardisation reinforces the NIST characteristics of rapid elasticity and measured service identified by Mell and Grance (2011), as infrastructure can be provisioned and governed dynamically in response to demand. The Cloud Readiness Review further embeds governance by validating workloads against defined security and operational criteria before production deployment.

In cost terms, the Public Cloud Portal integrates budget tracking within the onboarding workflow. CloudFormation templates limit uncontrolled resource creation and align deployments with approved architectural patterns. However, cost optimisation remains dependent on oversight. While infrastructure-as-code improves transparency and reduces duplication, inefficient template design may scale misconfigurations across environments. Consequently, CloudFormation enhances financial governance when integrated within DevSecFinOps practices rather than acting as an automatic cost-control mechanism.

6. Conclusion

In conclusion, AWS CloudFormation operationalises foundational cloud principles through structured automation and governance. It enables consistent orchestration of IaaS and PaaS resources, translating characteristics such as rapid elasticity and measured service into repeatable deployment processes (Mell and Grance, 2011). The GoDaddy case demonstrates efficiency gains through reduced provisioning time and standardised multi-account architectures. However, its effectiveness depends on governance maturity and architectural discipline. Although tightly integrated within the AWS ecosystem, which may constrain interoperability in multi-cloud strategies, CloudFormation ultimately functions as a strategic orchestration framework shaping modern cloud governance, scalability, and cost control.

References

AWS (2024) AWS CloudFormation user guide. Seattle: Amazon Web Services. Available at: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/ (Accessed: 13 February 2026).

AWS (2025a) AWS Outposts overview. Seattle: Amazon Web Services. Available at: https://docs.aws.amazon.com/outposts/ (Accessed: 13 February 2026).

Mora, J. et al. (2024) ‘Infrastructure as Code Maturity Model: Managing Risks in DevOps’, Journal of Systems and Software, 210, p. 112456. Available at: https://doi.org/10.1016/j.jss.2024.112456 (Accessed: 15 February 2026).

Multi-IaC-Eval (2025) ‘Multi-IaC-Eval: Benchmarking Cloud Infrastructure as Code Across Providers’, arXiv preprint. Available at: https://arxiv.org/pdf/2509.05303.pdf (Accessed: 14 February 2026).

Neamt, A.I. (2024) From Terraform to AWS CloudFormation: A Study of Cost Patterns and Antipatterns. University of Groningen. Available at: https://fse.studenttheses.ub.rug.nl/33817/1/bCS2024NeamtAI.pdf (Accessed: 14 February 2026).

AWS (n.d.) AWS CloudFormation. Available at: https://aws.amazon.com/cloudformation/ (Accessed: 23 February 2026).

GoDaddy (2021) GoDaddy’s journey to the cloud and their Public Cloud Portal. Available at: https://www.godaddy.com/resources/news/godaddys-journey-to-the-cloud
 (Accessed: 23 February 2026)

Mell, P. and Grance, T. (2011) The NIST definition of cloud computing. NIST Special Publication 800-145. Gaithersburg, MD: National Institute of Standards and Technology. Available at: https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-145.pdf (Accessed: 17 February 2026).

Hashizume, K., Rosado, D.G., Fernández-Medina, E. and Fernandez, E.B. (2013) ‘An analysis of security issues for cloud computing’, Journal of Internet Services and Applications, 4(1), pp. 1–13. Available at: https://doi.org/10.1186/1869-0238-4-5 (Accessed: 26 February 2026).

Zhang, Q., Cheng, L. and Boutaba, R. (2010) ‘Cloud computing: state-of-the-art and research challenges’, Journal of Internet Services and Applications, 1(1), pp. 7–18. Available at: https://doi.org/10.1007/s13174-010-0007-6 (Accessed: 26 February 2026).



