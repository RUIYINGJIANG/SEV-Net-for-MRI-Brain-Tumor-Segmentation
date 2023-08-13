# SEV-Net-for-MRI-Brain-Tumor-Segmentation

# Keywords: image analysis, neural networks, brain imaging, V-Net, SENet.

# Background 
Brain tumours are caused by abnormal growth of cells in the brain, which may severely damage the nervous system 
and endanger patients [1]. Accurate brain tumour segmentation from magnetic resonance images (MRI) allows 
clinicians to clearly identify the location, extent, and type of tumour, which supports the diagnosis, treatment planning 
and survival prediction [2]. Traditionally, brain tumour segmentation has been performed manually by experienced 
radiologists. However, the manual depiction is not only error-prone due to its subjective nature, but also tedious and 
time-consuming. Therefore, the development of reliable and fast automated algorithms will undoubtedly lead to more 
accurate, rapid, and cost-effective diagnoses, resulting in significant advances in long-term patient care planning.
The project will study the most common type of brain tumours- Gliomas. The multi-modal MRI sequences are the 
typical tool to detect Gliomas, which have four modalities (T1, T1 with contrast-enhanced (T1ce), T2, and fluid 
attenuation inversion recovery (FLAIR)). Gliomas consist of three overlapping regions including the necrotic tumour 
core (NCR), the peritumoral edema (ED), and enhancing tumour (ET). The regions can be combined into 3 nested 
regions: whole tumour or WT(NCR+ED+ET), tumour core or TC (NCR), and ET. This project will build a 
convolutional neural network (CNN) to segment the above three regions (WT, TC, and ET).
Dataset and Data availability
The image data to be used for this project is from BraTS 2021 Multi-parametric MRI (mpMRI) dataset [3-5]. I will 
use the training set (125, provided with images and segmentation labels) to develop the model, and test the performance 
of the model on the validation set (219, without segmentation labels).
Data is available upon request from the BraTS Continuous Evaluation, which provides downloading of training 
and validation data.
# Literature Review
Recently, deep learning has made significant progress in various medical image segmentation tasks, especially for 
large-scale training data. Full Convolutional Networks (FCN) have been proposed for per-pixel classification with 
end-to-end learning advantages [6]. Despite the FCN-based models having the advantage of dense pixel classification, 
the loss of spatial information would occur in the pooling layers, resulting in rough segmentation [7]. U-Net [8] 
proposes the use of a skip layer to address this problem and has been suggested for fine medical image segmentation. 
Several excellent models with modifications to the original U-Net have been presented in previous BraTS challenges, 
such as nn-UNet [9] and extending nn-UNet [10].

# Methodology 
V-Net: V-Net is a 3D image segmentation model based on a volumetric, FCN proposed by Millettari et al. [11]. The 
structure of the V-Net is very similar to that of the U-Net, which essentially replaces the 2D operations of the U-Net 
with the corresponding 3D operations, so that instead of inputting each slice individually for training, the entire image 
can be taken as input to the model. In addition, a significant improvement of V-Net over U-Net is that in each stage, 
V-Net adds a Residual learning block to accelerate the convergence of the training process.
SENet: Squeeze-and-Excitation Networks (SENet) is a new image recognition architecture published by Momenta in 
2017 [12], which enhances the performance of the model by modelling the correlation between feature channels, 
strengthening features that are important for the task and weakening less important features.
SEV-Net: In this project, the SEV-Net framework will be proposed for the segmentation of MRI, which is obtained 
by embedding the SE block into each stage of the V-Net.

#Assessment
Evaluation Metrics: Dice score
The Dice score is a metric commonly used to evaluate the performance of image segmentation algorithms. A larger 
dice score means that the algorithm has better segmentation performance.
It is defined as follows: 𝐷ⅈ𝑐ⅇ = 2|𝑋∩𝑌|/|𝑋|+|𝑌|
The project looks forward to demonstrating the benefit of the SEV-Net model in terms of improving the accuracy of 
the brain tumour segmentation synthesis or the accuracy of one of these aspects (WT, TC, ET). 
I will calculate the Dice score of WT, TC, and ET to evaluate the performance of the SEV-Net model for brain tumor 
segmentation. And then compare the result with other published methods [9, 10, 13] on the BraTS challenges 2021 
validation dataset.
Ethics approval and consent to participate
The study was conducted in accordance with the Declaration of Helsinki and approved by the Institutional Review 
Board of the RSNA-ASNR-MICCAI BraTS 2021 challenge for studies involving humans.

