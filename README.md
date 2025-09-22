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

### Power BI Dashboard
<img width="1158" height="652" alt="Screenshot 2025-09-20 192645" src="https://github.com/user-attachments/assets/90f00063-21f2-4be7-bd8a-5b985e2dc0bb" />

<img width="1012" height="461" alt="image" src="https://github.com/user-attachments/assets/5aefffd9-db83-4c19-9cab-dc0d91e21106" />


### Excel Pivot Tables

#### 1. Pivot Table – Average Charges by Smoker Status  
<img width="166" height="76" alt="Screenshot 2025-09-20 161421" src="https://github.com/user-attachments/assets/1c1e35e1-2bdd-491e-a06a-7665383b01bc" />

#### 2. Pivot Table – Average Charges by BMI Category  
 
<img width="128" height="86" alt="Screenshot 2025-09-20 161600" src="https://github.com/user-attachments/assets/7edf502f-2cf1-422e-8b69-29a2524360f0" />

#### 3. Pivot Table – Charges by Region  
<img width="350" height="270" alt="Screenshot 2025-09-20 193522" src="https://github.com/user-attachments/assets/2bd3ef98-76e9-4a53-8068-352e92df4871" />

## Chart

  <img width="821" height="468" alt="Screenshot 2025-09-20 194652" src="https://github.com/user-attachments/assets/2ea37518-8560-4547-8ae5-91669b6c6e10" />


---

## 🗄 SQL Queries  

  
```sql
---Average charges by smoker status---
SELECT smoker, ROUND(AVG(charges),2) AS avg_charges
FROM insurance
GROUP BY smoker
ORDER BY avg_charges DESC;
```

```sql
---Charges by BMI category---
SELECT 
    CASE 
        WHEN bmi < 18.5 THEN 'Underweight'
        WHEN bmi BETWEEN 18.5 AND 24.9 THEN 'Normal'
        WHEN bmi BETWEEN 25 AND 29.9 THEN 'Overweight'
        ELSE 'Obese'
    END AS bmi_category,
    ROUND(AVG(charges),2) AS avg_charges
FROM insurance
GROUP BY bmi_category
ORDER BY avg_charges DESC;
```

```sql
---Regional average charges---
SELECT region, ROUND(AVG(charges),2) AS avg_charges
FROM insurance
GROUP BY region
ORDER BY avg_charges DESC;
```

```sql
SELECT 
    CASE 
        WHEN children > 0 THEN 'With Children'
        ELSE 'No Children'
    END AS HasChildren,
    sex AS Gender,
    AVG(charges) AS AvgCharges,
    COUNT(*) AS PatientCount
FROM insurance
GROUP BY 
    CASE 
        WHEN children > 0 THEN 'With Children'
        ELSE 'No Children'
    END,
    sex
ORDER BY HasChildren, Gender;
```

---

## 🏷️ Author  

- **Name:** Jessica Osagie  
- **Email:** jessica.a.osagie@gmail.com   
- **LinkedIn:** [jessica-osagie](https://linkedin.com/in/jessica-osagie/)  
