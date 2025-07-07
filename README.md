# Dyslexia-Detection-Using-Eye-Movement-Tracking-SVM-Based-
Eye-movement based dyslexia detection using Support Vector Machine (SVM). Uses fixation data to classify subjects with high accuracy. Includes full pipeline from feature extraction to model training, evaluation, and visualization.
## Dataset

- **Source:** [ETDD70: Eye-tracking Dyslexia Dataset](https://zenodo.org/records/13332134)
- **Original Dataset:** 70 subjects (35 dyslexic, 35 non-dyslexic)
- **Synthetic Augmentation:** 140 synthetic subjects generated
- **Total Dataset Size:** 210 subjects (105 dyslexic, 105 non-dyslexic)
- **Fixation Files:** `.csv` files per subject with fixation points during reading tasks
- **Ground Truth:** Provided in `expanded_file.csv`

---

## Feature Extraction

We extract several features per subject from the fixation data:

- Fixation count
- Mean and standard deviation of fixation duration
- Mean fixation positions (`fix_x`, `fix_y`)
- Mean saccade length

---

## SVM Classification Pipeline

### 🧪 80-20 Train-Test Split
- Split is based on subject IDs (not rows of data)
- Training: 80% of subjects
- Testing: 20% of subjects

### 🧠 Model
- **Algorithm:** Support Vector Machine (SVM)
- **Kernel:** Radial Basis Function (RBF)
- **Validation:** Manual 80-20 split with ground truth labels only available for training subjects

---

## Performance Metrics

### 📊 Classification Report (Test Set)

| Class         | Precision | Recall | F1-Score | Support |
|---------------|-----------|--------|----------|---------|
| Non-Dyslexic  | 0.79      | 0.92   | 0.85     | 24      |
| Dyslexic      | 0.86      | 0.67   | 0.75     | 18      |

- **Overall Accuracy:** 80.95%
- **Train Accuracy:** 79.76%
- **Macro F1 Score:** 0.80
- **Weighted F1 Score:** 0.80

### ✅ Overfitting Check
- The training and testing accuracy are close, indicating **no major overfitting**.

---

## Results and Visualizations

- **ROC Curve:** `Results/roc_curve_svm.png`
- **Confusion Matrix:** `Results/confusion_matrix_svm.png`
- **Learning Curve:** `Results/learning_curve_svm.png`

---

## Project Structure

- `data/` - Folder containing `.csv` fixation files for each subject
- `expanded_file.csv` - Ground truth mapping for all real and synthetic subjects
- `Syllable Svm Eval.ipynb` - Jupyter notebook implementing training, evaluation, and visualization
- `Results/` - Folder with plots and evaluation outputs
- `models/` - Folder containing saved model (`svm_model_csv.pkl`)

---

## Requirements

- Python 3.x
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn

---

## Acknowledgments

- Dataset from [Zenodo ETDD70](https://zenodo.org/records/13332134) project
- Czech eye-tracking dataset focused on children with dyslexia (ages 9-10)

