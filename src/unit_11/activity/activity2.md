Unit 11 Development and Cloud Deployment of a Deep Learning-Based Chest X-ray Classification System

1. Introduction

The application of deep learning in medical imaging has significantly enhanced diagnostic capabilities, particularly in radiology. Chest X-ray analysis remains a fundamental method for detecting respiratory diseases such as pneumonia, which continues to pose a major global health burden (World Health Organization, 2024). However, the interpretation of radiographic images requires specialised expertise, which may not be readily available in resource-constrained healthcare environments.

This study aims to develop and deploy a deep learning-based system capable of classifying chest X-ray images into normal and pneumonia categories. The system integrates a convolutional neural network (CNN) with a web-based interface and is deployed on a cloud platform using Amazon Web Services (AWS) Elastic Compute Cloud (EC2).

This study contributes by bridging the gap between model development and real-world implementation, providing a practical evaluation of both model performance and deployment challenges in a constrained cloud environment.


2. Literature Review

Recent advancements in deep learning have demonstrated substantial improvements in medical image classification. Convolutional neural networks (CNNs) are particularly effective due to their ability to automatically extract hierarchical features from image data. Transfer learning has become a dominant approach, allowing pre-trained models to be adapted for domain-specific tasks such as pneumonia detection (Albahli, 2023).

MobileNetV2 is a lightweight architecture designed for computational efficiency, making it particularly suitable for deployment in resource-constrained environments (Sandler et al., 2018). Recent studies have shown that lightweight CNNs can achieve competitive performance while maintaining reduced computational requirements (Zhang et al., 2024).

Despite these advances, a significant gap remains between experimental performance and real-world deployment. While prior research demonstrates high classification accuracy, limited attention has been given to the practical challenges of deploying such models within constrained infrastructures (Johnson et al., 2024; Kumar et al., 2023). This highlights the need for research that not only evaluates model accuracy but also considers deployment feasibility. However, many existing studies prioritise classification accuracy without addressing deployment constraints, limiting their practical applicability in real-world healthcare systems.


3. Methodology

The model is developed using MobileNetV2 with transfer learning, leveraging pre-trained weights to improve performance while reducing training complexity. MobileNetV2 was selected over deeper architectures such as ResNet due to its lower computational requirements, making it more suitable for deployment within resource-constrained cloud environments. Input images are resized and normalised to match the expected input format of the model. The final classification layer is modified to perform binary classification, producing a probability score representing the likelihood of pneumonia.

The dataset used in this study consists of labelled chest X-ray images categorised into normal and pneumonia classes. Pneumonia cases typically present with increased lung opacity and visible infiltrates, whereas normal images exhibit clear lung fields. 


 
Figure 1: Sample chest X-ray images from the dataset showing normal and pneumonia cases

Representative samples from the dataset are shown in Figure 1, illustrating the visual differences that the model learns during training. The variability in image quality and anatomical structure introduces additional complexity, requiring the model to extract robust and generalisable features.

A threshold-based decision mechanism is implemented to convert probability outputs into discrete class labels. This approach enhances interpretability and aligns with clinical decision-making practices (Shen, Wu and Suk, 2023).

The system architecture consists of three components: a frontend interface, a backend application, and a model inference layer. The frontend enables image upload, the backend processes requests using Flask, and the inference layer performs predictions using TensorFlow.

4. Deployment and Implementation

The application is deployed on an AWS EC2 instance running a Linux-based operating system. Deployment involves configuring the virtual machine, establishing secure access via SSH, and transferring application files using SCP. A Python virtual environment is created to manage dependencies, and required libraries are installed using a requirements file.

During deployment, several technical challenges were encountered. The installation of TensorFlow initially failed due to insufficient memory on the EC2 free-tier instance. This issue was resolved by implementing a swap file, which extended available memory and enabled successful installation.

Storage constraints also resulted in installation failures, requiring manual cleanup of temporary files. Additionally, model deserialization errors occurred due to incompatibility between Keras versions, highlighting the importance of maintaining consistent development and deployment environments (Kumar et al., 2023).


5. Model Performance Evaluation

The model performance was evaluated using standard classification metrics, including accuracy, precision, recall, and F1-score. These metrics provide a comprehensive assessment of predictive performance.

 

Figure 2: Training and validation accuracy and loss curves

As shown in Figure 2, the training process demonstrates effective convergence, with increasing accuracy and decreasing loss over successive epochs. The close alignment between training and validation curves indicates minimal overfitting.

 

