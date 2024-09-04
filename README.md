# Self-Supervised Pretraining For Improving Segmentation Performance of Ultrasound Medical Images

More details such as figures please see the poster.

## Abstract
A significant challenge in medical imaging for machine learning is the scarcity of labeled training data. Self-supervised pretraining methods, like DenseCL, can learn useful features from unlabelled data, enhancing downstream performance when fine-tuned on limited labeled data. This project explores the application of DenseCL for segmenting ultrasound knee recess distension images, demonstrating that DenseCL pretraining can slightly improve segmentation performance, particularly when annotated data is scarce.

## Introduction
Machine learning in medical imaging automates tasks like classification, detection, and segmentation, reducing workloads and improving healthcare services. A major challenge is the lack of annotated medical images for training. Self-supervised learning addresses this by pretraining models on unlabelled data using pretext tasks, which can significantly enhance downstream segmentation performance when fine-tuned on annotated datasets. This project evaluates DenseCL's effectiveness in ultrasound image segmentation, particularly in scenarios with limited annotated data.

## Purpose
To improve segmentation performance in ultrasound medical images without requiring large quantities of annotated data.

## Research Question
Can the adapted DenseCL pretrain method produce better image representations for the encoder and improve the performance of downstream segmentation tasks with ultrasound medical images?

## Hypothesis
DenseCL pretraining will produce better image representations, leading to improved performance in downstream segmentation tasks of ultrasound medical images.

## Objectives
- Adapt DenseCL for self-supervised pretraining on ultrasound medical images.
- Evaluate the performance improvements in segmentation tasks using DenseCL compared to unpretrained models.
- Provide recommendations for applying DenseCL pretraining in medical image segmentation.

## Methodology
- **Dataset:** 3750 annotated ultrasound knee recess distension images from MiData lab.
- **Model Pretraining:** DenseCL on ResNet-50 using modified augmentations suitable for ultrasound images. Trained for 200 epochs with a batch size of 32.
- **Downstream Segmentation Model:** ResNet-50 backbone with fully convolutional decoder trained for 40,000 iterations. Evaluated on mIoU metric.
- **Experiments:** 
  - Compare segmentation performance with and without DenseCL pretraining on various data fractions (1%, 5%, 100%).
  - Visualize learned features using t-SNE to assess differences in image representations.
- **Hardware:** Experiments conducted on a single NVIDIA TITAN X GPU with 12GB memory.

## Results
- **Segmentation Performance:** DenseCL pretraining improved mIoU by up to 3.9%, with higher gains observed when training data is limited.
- **Feature Visualization:** t-SNE plots show distinct clustering between pretrained and unpretrained models, suggesting improved feature representations with DenseCL.

## Discussion
DenseCL pretraining consistently enhanced segmentation performance across varying data sizes, especially when annotations were sparse. Although the improvements were modest, they indicate the potential for greater gains with larger pretraining datasets. Future work should involve repeated experiments to confirm statistical significance and explore additional augmentation strategies.

## Conclusion
DenseCL pretraining offers a promising approach for improving segmentation performance in ultrasound medical images, particularly in low-data scenarios. While gains were modest in this study, expanding the pretraining dataset could unlock further improvements. Recommendations include further testing with varied augmentations and longer pretraining periods to refine model performance.

## References
- Chen, T., Kornblith, S., Norouzi, M., & Hinton, G. (2020). A Simple Framework for Contrastive Learning of Visual Representations. [DOI](https://doi.org/10.48550/ARXIV.2002.05709)
- He, K., Fan, H., Wu, Y., Xie, S., & Girshick, R. (2019). Momentum Contrast for Unsupervised Visual Representation Learning. [DOI](https://doi.org/10.48550/ARXIV.1911.05722)
- Wang, X., Zhang, R., Shen, C., Kong, T., & Li, L. (2020). Dense Contrastive Learning for Self-Supervised Visual Pre-Training. [DOI](https://doi.org/10.48550/ARXIV.2011.09157)
