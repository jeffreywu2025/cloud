Unit 1 Formative Discussion: AWS vs Google Cloud

Compare and contrast the service models of two major cloud providers (e.g., AWS vs. Google Cloud). Discuss their differences in terms of flexibility, pricing, and specific use cases.
_____________________________________________
My post:

AWS and Google Cloud Platform (GCP) both deliver IaaS/PaaS as composable building blocks, but their service-model emphasis differs in practice.

Flexibility: AWS tends to maximise “pick-your-own-components” flexibility: many instance families, storage tiers, networking options, and niche managed services, which suits teams that want fine-grained architectural control (and accept higher configuration overhead). GCP is often more opinionated around managed, integrated platforms, especially where services are designed to work together via consistent IAM, APIs and data tooling. In storage, for example, a recent weighted-scoring comparison found AWS strongest overall for object/file/hybrid options, while GCP stood out particularly for block and archive storage performance/scalability—useful when latency-sensitive throughput and scaling are primary drivers (Nouhas, Belangour and Nassar, 2025).

Pricing and cost governance: Both use pay-as-you-go plus commitment discounts, but the lived experience is shaped by billing transparency and optimisation tooling. A 2026 security study frames cost observability as hard precisely because providers expose different billing data structures and metrics; it notes the need to normalise exports such as AWS Cost Explorer JSON and GCP Billing exports (often queried via BigQuery) to achieve unified budget controls across clouds (Martseniuk et al., 2026). This implies AWS–GCP price comparison is not only about rates, but about measurement friction and governance maturity.

Use cases: For tightly coupled HPC, evidence shows AWS can be competitive when using HPC-oriented networking (e.g., EFA), achieving strong scaling and cost-efficiency comparable to on-prem HPC in a large CFD study (Dancheva, Alonso and Barton, 2024). Conversely, GCP can be attractive for data-heavy and latency-sensitive workloads where high-performing block/archive storage and integrated analytics pipelines simplify delivery (Nouhas, Belangour and Nassar, 2025).

References:

Dancheva, T., Alonso, U. and Barton, M. (2024) ‘Cloud benchmarking and performance analysis of an HPC application in Amazon EC2’, Cluster Computing, 27, pp. 2273–2290.

Martseniuk, Y., Partyka, A., Opirskyy, I. and Harasymchuk, O. (2026) ‘Cost observability as a security control in multi-cloud environments based on SOC 2 security standard’, Computers & Security, 161, 104771. 


Nouhas, H., Belangour, A. and Nassar, M. (2025) ‘A Weighted Scoring Model Analysis of Cloud Storage Services: Comparing AWS, Azure, and Google Cloud Platform’, International Journal of Engineering Trends and Technology, 73(6), pp. 350–370. 
