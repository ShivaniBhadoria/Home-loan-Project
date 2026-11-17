# Home Loan Data Analysis (deep learning)

Predicts whether a loan applicant will have trouble repaying, using a Keras neural network on 307,511 past applications.
Course-end Project 1 of the Deep Learning module, Professional Certificate in AI and Machine Learning.

## What's in this folder

| File | Purpose |
| --- | --- |
| `home_loan_analysis.ipynb` | The full project: all 8 steps with explanations and charts |
| `loan_data.csv` | The dataset (about 160 MB) |
| `Data_Dictionary.csv` | What each column means |
| `requirements.txt` | The Python libraries the project needs |

## Set up on a Mac (one time)

TensorFlow supports Python 3.10 to 3.13 on Apple Silicon Macs (M1 or newer). Intel Macs need Python 3.10 to 3.12.

1. Check your Python version with `python3 --version`. Any version from 3.10 to 3.13 works on an Apple Silicon Mac.
2. Open Terminal and go to this folder:
   ```bash
   cd ~/Downloads/home_loan_project
   ```
3. Create and activate a virtual environment:
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```
   If `python3` points to an unsupported version, name a supported one instead, for example `python3.13 -m venv .venv`.
   ```bash
   python --version   # confirm the environment uses 3.10 to 3.13
   ```
4. Install the libraries (TensorFlow is large, so this can take several minutes):
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```
5. Check that TensorFlow works:
   ```bash
   python -c "import tensorflow as tf; print(tf.__version__)"
   ```

On Windows, use `py -3.13 -m venv .venv` and `.venv\Scripts\activate` instead.

## Run it

```bash
source .venv/bin/activate
jupyter lab
```

Open `home_loan_analysis.ipynb` and choose **Run > Run All Cells**. It takes about 2 to 4 minutes. Wait until the status bar says **Idle**.

## Troubleshooting

| Problem | Fix |
| --- | --- |
| `No matching distribution found for tensorflow` | Your Python version isn't supported (3.10 to 3.13; 3.10 to 3.12 on Intel Macs): delete `.venv` and recreate it with a supported version |
| `No module named 'tensorflow'` or `'imblearn'` | Activate `.venv`, then run `pip install -r requirements.txt` again |
| An imblearn import error mentioning scikit-learn | Run `pip install "scikit-learn==1.7.*"` |
| The kernel dies or runs out of memory | Close other apps, and keep `BALANCE_METHOD = "undersample"` |
| `FileNotFoundError: loan_data.csv` | Keep the CSV in the same folder as the notebook, named exactly `loan_data.csv` |

## Expected results

Neural networks vary slightly from run to run and machine to machine. Expect roughly:

- **Defaulters:** about 8% of applicants
- **Sensitivity:** about 0.65 to 0.75 at a 0.5 threshold
- **ROC-AUC:** about 0.72 to 0.76

Moderate scores are normal for this dataset: repayment is genuinely hard to predict from an application form alone.
