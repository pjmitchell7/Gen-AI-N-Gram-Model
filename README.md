# Gen-AI-N-Gram-Model
Generative AI for Software Dev Homework 1 - Paul Mitchell &amp; Stephanie Omondiale
### **Tutorial: Running the N-Gram Model on Google Colab Using a Public Google Drive Folder**
This guide provides step-by-step instructions for running the N-Gram model on Google Colab using a public Google Drive folder. This ensures that anyone with the link can access and run the model consistently without manual file uploads.
-----
Google Drive LINK: https://drive.google.com/drive/folders/1LOJm5cwTWKC8J1iYJmvHVG-E-9X6nzqV?usp=sharing
---

## **Step 1: Open Google Colab**
1. Go to [Google Colab](https://colab.research.google.com/).
2. Locate **HW1.ipynb** in this GitHub repository, download it locally, and open it in google colab.
    2.5. You can also access it here for the downloaded pkl files:  https://colab.research.google.com/drive/17JjbDYHUTIOimwySca5vKRketFYckYB6?usp=sharing

---

## **Step 2: Mount the Public Google Drive Folder**
Since the Google Drive folder is public, authentication is not required. Instead, download the necessary files using `gdown`:

```python
!pip install gdown
!gdown --folder "YOUR_GOOGLE_DRIVE_FOLDER_LINK"
```
Replace `"YOUR_GOOGLE_DRIVE_FOLDER_LINK"` with the actual Google Drive folder link.

This will download the entire **N-Gram Model** directory, including:
- **HW1.ipynb** (Main Colab Notebook)
- **tokenized_train.txt** (Training Data)
- **tokenized_eval.txt** (Evaluation Data)
- **tokenized_test.txt** (Test Data)
- **kneserney_3gram_model.pkl** (Trained 3-Gram Model)
- **kneserney_5gram_model.pkl** (Trained 5-Gram Model)
- **kneserney_7gram_model.pkl** (Trained 7-Gram Model)

---

## **Step 3: Install Dependencies**
Before running the notebook, install the necessary Python packages:

```python
!pip install nltk pandas matplotlib seaborn pydriller
```
Additionally, download the NLTK tokenizer data:

```python
import nltk
nltk.download('punkt')
```

---

## **Step 4: Run HW1.ipynb**
Once all dependencies are installed, run the entire notebook:

1. Open **HW1.ipynb** in Google Colab.
2. Click **"Runtime" > "Run All"**.
3. Ensure that all cells execute successfully.

The notebook will:
- Preprocess the dataset (clean, tokenize, and split Java methods).
- Train the N-Gram Model (3-Gram, 5-Gram, and 7-Gram) using Kneser-Ney smoothing.
- Evaluate the model using confidence scores and prediction probability distributions.

---

## **Step 5: View Model Performance**
### Histogram of Prediction Probabilities
To visualize the probability distribution of predicted tokens, run:

```python
import matplotlib.pyplot as plt
import seaborn as sns
import json

# Load results from the JSON file
with open("results_student_model.json", "r") as f:
    results = json.load(f)

# Extract probabilities
all_probabilities = [prob for predictions in results.values() for _, prob in predictions]

# Plot histogram
plt.figure(figsize=(10, 5))
sns.histplot(all_probabilities, bins=30, kde=True)
plt.xlabel("Prediction Probability")
plt.ylabel("Frequency")
plt.title("7-Gram Model Token Prediction Probability Distribution")
plt.show()
```

---

## **Step 6: Save Results to Google Drive**
If you want to save outputs (e.g., JSON files, trained models, plots) back to Google Drive, mount your Drive manually:

```python
from google.colab import drive
drive.mount('/content/drive')
```

Then copy the results:

```python
!cp results_student_model.json /content/drive/MyDrive/N-Gram-Model/
!cp results_teacher_model.json /content/drive/MyDrive/N-Gram-Model/
```

---

## **Summary**
This tutorial provides a simple and standardized method for running the N-Gram Model on Google Colab using a public Google Drive folder. 

By following these steps, users can:
1. Download the repository from GitHub or Google Drive.
2. Install dependencies and download required NLTK data.
3. Run HW1.ipynb to preprocess data, train models, and evaluate predictions.
4. Visualize model confidence scores using probability histograms.
5. Save results back to Google Drive if needed.

Now, anyone with access to the repository can run the code in a consistent environment without manually configuring files.
