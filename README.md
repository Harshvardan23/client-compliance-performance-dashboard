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

# 🔄 Data Flow 

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

# ❓ Business Questions Answered

### How many clients are currently active, inactive, returned, or in draft state?

![executive summary.png](https://github.com/Harshvardan23/client-compliance-performance-dashboard/blob/main/assets/executive%20summary.png)

## Design Challenge

The underlying schema contains only one status column (Status), which stores values such as: Approved, Inactive, Returned, Draft. There are no separate columns for each status category.

## ⚙️ Metric Logic Approach

The source table contains a single Status field that represents the current state of each client. To compute status-wise metrics without modifying the schema, conditional calculated fields were used in Looker Studio.

CASE
  WHEN Status = 'Inactive'
  THEN Client ID
  ELSE NULL
END

CASE
  WHEN Status = 'Returned'
  THEN Client ID
  ELSE NULL
END

The same pattern is reused for:

Approved Clients

Draft Clients

# 📈 Monthly Onboarding Trend (Year-over-Year)

### This visualization compares monthly client onboarding trends across different calendar years to identify growth patterns and seasonality. Only approved clients with valid onboarding dates are included to ensure accuracy and consistency

![YOY client onboarding.png](https://github.com/Harshvardan23/client-compliance-performance-dashboard/blob/main/assets/YOY%20client%20onboarding.png)

## ⚙️ Metric Logic Approach

The Y-axis is driven by year-specific calculated fields, derived from the same onboarding date column.

🟢 Clients Onboarded in 2025

CASE
  WHEN YEAR(Client Onboarding Date) = 2025
       AND Client Onboarding Date IS NOT NULL
       AND Status = 'Approved'
  THEN Client ID
  ELSE NULL
END

🔵 Clients Onboarded in 2024

CASE
  WHEN YEAR(Client Onboarding Date) = 2024
       AND Client Onboarding Date IS NOT NULL
       AND Status = 'Approved'
  THEN Client ID
  ELSE NULL
END

# 📊 Regional Head – Client Compliance Performance

### This section evaluates client compliance performance at a leadership ownership level by comparing total clients, approved (active) clients, and active ratio across Regional Heads. The intent is to: Highlight ownership-driven performance, Identify regions below / above target, Enable quick leadership intervention

![RH client comparison.png](https://github.com/Harshvardan23/client-compliance-performance-dashboard/blob/main/assets/RH%20client%20comparison.png)

## ⚙️ Active Ratio Calculation

The Active Ratio (%) represents the proportion of approved clients out of the total client base under each Regional Head.

SUM(
  CASE
    WHEN Status = 'Approved' THEN Client ID
    ELSE NULL
  END
)
/
SUM(Client ID)

🟢 High Active Ratio (> 90%)

CASE
  WHEN
    COUNT(
      CASE
        WHEN Status = 'Approved' THEN Client ID
        ELSE NULL
      END
    ) * 100
    /
    COUNT(
      CASE
        WHEN Client ID > 0 THEN Client ID
        ELSE NULL
      END
    ) > 90
  THEN
    COUNT(
      CASE
        WHEN Status = 'Approved' THEN Client ID
        ELSE NULL
      END
    )
    /
    COUNT(
      CASE
        WHEN Client ID > 0 THEN Client ID
        ELSE NULL
      END
    )
  ELSE NULL
END

🟡 Mid Active Ratio (70% – 90%)

CASE
  WHEN
    COUNT(
      CASE
        WHEN Status = 'Approved' THEN Client ID
        ELSE NULL
      END
    ) * 100
    /
    COUNT(
      CASE
        WHEN Client ID > 0 THEN Client ID
        ELSE NULL
      END
    ) > 70
    AND
    COUNT(
      CASE
        WHEN Status = 'Approved' THEN Client ID
        ELSE NULL
      END
    ) * 100
    /
    COUNT(
      CASE
        WHEN Client ID > 0 THEN Client ID
        ELSE NULL
      END
    ) < 90
  THEN
    COUNT(
      CASE
        WHEN Status = 'Approved' THEN Client ID
        ELSE NULL
      END
    )
    /
    COUNT(
      CASE
        WHEN Client ID > 0 THEN Client ID
        ELSE NULL
      END
    )
  ELSE NULL
END

--- 

# 🖥️ Dashboard Preview
![Dashboard 01](assets/dashboard_01.png)
![Dashboard 02](assets/dashboard_02.png)
![Dashboard 03](assets/dashboard_03.png)
![Dashboard 04](assets/dashboard_04.png)
![Dashboard 05](assets/dashboard_05.png)
![Dashboard 06](assets/dashboard_06.png)

--- 

# 👨‍💻 Author
@https://github.com/Harshvardan23

