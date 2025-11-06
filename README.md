# 🏦 Banking Risk Analytics Dashboard (Power BI)

## 📘 Overview
The **Banking Risk Analytics Dashboard** is a comprehensive Power BI project designed to provide insights into banking operations, risk assessment, and client behavior.  
It enables financial institutions to make data-driven decisions by analyzing customer profiles, deposits, loans, and engagement patterns—ultimately helping minimize financial risk in lending.

---

## 🎯 Problem Statement
Banks and financial institutions face significant risks when lending money to customers. The primary challenge lies in identifying applicants who are less likely to default on their loans.  

The objective of this project is to:
> Develop a data-driven analytical solution using **Power BI** to understand risk analytics in banking and minimize potential financial losses through informed decision-making.

---

## 💡 Solution
This solution leverages **Power BI’s advanced visualization and analytical capabilities** to evaluate loan applications based on applicant profiles.  
It allows decision-makers to:
- Assess whether an applicant is likely to repay a loan.
- Visualize risk exposure across demographics, income groups, and banking relationships.
- Identify key patterns across deposits, loans, and client engagement metrics.

---

## 📊 About the Dataset
The dataset contains various **interrelated banking and client data tables** connected through primary and foreign keys.

### Key Tables:
- **Banking Relationship**
- **Client-Banking**
- **Gender**
- **Investment Advisor**
- **Period**

Each table contributes to understanding customer engagement, account performance, and financial exposure.

---

## 🧹 Data Cleaning & Preparation
Several data transformation and calculated columns were created to enhance analysis accuracy and performance:

1. **Engagement Timeframe**  
   Added to the *Client-Banking* table to track the timeline of a client’s relationship with the bank.

2. **Engagement Days**  
   Calculates how many days a client has been with the bank:
   ```DAX
   Engagement Days = DATEDIFF('Clients - Banking'[Joined Bank], TODAY(), DAY)
3. **Income Band** 

    Created **bins** for estimated income in the *Client-Banking* dataset to classify clients based on their income range.  
    This categorization helps in analyzing financial behavior and risk by income group.

    | Income Range | Category |
    |---------------|-----------|
    | `< 100,000` | Low Income |
    | `< 300,000` | Mid Income |

    This classification enables **comparative analysis** between low and mid-income clients across deposits, loans, and credit behavior.

---

4. **Processing Fees** 

    Derived a new column **Processing Fees** from the *Fee Structure* field.  
    It represents the percentage of total fees applied based on the type of fee structure.

**Logic:**
- If the *Fee Structure* is **High**, then  
  `Processing Fee = 0.05`

This helps calculate total fees dynamically for each client using DAX measures.

---

## 🧮 Calculated Measures (DAX Functions)

### 🔹 **SUM**
Adds all numerical values in a column.  
Used to calculate total deposits, loans, and account balances.

```DAX
Bank Deposit = SUM('Clients - Banking'[Bank Deposits])

Total Clients = DISTINCTCOUNT('Clients - Banking'[Client ID])

Total Fees = SUMX('Clients - Banking', [Total Loan] * 'Clients - Banking'[Processing Fees])

