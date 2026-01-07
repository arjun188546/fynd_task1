# Fynd AI Intern Assessment - Task 1
## Rating Prediction via Prompting

This repository contains the solution for Task 1 of the Fynd AI Intern Take Home Assessment 2.0.

## Overview

This project implements and evaluates **4 different prompting approaches** to predict star ratings (1-5) from Yelp reviews using Large Language Models (LLMs).

### Prompting Approaches Implemented

1. **Simple Direct Prompting** - Baseline approach with minimal context
2. **Few-Shot Learning** - Includes 5 examples to guide the model
3. **Chain-of-Thought (CoT)** - Asks the model to reason step-by-step
4. **Structured Criteria-Based Analysis** - Detailed evaluation framework

## Setup Instructions

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook or JupyterLab
- Gemini API key (free tier available)

### Installation

1. **Clone or download this repository**

2. **Install dependencies:**
```bash
pip install pandas numpy scikit-learn google-generativeai python-dotenv matplotlib seaborn kaggle
```

3. **Get your Gemini API key:**
   - Visit: https://makersuite.google.com/app/apikey
   - Create a free API key
   - Copy the key

4. **Create `.env` file:**
```bash
# Copy the example file
copy .env.example .env

# Edit .env and add your API key
GEMINI_API_KEY=your_actual_api_key_here
```

5. **Download the Yelp dataset:**

**Option A: Using Kaggle API (Recommended)**
```bash
# Set up Kaggle credentials first
# Download kaggle.json from https://www.kaggle.com/settings/account
# Place it in ~/.kaggle/ (Linux/Mac) or C:\Users\<YourUsername>\.kaggle\ (Windows)

kaggle datasets download -d omkarsabnis/yelp-reviews-dataset
unzip yelp-reviews-dataset.zip
```

**Option B: Manual Download**
- Visit: https://www.kaggle.com/datasets/omkarsabnis/yelp-reviews-dataset
- Download the dataset
- Extract `yelp.csv` to this directory

### Running the Notebook

1. **Start Jupyter:**
```bash
jupyter notebook
```

2. **Open `task1_rating_prediction.ipynb`**

3. **Run all cells sequentially**
   - The notebook will automatically sample ~200 reviews
   - Evaluation takes approximately 10-20 minutes
   - Progress is displayed during execution

## Project Structure

```
fynd-task1/
│
├── task1_rating_prediction.ipynb    # Main notebook with all implementations
├── .env.example                     # Environment variable template
├── .env                            # Your API keys (create this, not in git)
├── README.md                       # This file
├── yelp.csv                        # Dataset (download separately)
│
└── Generated files after running:
    ├── approach_comparison.csv      # Results comparison table
    ├── approach_comparison.png      # Visualization of results
    ├── confusion_matrix_best.png    # Confusion matrix
    └── results_*.csv               # Detailed results for each approach
```

## Features

### Evaluation Metrics

- **Accuracy**: Exact match between predicted and actual ratings
- **Mean Absolute Error (MAE)**: Average rating difference
- **JSON Validity Rate**: Percentage of valid JSON responses
- **Confusion Matrix**: Detailed breakdown of predictions
- **Classification Report**: Precision, recall, F1-score per rating

### Visualizations

- Comparison charts for all approaches
- Confusion matrix heatmap
- Rating distribution analysis
- Sample prediction examples

### Error Handling

- API retry logic with exponential backoff
- JSON parsing from various response formats
- Validation of prediction structure
- Graceful handling of API failures

## Results

The notebook provides:

1. **Comparison Table** - Side-by-side metrics for all approaches
2. **Visualizations** - Charts comparing accuracy, validity, and errors
3. **Detailed Analysis** - Classification reports and confusion matrices
4. **Sample Predictions** - Examples of correct and incorrect predictions
5. **Discussion** - Trade-offs, challenges, and recommendations

## Design Decisions

### Why These Approaches?

1. **Simple Direct**: Establishes baseline performance
2. **Few-Shot Learning**: Research-backed technique for improved calibration
3. **Chain-of-Thought**: Better reasoning for ambiguous cases
4. **Structured Analysis**: Mimics human rating process

### Prompt Engineering Principles

- Clear output format specification (JSON)
- Explicit rating scale definitions
- Consideration of sentiment intensity
- Balance between prompt length and effectiveness

## Trade-offs

| Approach | Pros | Cons |
|----------|------|------|
| Simple Direct | Fast, low cost | Lower accuracy |
| Few-Shot | Better calibration | Higher token cost |
| Chain-of-Thought | Explainable | Slower, more expensive |
| Structured | Most comprehensive | Highest cost |

## Notes

- Sample size is ~200 reviews (stratified sampling)
- API rate limiting is implemented (0.5s delay)
- Free Gemini API tier has daily limits
- Results may vary slightly between runs

## Troubleshooting

**Issue: API key error**
- Ensure `.env` file exists and contains valid API key
- Check API key is active at https://makersuite.google.com/

**Issue: Dataset not found**
- Download `yelp.csv` and place in project root
- Check file name matches exactly: `yelp.csv`

**Issue: Rate limit exceeded**
- Wait a few minutes and retry
- Consider using a smaller sample size

**Issue: JSON parsing errors**
- The notebook handles most parsing issues automatically
- Check the raw responses in results CSV files

## Contact

For questions or issues related to this submission, please refer to the GitHub repository.

## License

This project is submitted as part of the Fynd AI Intern assessment.
