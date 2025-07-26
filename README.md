Group Members:
Om Borda  (Matriculation no: 10000722)
Zaranaben Savani (Matriculation no :10001007)

Sign Language Alphabet Classification Project
=============================================

Overview
--------
This project aims to classify hand sign images into letters of the alphabet using a Convolutional Neural Network (CNN). The goal is to assist in building a sign-to-text tool by annotating unlabeled sign language data.

Project Structure
-----------------
SignLanguage/
│
├── README.md                   # Project documentation
├── requirements.txt            # Project dependencies
├── portfolio3.ipynb            # Main training + inference notebook
├── best_model.pth              # Saved best model weights
├── submission_5226.csv         # Final predictions (submission-ready)
├── sample_submission.csv       # Sample format reference
│
└── SignLanguage_kaggle/
    ├── old_annotated.pth       # Pre-annotated training dataset
    ├── todo.pth                # Unlabeled dataset to annotate
    └── todo_example.pth        # Small manually labeled sample

Dataset
-------
- Labeled Set: 25-class labeled hand sign images (from `old_annotated.pth` + `todo_example.pth`)
- Unlabeled Set: Similar image samples (from `todo.pth`) to be predicted
- Format: All data is stored in PyTorch `.pth` Dataset format

Data Preprocessing
------------------
- All images are resized to 32x32
- Training data includes grayscale conversion, sharpness/inversion jitter, color augmentation, and flipping
- Test/inference data is only resized and grayscaled

Model Architecture
------------------
Convolutional Neural Network (CNN):
- 3 Convolutional layers with ReLU and MaxPooling
- 1 Fully connected hidden layer with Dropout
- Output: 25 classes (A–Z except J/Z, depending on dataset)

Training & Evaluation
---------------------
- Loss Function: CrossEntropyLoss
- Optimizer: Adam (lr = 0.001)
- Scheduler: ReduceLROnPlateau for dynamic learning rate
- Early Stopping: Patience = 5 epochs
- Train/Val Split: 80/20
- Epochs: 20
- Best model saved as `best_model.pth`

Results
-------
- Final predictions are saved in `submission_5226.csv`
- Format: CSV with columns `ID,Label`, ready for submission

How to Run
----------
1. Install Requirements:
   - Python 3.x, PyTorch, torchvision, matplotlib, pandas, scikit-learn

2. Prepare Data:
   - Ensure all `.pth` files are inside `SignLanguage_kaggle/`

3. Run Notebook:
   - Open and execute all cells in `portfolio3.ipynb`

4. View Submission:
   - Output CSV is generated automatically after inference

File Descriptions
-----------------
- `README.md`: This documentation file
- `portfolio3.ipynb`: Main notebook with full training-to-submission pipeline
- `requirements.txt`: Dependencies to install
- `best_model.pth`: Saved model with best validation performance
- `submission_5226.csv`: Final prediction results
- `sample_submission.csv`: Example format for submission
- `SignLanguage_kaggle/`: Contains the datasets (`.pth` files)

Acknowledgments
---------------
- Inspired by Margot’s work with the deaf community
- Built using PyTorch and torchvision

For questions or improvements, feel free to fork or contribute.