# Outcomes:
In this project, I propose to use a novel CNN structure (SEV-Net) for brain tumour segmentation. If SEV-Net performs 
better than other CNNs in segmenting important regions of brain tumours, this will further increase the value of deep 
learning models in enhancing glioma diagnosis. In future work, I will collect the image data of more kinds of diseases 
to train the model and improve its generalization ability.


# REFERENCES
[1] Louis, D.N., Perry, A., Reifenberger, G. et al. The 2016 World Health Organization Classification of Tumors of 
the Central Nervous System: a summary. Acta Neuropathol 131, 803–820 (2016)
[2] Gordillo, N., Montseny, E., Sobrevilla, P.: State of the art survey on MRI brain tumor segmentation. Magn Reson 
Imaging. 31, 1426–1438 (2013)
[3] U.Baid, et al., The RSNA-ASNR-MICCAI BraTS 2021 Benchmark on Brain Tumor Segmentation and 
Radiogenomic Classification, arXiv:2107.02314, 2021
[4] B. H. Menze, A. Jakab, S. Bauer, J. Kalpathy-Cramer, K. Farahani, J. Kirby, et al. "The Multimodal Brain Tumor 
Image Segmentation Benchmark (BRATS)", IEEE Transactions on Medical Imaging 34(10), 1993-2024 (2015) DOI: 
10.1109/TMI.2014.2377694
[5] S. Bakas, H. Akbari, A. Sotiras, M. Bilello, M. Rozycki, J.S. Kirby, et al., "Advancing The Cancer Genome Atlas 
glioma MRI collections with expert segmentation labels and radiomic features", Nature Scientific Data, 4:170117 
(2017) DOI: 10.1038/sdata.2017.117
[6] Long, J., Shelhamer, E., Darrell, T.: Fully Convolutional Networks for Semantic Segmentation. Presented at the 
Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, (2015)
[7] Soltaninejad, M., Zhang, L., Lambrou, T., Yang, G., Allinson, N., & Ye, X.: MRI brain tumor segmentation and 
patient survival prediction using random forests and fully convolutional networks. In: International MICCAI 
Brainlesion Workshop. pp. 204-215. Springer, Cham (2017)
[8] Ronneberger O, Fischer P, Brox T. U-net: Convolutional networks for biomedical image segmentation. 
In: Medical Image Computing and Computer-Assisted Intervention – MICCAI 2015. Cham (2015)
[9] Isensee, F., Jäger, P.F., Full, P.M., Vollmuth, P., Maier-Hein, K.H. (2021). nnU-Net for Brain Tumor 
Segmentation. In: Crimi, A., Bakas, S. (eds) Brainlesion: Glioma, Multiple Sclerosis, Stroke and Traumatic Brain 
Injuries. BrainLes 2020. Lecture Notes in Computer Science(), vol 12659. Springer, Cham. 
https://doi.org/10.1007/978-3-030-72087-2_11
[10] Luu, H.M., Park, SH. (2022). Extending nn-UNet for Brain Tumor Segmentation. In: Crimi, A., Bakas, S. (eds) 
Brainlesion: Glioma, Multiple Sclerosis, Stroke and Traumatic Brain Injuries. BrainLes 2021. Lecture Notes in 
Computer Science, vol 12963. Springer, Cham. https://doi.org/10.1007/978-3-031-09002-8_16
[11] Milletarì, F., Navab, N., & Ahmadi, S. (2016). V-Net: Fully Convolutional Neural Networks for Volumetric 
Medical Image Segmentation. 2016 Fourth International Conference on 3D Vision (3DV), 565-571
[12] J. Hu, L. Shen, S. Albanie, G. Sun and E. Wu, "Squeeze-and-Excitation Networks," in IEEE Transactions on 
Pattern Analysis and Machine Intelligence, vol. 42, no. 8, pp. 2011-2023, 1 Aug. 2020, doi: 
10.1109/TPAMI.2019.2913372
[13] Myronenko, A. (2019). 3D MRI Brain Tumor Segmentation Using Autoencoder Regularization. In: Crimi, A., 
Bakas, S., Kuijf, H., Keyvan, F., Reyes, M., van Walsum, T. (eds) Brainlesion: Glioma, Multiple Sclerosis, Stroke 
and Traumatic Brain Injuries. BrainLes 2018. Lecture Notes in Computer Science(), vol 11384. Springer, Cham. 
https://doi.org/10.1007/978-3-030-11726-9_2
