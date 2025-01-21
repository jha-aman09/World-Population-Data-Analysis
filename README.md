# 🌍 World Population Data Analysis

Welcome to the **World Population Data Analysis**! This is a personal initiative to analyze global population trends, create insightful visualizations, and gain a deeper understanding of demographic patterns. The project leverages various data visualization and analysis techniques to derive meaningful insights from the dataset.

## 👨‍💻 Author
- **Github:** [Aman Jha](github.com/jha-aman09)
- **LinkedIn:** [Aman Jha](https://www.linkedin.com/in/aman--jha)

## 🔗 Project Links
- **Google Colab Notebook**: [World Population data analysis.ipynb](https://colab.research.google.com/drive/1hqWHEV4Te2nJe0maH8p4-QsLVL_Yzhuv?usp=sharing)
- **Dataset**: Included in the repository as `Total.csv` and `Metadata.csv`

## 📂 File Structure
Here's an overview of the files in this repository:
```
World-Population-Data-Analysis/
├── README.md
├── World_Population.pbix
├── World_Population_data_analysis.ipynb
├── total.csv
├── metadata.csv
└── total_cleaned.csv
```

1. **README.md**: This file, containing detailed information about the project.
2. **World_Population.pbix**: A Power BI file for advanced visualization of the world population dataset.
3. **World_Population_data_analysis.ipynb**: A Jupyter Notebook containing Python code for data analysis and visualization.
4. **Total.csv**: Raw population data for all countries from 1960 to 2022.
5. **Metadata.csv**: Additional metadata about countries (e.g., income group, region).
6. **total_cleaned.csv**: The cleaned dataset used for analysis.

## 📜 Code Explanation

The project performs the following steps to clean and preprocess the population data:

1. **Load Data**:
   - The datasets `total.csv` and `metadata.csv` are loaded using `pandas`:
   ```python
   total = pd.read_csv("/path/to/Total.csv")
   metadata = pd.read_csv("/path/to/Metadata.csv")
   ```

2. **Data Inspection**:
   - Inspect the first few rows of the datasets to understand their structure:
   ```python
   total.head()  
   metadata.head()
   ```

3. **Data Cleaning**:
   - **Drop unnecessary columns**: Remove columns that aren't needed for analysis.
   ```python
   total = total.drop(columns=['Indicator Name', 'Indicator Code', '2023']).dropna()
   metadata = metadata.drop(columns=['SpecialNotes']).dropna()
   ```

4. **Merge Datasets**:
   - The `total` dataset (containing population data) is merged with the `metadata` dataset (containing country metadata) on the `Country Code`.
   ```python
   data = (total.merge(metadata, on='Country Code')
           .rename(columns={'Country Name': 'Country', 'IncomeGroup': 'Income'}))
   ```

5. **Reshape the Data**:
   - The data is reshaped from wide format (years as columns) to long format (years as rows) using `melt()`.
   ```python
   data = data.melt(id_vars=['Country', 'Region', 'Income'],
                    value_vars=[str(year) for year in range(1960, 2023)],
                    var_name='Year', value_name='Population')
   ```

6. **Save Cleaned Data**:
   - The cleaned data is saved as `total_cleaned.csv` for further analysis or visualization.
   ```python
   data.to_csv("/path/to/total_cleaned.csv")
   ```

7. **Final Data**:
   - The final dataset contains columns like `Country`, `Region`, `Income`, `Year`, and `Population`.

## 📊 Key Insights
- **Population Trends**: Identified key trends and patterns in the global population data.
- **Visualizations**: Leveraged Python and Power BI to create impactful visualizations that aid in understanding demographic distributions and growth.
- **Actionable Insights**: Derived insights to inform decision-making and policy development.

## 🧠 Knowledge Gained
This project provided hands-on experience in:
- Data cleaning and preprocessing.
- Visualization techniques using Python libraries (e.g., Matplotlib, Seaborn) and Power BI.
- Interpreting demographic data to uncover trends and patterns.

## 🚀 Steps to Clone and Run

### 1. Clone the Repository
To clone the repository to your local machine, use the following command:
```bash
git clone https://github.com/jha-aman09/World-Population-Data-Analysis.git
```

### 2. Install Dependencies
Ensure you have the required Python libraries installed. You can do this by creating a virtual environment and installing the dependencies using `pip`:
```bash
cd World-Population-Data-Analysis
pip install -r requirements.txt
```

**Required libraries:**
- pandas
- numpy
- matplotlib
- seaborn

### 3. Run the Jupyter Notebook
After setting up your environment, you can open the Jupyter notebook `World_Population_data_analysis.ipynb`:
```bash
jupyter World_Population_data_analysis.ipynb
```
Navigate to the notebook and run the cells to see the analysis and visualizations.

### 4. Use Power BI (Optional)
You can also open the `World_Population.pbix` file in Power BI to explore advanced visualizations based on the cleaned data.

## ⭐ Stay Updated
Don't forget to **star** this repository to stay updated with the latest developments and insights!

## 📑 Keywords
- Data Science
- Data Visualization
- World Population
- Python
- Power BI
