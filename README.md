Brain MRI Metastasis Segmentation using Nested U-Net and Attention U-Net
Overview
This project demonstrates the application of Nested U-Net (U-Net++) and Attention U-Net architectures for brain MRI metastasis segmentation. The primary goal is to enhance metastasis visibility and segment the regions accurately using two advanced U-Net variants. The project also includes a web application to visualize segmentation results using FastAPI and Streamlit.

Dataset
The dataset consists of brain MRI images and their corresponding metastasis segmentation masks. The dataset is split into 80% for training and 20% for testing. Preprocessing techniques, such as CLAHE (Contrast Limited Adaptive Histogram Equalization), have been applied to improve image quality and visibility of metastasis regions.

Architectures
1. Nested U-Net (U-Net++)
U-Net++, also known as Nested U-Net, is an improvement over the traditional U-Net architecture. It introduces nested skip pathways and dense connections to help capture finer details in segmentation tasks. This architecture addresses some limitations of the original U-Net by utilizing densely connected convolutional layers within the skip connections.

Key Features:

Dense skip connections to avoid gradient vanishing problems.
Better feature reuse across the model.

2. Attention U-Net
The Attention U-Net enhances the U-Net architecture by introducing attention gates. These gates learn to focus on the relevant regions of the image, which is particularly useful in medical imaging where target regions (e.g., metastasis) are small and vary in size and shape.

Key Features:

Attention gates allow the model to focus on metastasis regions, suppressing irrelevant regions.
Reduces false positives and improves segmentation accuracy for small target areas.

Data Preprocessing
CLAHE (Contrast Limited Adaptive Histogram Equalization)
CLAHE is a preprocessing technique that enhances the contrast of an image by applying histogram equalization locally. For medical images, where low contrast regions (e.g., metastasis) are crucial, CLAHE improves the visibility of those regions without amplifying noise.

How CLAHE works:

Divides the image into small tiles.
Applies histogram equalization to each tile to enhance local contrast.
Limits the contrast to prevent over-amplification of noise (via contrast limiting).
Benefits in our project:

CLAHE helps in highlighting metastasis regions, making the segmentation task more efficient.
It improves the model's ability to detect small, low-contrast regions.
Training and Evaluation
Training
Both models were trained using the preprocessed MRI dataset. We utilized the DICE Score as the primary evaluation metric. Training was carried out on a GPU for faster computation.

Hyperparameters:

Optimizer: Adam
Loss function: Binary Crossentropy
Batch size: 8
Epochs: 25
Evaluation Metric: DICE Score
The DICE Score is a measure of overlap between the predicted segmentation mask and the ground truth mask. It ranges from 0 (no overlap) to 1 (perfect overlap). It is well-suited for medical image segmentation tasks where the target regions are often small.
Challenges
Data Quality: Some MRI images had poor contrast, making it difficult for the model to learn. CLAHE helped mitigate this.
Class Imbalance: The number of metastasis regions was much smaller compared to the non-metastasis regions, leading to an imbalanced dataset.
Small Target Areas: Many metastasis regions were very small, causing the model to miss them during segmentation.
Future Improvements
Experiment with GANs (Generative Adversarial Networks) for better segmentation of small metastasis regions.
Implement 3D U-Net for volumetric (3D) brain MRI segmentation to capture more context from adjacent slices.
Use transfer learning from pre-trained models on large medical image datasets to improve segmentation accuracy.
Conclusion
This project successfully demonstrated the use of advanced U-Net architectures for brain MRI metastasis segmentation. The Attention U-Net architecture, with its attention gates, achieved the best segmentation results, as measured by the DICE score.
