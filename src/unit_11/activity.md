Unit 11 Formative Activity: TensorFlow and Keras

Task:

Using TensorFlow and Keras (both open-source AI tools), build and deploy a simple AI model for image recognition on OpenStack.

Reflection: Reflect on how you technically built, deployed, and evaluated the AI model. Reflect on how AI can enhance cloud computing operations, especially in resource management and optimisation.
AI-Based Image Recognition Deployment on OpenStack and AWS EC2 Using TensorFlow and Keras

-------------------------

1. Introduction

The convergence of Artificial Intelligence (AI) and cloud computing has become a key enabler of modern computing systems. AI techniques such as machine learning and image recognition require substantial computational resources, which cloud platforms provide through scalable and on-demand infrastructure. This integration allows organisations to deploy intelligent applications efficiently while maintaining flexibility and cost-effectiveness (Nama, 2024).
This report presents the development and deployment of an image recognition model using TensorFlow and Keras. The model was deployed on both OpenStack and Amazon Web Services (AWS EC2) cloud environments. The objective is to demonstrate how AI models can be hosted and accessed in cloud infrastructures while evaluating the differences between private and public cloud platforms. The report concludes with a reflection on the process.
 
2. Relationship Between AI and Cloud Computing

AI and cloud computing are highly complementary technologies. Cloud computing provides scalable infrastructure for storing and processing large datasets, while AI enables intelligent data analysis and automation. Together, they allow organisations to develop advanced applications such as image recognition and predictive analytics (Kumar, 2024).
Recent research indicates that AI enhances cloud operations by improving resource allocation, workload scheduling, and system efficiency (Sanjalawe et al., 2025). Additionally, cloud-based AI systems enable real-time processing and distributed computing, which are essential for modern applications (Ficili et al., 2025).
Therefore, cloud platforms play a critical role in enabling the deployment and scalability of AI systems.
 
3. Model Development Using TensorFlow and Keras

The image recognition model was developed using TensorFlow and Keras, two widely used open-source frameworks for machine learning. A dataset consisting of labelled images of cats and dogs was used for training.
A convolutional neural network (CNN) architecture was implemented due to its effectiveness in image classification tasks. The dataset was loaded and automatically split into training and validation sets using TensorFlow utilities. The model was trained over several epochs, allowing it to learn features from the input images.
 
Figure1

The results in Figure1 showed high training accuracy but lower validation accuracy, indicating overfitting. This occurred due to the limited dataset size, which restricted the model’s ability to generalise to new data. Similar findings have been reported in AI research, where small datasets lead to reduced model performance (Kumar, 2024).
The trained model was saved as image_model.h5, enabling it to be reused for deployment.

4. Deployment on OpenStack

The first deployment was carried out using OpenStack, an open-source cloud platform used for managing private cloud infrastructures. OpenStack provides Infrastructure-as-a-Service (IaaS) capabilities, including virtual machine provisioning, networking, and storage management (Kanthed, 2024).

Deployment Steps on OpenStack
1.	A virtual machine (VM) was launched using the OpenStack Horizon dashboard.
2.	A key pair was created and assigned for secure SSH access.
3.	A floating IP address was configured to enable external access.
4.	Security groups were configured to allow SSH (port 22) and API access (port 5001).
5.	Python, TensorFlow, Flask, and required dependencies were installed on the VM.
6.	The trained model (image_model.h5) and Flask application (app.py) were uploaded.
7.	The Flask application was executed, exposing the AI model as a REST API.
The OpenStack deployment required manual configuration of networking and infrastructure, providing greater control over the environment.
 
5. Deployment on AWS EC2
 
Figure3 Connected the EC2 instance via SSH 

 
Figure4 The model was successfully tested using a remote API request
The model was also deployed on AWS EC2 as shown on Figure 3 and 4, a public cloud platform that provides scalable and managed infrastructure.

Deployment Steps on AWS

1.	An EC2 instance was launched using an Ubuntu image.
2.	A key pair was created and used for SSH access.
3.	Security groups were configured to allow ports 22 and 5001.
4.	Required software (Python, TensorFlow, Flask) was installed.
5.	The model and application files were uploaded using SCP.
6.	The Flask application was executed, making the model accessible via a public IP address.
The AWS deployment was faster and more automated compared to OpenStack, as networking and infrastructure setup were simplified.
 
6. Comparison of OpenStack and AWS EC2

Both OpenStack and AWS EC2 provide IaaS capabilities, but they differ in usability and configuration.
Feature	OpenStack	AWS EC2
Type	Private cloud	Public cloud
Setup complexity	High	Low
Networking	Manual	Automated
Control	High	Moderate
Deployment speed	Slower	Faster
OpenStack offers greater control over infrastructure and is suitable for private cloud environments. In contrast, AWS provides a more user-friendly and efficient deployment process, making it suitable for rapid application development.
 
7. Impact of AI on Cloud Operations

AI significantly enhances cloud computing by enabling intelligent automation and optimisation. AI-driven systems can dynamically allocate resources, predict workloads, and improve system efficiency (Sanjalawe et al., 2025).
Furthermore, AI enables advanced applications such as image recognition and real-time analytics, which rely on cloud infrastructure for scalability (Ficili et al., 2025). Cloud platforms also support distributed AI systems, allowing models to process large datasets efficiently (Mušić, 2024).
 
8. Reflection

The development and deployment process provided valuable insights into both AI and cloud computing.
One of the main challenges was the limited dataset, which resulted in overfitting and reduced model accuracy. This highlighted the importance of using larger datasets for effective machine learning.
Deploying the model on OpenStack required a deeper understanding of cloud infrastructure, particularly networking and security configuration. In contrast, AWS EC2 provided a simpler and faster deployment experience due to its managed services.
The comparison between OpenStack and AWS demonstrated the trade-off between control and usability. OpenStack offers flexibility and customisation, while AWS prioritises ease of use and scalability.
Overall, the project successfully demonstrated how AI models can be deployed in cloud environments, making them accessible as remote services.
 
9. Conclusion

This report has demonstrated the development and deployment of an AI-based image recognition model using TensorFlow and Keras. The model was successfully deployed on both OpenStack and AWS EC2 platforms.
The findings confirm that cloud computing is essential for enabling scalable and accessible AI applications. OpenStack provides greater control and flexibility, while AWS offers ease of deployment and efficiency. The integration of AI and cloud computing continues to drive innovation, enabling intelligent and scalable systems in modern computing environments.
 
References

Ficili, I. et al. (2025) Leveraging IoT, Cloud, and Edge Computing with AI. Sensors.
Kanthed, S. (2024) The Role of OpenStack in Multi-Cloud Strategies. Quest Journals.
Kumar, A. (2024) AI-Driven Innovations in Modern Cloud Computing. Journal of Computing Research.
Mušić, D. (2024) Digital transformation with cloud computing platforms. ScienceDirect.
Nama, P. (2024) Integrating AI with Cloud Computing. International Journal of Science and Research Archive.
Sanjalawe, Y. et al. (2025) AI-driven job scheduling in cloud computing. Artificial Intelligence Review.