Engagement Days = DATEDIFF('Clients - Banking'[Joined Bank], TODAY(), DAY)
```

---

## 📈 Key Performance Indicators (KPIs)

| KPI | Description | Formula |
|-----|--------------|----------|
| **Total Clients** | Total number of clients in the banking system | `DISTINCTCOUNT('Clients - Banking'[Client ID])` |
| **Total Loan** | Combined value of bank loans, business lending, and credit card balances | `[Bank Loan] + [Business Lending] + [Credit Cards Balance]` |
| **Bank Loan** | Total loan amount owed by clients | `SUM('Clients - Banking'[Bank Loans])` |
| **Business Lending** | Total amount lent to small businesses | `SUM('Clients - Banking'[Business Lending])` |
| **Total Deposit** | Sum of all account deposits | `[Bank Deposit] + [Savings Account] + [Foreign Currency Account] + [Checking Accounts]` |
| **Total Fees** | Total amount charged for account setup and maintenance | `SUMX('Clients - Banking', [Total Loan] * 'Clients - Banking'[Processing Fees])` |
| **Checking Account Amount** | Total balance in checking accounts | `SUM('Clients - Banking'[Checking Accounts])` |
| **Total Credit Card Amount** | Total outstanding balance on credit cards | `SUM('Clients - Banking'[Amount of Credit Cards])` |
| **Savings Account Amount** | Total savings account balance | `SUM('Clients - Banking'[Saving Accounts])` |
| **Foreign Currency Amount** | Deposits held in non-domestic currencies | `SUM('Clients - Banking'[Foreign Currency Account])` |
| **Engagement Length** | Total duration of client relationships | `SUM('Clients - Banking'[Engagement Days])` |
| **Credit Card Balance** | Outstanding balance on all credit cards | `SUM('Clients - Banking'[Credit Card Balance])` |

---

## 📊 Visualizations

The dashboard contains multiple interactive pages for analysis:

### 🏠 Home Page
- Overview of total clients, deposits, loans, and key KPIs.  
- Gender and year-based segmentation.  
- High-level bank performance indicators.  

### 💰 Loan Analysis
Breakdown of total loans by:
- Income Band (High, Medium, Low)  
- Banking Relationship (Private, Retail, Commercial, Institutional)  
- Nationality (European, Asian, American, etc.)  
- Occupation and Gender  
- Visual comparisons of loan amounts across categories.  

### 💵 Deposit Analysis
Analysis of deposits across:
- Income Bands  
- Bank Relationships  
- Nationalities and Occupations  
- Evaluation of total, savings, checking, and foreign currency accounts.  

### 📋 Summary Dashboard
- Consolidated view of total clients, deposits, and loans.  
- Quick comparative insights for all metrics.  
- Highlights key business lending and engagement data.  

---

## 🧠 Insights & Results
- Enables **data-driven lending decisions** based on applicant risk profiles.  
- Identifies **banking relationships** with the highest client engagement and loan distribution.  
- Reveals **nationality-wise and gender-based trends** in loan and deposit activities.  
- Helps compare performance across **Private, Retail, Commercial, and Institutional Banks**.  
- Provides transparency in **risk evaluation** and **deposit/loan ratios**.  

---

## 🔮 Future Enhancements
- Integration with **real-time banking databases** for live analytics.  
- Implementation of **predictive modeling** to forecast loan default probabilities.  
- Addition of **AI-based segmentation** of clients by financial behavior and repayment patterns.  
- Enhanced **visual storytelling** with interactive drill-through reports.  
- Integration of **automated risk scoring dashboards**.  

---

## 🏁 Conclusion
Empowered by modern data visualization and analysis techniques, **Power BI dashboards** serve as powerful tools for the banking sector.  
This **Banking Risk Analytics Dashboard** provides a clear view of customer profiles, deposits, and lending trends—helping financial institutions make smarter, safer, and more strategic decisions.

By combining **data cleaning, calculated DAX measures, and meaningful KPIs**, this project demonstrates how Power BI can transform raw banking data into actionable insights for improved decision-making.

---

## ⚙️ Technical Details
- **Tool Used:** Microsoft Power BI  
- **Language:** DAX (Data Analysis Expressions)  
- **Dataset Type:** Relational (Multiple Linked Tables)  
- **Data Source:** Banking Client & Relationship Data  
- **Data Model:** Star Schema (Primary-Foreign Key Relationships)  
- **Key Functions Used:** SUM, DISTINCTCOUNT, SUMX, SWITCH, DATEDIFF  

---

📫 Contact Information

👤 Yanglesh Jaiswal  
🎓 Management Engineering Student | Data Analyst  
📍 Palermo, Italy  
📧 jaiswalyanglesh11@gmail.com  
📞 +39 3935524408  
### 🌐 Social Links  

<p align="left">
  <a href="https://www.linkedin.com/in/yanglesh-jaiswal/" target="_blank">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" alt="LinkedIn" width="40" height="40"/>
  </a>
  <a href="https://github.com/Yanglesh5139/" target="_blank">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" alt="GitHub" width="40" height="40"/>
  </a>
</p>

