# 🩺 Health / Medical Cost Analysis  

## 📑 Table of Contents  
- [Dataset Overview](#-dataset-overview)  
- [Problem Statement](#-problem-statement)  
- [Objectives](#-objectives)  
- [Tools Used](#-tools-used)  
- [Key Insights](#-key-insights)  
- [Visualizations](#-visualizations)  
- [SQL Queries](#-sql-queries)  
- [Author](#-author)  

---

## 📊 Dataset Overview  

**Source:** [Kaggle – Medical Cost Personal Dataset](https://www.kaggle.com/datasets/mirichoi0218/insurance)  

This dataset contains information on patient demographics, health factors, and medical charges.  
Below are the first 3 records:  

| age | sex    | bmi   | children | smoker | region    | charges   |  
|-----|--------|-------|----------|--------|-----------|-----------|  
| 19  | female | 27.9  | 0        | yes    | southwest | 16884.92  |  
| 18  | male   | 33.77 | 1        | no     | southeast | 1725.55   |  
| 28  | male   | 33    | 3        | no     | southeast | 4449.46   |  

---

## ❓ Problem Statement  

Healthcare providers and insurers face growing pressure to balance patient outcomes with rising medical costs. Companies like **Optum**, a leading US health technology and analytics company, leverage real-world data to uncover drivers of healthcare expenses.  

The challenge is: **What factors significantly influence medical charges, and how can insurers use this insight to design better pricing and care strategies?**  

---

## 🎯 Objectives  

This project seeks to:  
1. **Analyze** patient demographics and lifestyle factors that influence medical charges.  
2. **Identify high-risk groups** (e.g., smokers, obese individuals) that disproportionately contribute to healthcare costs.  
3. **Benchmark average medical expenses** across different regions and population groups.  
4. **Provide insights for cost management** that could support companies like **Optum** in designing data-driven insurance and care models.  
5. **Demonstrate practical data analytics skills** (SQL, Excel, visualization) applied to real-world healthcare cost data.  

---

## 🛠 Tools Used  

- **Excel**: Pivot tables and charts for summary analysis.  
- **SQL**: Querying patterns and extracting insights.  
- **Power BI**: Interactive dashboards.  

---

## 🔑 Key Insights  

1. **Smokers vs Non-Smokers:** Smokers pay over **twice the average medical charges** compared to non-smokers, highlighting smoking as the strongest cost driver.  
2. **BMI Impact:** Obese patients (BMI > 30) show significantly higher average charges, reinforcing the link between weight and healthcare costs.  
3. **Regional Variance:** The **southeast region** records the highest medical charges, suggesting lifestyle or demographic factors at play.  
4. **Children Factor:** Having more children slightly raises average charges, but the impact is smaller compared to smoking and BMI.  
5. **Gender:** Charges do not differ significantly between males and females, indicating lifestyle factors matter more than gender.  

---

## 📊 Visualizations  

### 1. Pivot Table – Average Charges by Smoker Status  
*(Excel pivot showing smokers vs non-smokers)*  

### 2. Pivot Table – Average Charges by BMI Category  
*(Underweight, Normal, Overweight, Obese grouped)*  

### 3. Pivot Table – Charges by Region  
*(Bar chart comparing regions)*  

---

## 🗄 SQL Queries  

### Query 1 – Average charges by smoker status  
```sql
SELECT smoker, ROUND(AVG(charges),2) AS avg_charges
FROM insurance
GROUP BY smoker
ORDER BY avg_charges DESC;
