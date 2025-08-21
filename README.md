# Indian_Elections_2024_Analysis_
---
## 📌 Project Overview  
This project analyzes the **India General Election Results – 2024** using **Power BI dashboards** and **SQL queries**.  
It provides insights into party performance, state demographics, constituency-level outcomes, and overall election trends.  

The project is designed for **political analysts, researchers, policymakers, and the public** to better understand the 2024 Lok Sabha results.  

---

## 📊 Dashboards  

### 1. **Overview Analysis**  
- NDA seats, % share, and detailed breakdown  
- I.N.D.I.A. seats, % share, and detailed breakdown  
- Independent & Other party seats  
- Party-wise performance with logos  

---

### 2. **State Demographics Analysis**  
- State-wise total seats, NDA seats, I.N.D.I.A. seats  
- Map chart with tooltips (majority alliance, total seats)  
- Winning candidate & margin (bubble map view)  
- State with maximum seats won  

---

### 3. **Political Landscape by State**  
- Dynamic state filter  
- Party-wise grid results with alliances  
- Party-wise seat share (donut chart)  
- Map of constituencies in the selected state  

---

---

### 5. **Details Grid**  
- Full tabular dataset (constituency → winner, runner-up, alliance, votes, margin)  
- Drill-through from other dashboards  
- Export to Excel option  

---

## 🛠 Tech Stack  
- **Power BI Desktop** – Data visualization & dashboard building  
- **SQL (MS SQL Server)** – Data extraction and transformation  
- **Dataset(Kaggle)** – Constituency-wise, state-wise, and party-wise election results (India 2024)  

---

## 🗄 Dataset  
The dataset includes:  
- **Constituency-wise results**  
- **State-wise results**  
- **Party-wise results**  
- Candidate-level details (EVM votes, postal votes, margins)  

---

## 🧑‍💻 SQL Queries & Analysis  

Some example queries used in the analysis:  

```sql
-- Total Seats
SELECT DISTINCT COUNT(Parliament_Constituency) AS Total_Seats
FROM constituencywise_results;

-- Total Seats by State
SELECT s.State AS State_Name,
       COUNT(cr.Constituency_ID) AS Total_Seats_Available
FROM constituencywise_results cr
JOIN statewise_results sr ON cr.Parliament_Constituency = sr.Parliament_Constituency
JOIN states s ON sr.State_ID = s.State_ID
GROUP BY s.State
ORDER BY s.State;

-- NDA Total Seats Won
SELECT SUM(CASE WHEN party IN ('Bharatiya Janata Party - BJP', 'Telugu Desam - TDP', 'JD(U)', 'Shiv Sena - SHS', ...)
                THEN [Won] ELSE 0 END) AS NDA_Total_Seats_Won
FROM partywise_results;