Figure 3: Confusion matrix for classification results

The confusion matrix in Figure 3 shows strong classification performance, with a high number of correct predictions. However, the presence of false positives and false negatives indicates limitations in distinguishing subtle features in chest X-ray images.

 
Figure 4: Classification report showing precision, recall, and F1-score

The classification report shown in Figure 4 highlights high recall, which is particularly important in medical contexts to minimise missed pneumonia cases. However, precision remains critical to reduce false positives and avoid unnecessary clinical interventions (Zhang et al., 2024).


6. Results

The deployed system successfully enables users to upload chest X-ray images and receive real-time predictions. The application outputs both classification labels and confidence scores, improving interpretability.

 
Figure 5: Web application interface displaying prediction output

As illustrated in Figure 5, the system is accessible via the EC2 public IP address, demonstrating successful integration of machine learning and cloud infrastructure. However, the use of a Flask development server highlights limitations in scalability and production readiness. The observed system performance and architectural limitations are consistent with previous studies, which highlight the trade-off between model efficiency and deployment feasibility in resource-constrained environments (Zhang et al., 2024).

7. Discussion

This project demonstrates the feasibility of deploying deep learning-based medical imaging systems within cloud environments. However, the deployment process reveals significant challenges that extend beyond model performance.

The reliance on AWS free-tier resources introduces constraints on memory and storage, limiting the practicality of deploying large machine learning frameworks. Additionally, compatibility issues between model formats and runtime environments highlight the importance of reproducibility. Containerisation technologies such as Docker could address these challenges by ensuring consistent deployment environments (Johnson et al., 2024).

From a clinical perspective, the presence of false negatives remains a critical concern, as missed pneumonia cases may have serious consequences. Therefore, future improvements should prioritise recall and robustness.

In addition, ethical considerations must be addressed. Bias in training data may result in unequal performance across different populations, potentially exacerbating healthcare disparities. Furthermore, the system lacks clinical validation and should only be used to support, rather than replace, expert medical judgement.

Further optimisation of the model is required to enhance both performance and efficiency. Fine-tuning the pre-trained MobileNetV2 layers, applying hyperparameter optimisation, and addressing class imbalance through data augmentation or weighted loss functions could improve generalisation. Additionally, model compression techniques such as quantisation and pruning could reduce computational requirements, enabling deployment in resource-constrained environments (Kumar et al., 2023).

8. Limitations

This study presents several limitations that affect both performance and generalisability. Firstly, the dataset may not fully represent real-world clinical diversity, potentially introducing bias (Shen, Wu and Suk, 2023). Secondly, the binary classification approach simplifies the complexity of medical diagnosis.

From a computational perspective, deployment on AWS free-tier resources imposed significant constraints on memory and storage, affecting system performance. Furthermore, compatibility issues between model formats and runtime environments highlight the need for reproducible pipelines.

Finally, the system is not clinically validated and should not be used for diagnostic decision-making without expert supervision.

9. Conclusion

This study successfully developed and deployed a deep learning-based chest X-ray classification system. By integrating a CNN model with a web-based interface and deploying it on AWS EC2, the project demonstrates both technical capability and practical challenges associated with real-world implementation.

The findings highlight that achieving high model accuracy alone is insufficient; successful deployment requires addressing resource constraints, compatibility, and scalability. Future work should focus on optimising both model performance and deployment strategies to enable practical healthcare applications. 

This study uniquely contributes by demonstrating not only the development of a deep learning model, but also the practical challenges of deploying such systems within constrained cloud environments, thereby bridging the gap between experimental research and real-world implementation.

References

Albahli, S. (2023) ‘Efficient deep learning models for pneumonia detection’, Healthcare Analytics, 3, pp. 1–10.

Johnson, A.E.W. et al. (2024) ‘Advances in medical imaging datasets and AI deployment’, The Lancet Digital Health, 6(2), pp. e120–e130.

Kumar, R., Singh, A. and Patel, V. (2023) ‘Challenges in deploying deep learning models on cloud platforms’, IEEE Access, 11, pp. 45678–45690.

Shen, D., Wu, G. and Suk, H.I. (2023) ‘Deep learning in medical image analysis’, Annual Review of Biomedical Engineering, 25, pp. 221–248.

Zhang, Y. et al. (2024) ‘Lightweight convolutional neural networks for medical image classification’, Computers in Biology and Medicine, 165, 107452.

World Health Organization (2024) Pneumonia. Available at: https://www.who.int (Accessed: 25 March 2026).

