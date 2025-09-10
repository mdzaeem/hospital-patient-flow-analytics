## 📌 Project Overview
This project demonstrates a **real-time data engineering pipeline** for healthcare, designed to analyze **patient flow across hospital departments** using Azure cloud services.  
The pipeline ingests streaming data, processes it in **Databricks (PySpark)**, and stores it in **Azure Synapse SQL Pool** for analytics and visualization.

**Part 1 – Data Engineering:** Build the real-time ingestion + transformation pipeline.  
**Part 2 – Analytics:** Connect Synapse to Power BI and design an interactive dashboard for hospital KPIs.

For a full Youtube Tutorial of this project click this [Part-1 link](https://youtu.be/01LVHch-1x0?si=x70zJDO8OlK-bYJk)/[Part-2 link](https://youtu.be/1esHP63zLtM?si=e-pK7EcpK7yEOAyP).

## Pipeline

<img width="4719" height="2432" alt="Architecture" src="https://github.com/user-attachments/assets/cb1a1775-ab64-45d7-b45b-50ba97660e1d" />


---

## 🎯 Objectives
- Collect real-time patient data via **Azure Event Hub**.
- Process and cleanse data using **Databricks** (Bronze → Silver → Gold layers).
- Implement a **star schema** in **Synapse SQL Pool** for efficient querying.
- Enable **Version Control** with Git.

---

## 📂 Project Structure
```plaintext
real-time-patient-flow-azure/
│
├── databricks-notebooks/  # Transformation notebooks
│   ├── 01_bronze_rawdata.py
│   ├── 02_silver_cleandata.py
│   └── 03_gold_transform.py
├── simulator/             # Data simulation scripts
│   └── patient_flow_generator.py
├── sqlpool-quries/        # SQL scripts for Synapse
│   └── SQL_pool_quries.sql
├── git_commands/                  # Git Commands
└── README.md              # Project documentation
```

---

## 🛠️ Tools & Technologies
- **Azure Event Hub** – Real-time data ingestion
- **Azure Databricks** – PySpark-based ETL processing
- **Azure Data Lake Storage** – Staging raw and curated data
- **Azure Synapse SQL Pool** – Data warehouse for analytics
- **Power BI** – Dashboarding (future step)
- **Python 3.9+** – Core programming
- **Git** – Version control

---

## 📐 Data Architecture
The pipeline follows a **multi-layered architecture**:
- **Bronze Layer**: Raw JSON data from Event Hub stored in ADLS.
- **Silver Layer**: Cleaned and structured data (validated types, null handling).
- **Gold Layer**: Aggregated and transformed data ready for BI consumption.

---

## ⭐ Star Schema Design
The **Gold layer** data in Synapse follows a **star schema** for optimized analytics:
- **Fact Table**: `FactPatientFlow` (patient visits, timestamps, wait times, discharge)
- **Dimension Tables**:
  - `DimDepartment` – Department details
  - `DimPatient` – Patient demographic info
  - `DimTime` – Date and time dimension

---

## ⚙️ Step-by-Step Implementation

### **1. Event Hub Setup**
- Created **Event Hub namespace** and **patient-flow hub**.
- Configured **consumer groups** for Databricks streaming.

---

### **2. Data Simulation**
- Developed **Python script** `patient_flow_generator.py` to stream fake patient data (departments, wait time, discharge status) to Event Hub.
- [Producer Code](simulator/patient_flow_generator.py)

---

### **3. Storage Setup**
- Configured **Azure Data Lake Storage (ADLS Gen2)**.
- Created containers for **bronze**, **silver**, and **gold** layers.

---

### **4. Databricks Processing**
- [**Notebook 1**](databricks-notebooks/01_bronze_rawdata.py): Reads Event Hub stream into Bronze.
- [**Notebook 2**](databricks-notebooks/02_silver_cleandata.py): Cleans and validates schema.
- [**Notebook 3** ](databricks-notebooks/03_gold_transform.py): Aggregates and prepares star schema tables.

---

### **5. Synapse SQL Pool**
- Created **dedicated SQL Pool**.
- Executed schema and fact/dimension creation queries from:
  - [DDL_Qureis](sqlpool-quries/SQL_pool_quries.sql)

---

### **6. Version Control**
- Version control with **Git**:
  - [Commands reference](git_commands/git_bash)

---

## 📊 Data Analytics

Once the **data pipeline** was established and a **Star Schema** implemented in Synapse SQL Pool, the next step was to build an **interactive dashboard in Power BI**.  

### **🔗 Synapse → Power BI Connection**
- Connected **Azure Synapse SQL Pool** to Power BI using a direct SQL connection.  
- Imported **FactPatientFlow** and **Dimension tables**.  
- Established relationships for **Star Schema-based reporting**.  

### **📈 Dashboard Features**
The **Healthcare Patient Flow Dashboard** provides insights into:  
- **Bed Occupancy Rate** by department and gender.  
- **Patient Flow Trends** (admissions, wait times).  
- **Department-Level KPIs** (length of stay, Total Patients).  
- **Interactive Filters & Slicers** for gender.

<img width="1282" height="724" alt="Screenshot 2025-08-30 155951" src="https://github.com/user-attachments/assets/cf1f84dc-c1a5-4f07-84aa-1658abb4db16" />

---

## ✅ Key Outcomes
- **End-to-End Pipeline:** From **real-time ingestion → transformation → warehouse → analytics**.  
- **Scalable Architecture:** Easily adaptable for different hospital datasets.  
- **Business Insights:** Hospital admins can monitor **bed usage, patient flow, and department efficiency** in real time.  
- **Portfolio Value:** Demonstrates both **Data Engineering** and **Analytics skills** in one project.  

---

## 📜 License
This project is licensed under the **MIT License**.  
Feel free to use and adapt for learning or production.

---

**Author**: *Mohammed Zaeem* 

**LinkedIn**: [username]() 

**Contact**: [mail]()
