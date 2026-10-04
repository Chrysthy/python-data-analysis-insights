<h1 align="center"> Python Data Analysis Insights </h1>

<p align="center">
  A Python data analysis project focused on identifying the main factors related to customer churn.
  <br>
  This project analyzes a dataset with over 800,000 customers to understand cancellation patterns and identify possible actions to reduce churn.
</p>

<p align="center">  
  <a href="#-technologies">Technologies</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-project">Project</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-workflow">Workflow</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-main-insights">Main Insights</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-installation">Installation</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-additional-information">Additional Information</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
   <a href="#-license">License</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-contributing">Contributing</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#support">Support</a>  
</p>

<br>

## 🛠 Technologies

- Python
- Pandas
- Plotly
- Jupyter Notebook
- OpenPyXL
- CSV
- Git and GitHub

<br>

## 💻 Project

This project analyzes a dataset with over 800,000 customers to identify the main factors related to service cancellations.

The goal is to understand patterns among inactive customers and identify possible actions that could help reduce the churn rate.

<br>

## 🔄 Workflow

### Step 1: Import the dataset

Load the customer dataset for analysis.

### Step 2: Explore the data

Understand the available information, columns and possible inconsistencies.

### Step 3: Clean the data

Remove unnecessary information and handle missing or inconsistent values.

### Step 4: Perform an initial analysis

Analyze the distribution between active and cancelled customers.

### Step 5: Perform a detailed analysis

Evaluate how different variables may influence customer churn.

### Step 6: Identify possible actions

Use the analysis results to identify actions that may help reduce customer cancellations.

<br>

## 📊 Main Insights

### Monthly contracts

Customers with monthly contracts showed a higher occurrence of churn.

**Possible action:** offer incentives or discounts for migration to quarterly or annual contracts.

### Call center interactions

Customers with more than four calls to the call center showed a higher occurrence of churn.

This may indicate recurring problems that are not being resolved.

**Possible action:** create an alert when a customer contacts the call center three times.

### Payment delays

Customers with payment delays greater than 20 days showed a higher occurrence of churn.

**Possible action:** create an alert after 15 days of payment delay to allow preventive action.

<br>

## ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/Chrysthy/python-data-analysis-insights.git
```

Access the project folder:

```bash
cd python-data-analysis-insights
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

<br>

## 📝 Additional Information

This project uses a dataset obtained from Kaggle, provided in CSV format and read using `pandas`.

Dataset source: Kaggle

For projects that involve extracting tables from PDF files, the `tabula-py` library can be used to convert PDF tables into DataFrames for analysis with pandas.

Additional study notes and useful Python/Pandas commands can be found in:

```text
docs/useful-snippets.md
```

Detailed analysis notes can be found in:

```text
docs/analysis-insights.md
```


<br>

## 📜 License

* This project is licensed under the [MIT License](https://choosealicense.com/licenses/mit/)

<br>

