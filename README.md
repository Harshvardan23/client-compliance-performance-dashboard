# client-compliance-performance-dashboard
An end-to-end Looker Studio dashboard built to monitor client lifecycle, onboarding compliance, document validity, and contract renewals at a PAN-India scale. Designed for both leadership visibility and operational accountability using advanced calculated fields and business logic.

![futuristic-technology-hologram.jpg](https://github.com/Harshvardan23/client-compliance-performance-dashboard/blob/main/assets/futuristic-technology-hologram.jpg)

# 📌 Project Overview

This project presents an end-to-end Client Compliance & Performance Dashboard built using Looker Studio for a PAN-India enterprise operating with a large and diverse client base.

The organization manages hundreds of clients across multiple regions, agreements, and engagement models. With data being generated continuously by on-ground teams through a Warehouse Management System (WMS), there was a need for a single, reliable source of truth to track client lifecycle health, compliance status, and operational performance.

This dashboard addresses that need by enabling:

. Internal teams to monitor progress, identify gaps, and act on compliance issues
. Leadership to gain clear visibility into on-ground execution and risk areas

The solution transforms raw operational data into actionable insights through structured KPIs, drill-downs, and advanced calculated fields that reflect real business rules.

# 🧑‍💻 Technologies Used

. Warehouse Management System (WMS) – Source of operational data
. PostgreSQL (pgAdmin) – Data storage, querying, and extraction
. Google sheet – Sanitized dataset for practice and reproducibility
. Looker Studio – Dashboarding and data visualization

# 🗂️ Data Schema – client_details Table

![client_database.drawio (1).png](https://github.com/Harshvardan23/client-compliance-performance-dashboard/blob/main/assets/client_database.drawio%20(1).png)

To maintain transparency and clarity around the underlying data model, this project is built on a centralized client-level table named client_details.
This table captures the entire client lifecycle, contractual information, compliance dates, and ownership metadata.

# 🗂️ Data Schema – client_details Table

![client_data_flow.drawio.png](https://github.com/Harshvardan23/client-compliance-performance-dashboard/blob/main/assets/client_data_flow.drawio.png)

This dashboard is powered by a simple and scalable end-to-end data pipeline designed to ensure data accuracy, freshness, and reliability.

## 🧠 How Data Moves

WMS
Operational data is captured continuously from on-ground teams across PAN India.

Cloud Storage (AWS)
Raw data is centrally stored to ensure scalability and availability.

Database Layer (PostgreSQL / pgAdmin)
Data is queried, validated, and structured into analysis-ready extracts.

Data Validation (Google Sheets)
Controlled corrections and sanity checks are applied where required.

Visualization (Looker Studio)
Cleaned data is visualized using KPIs, filters, and calculated fields.
