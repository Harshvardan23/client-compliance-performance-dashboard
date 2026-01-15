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

To maintain transparency and clarity around the underlying data model, this project is built on a centralized client-level table named client_details.
This table captures the entire client lifecycle, contractual information, compliance dates, and ownership metadata.

📌 Table Purpose

The client_details table acts as the single source of truth for:

. Client identity and geography
. Agreement and engagement details
. Contractual validity
. Compliance timelines
. Operational ownership

🧾 Schema Overview

🔑 Key Fields Explained

Client Identification

. Client ID
. Client Internal ID
. Client Name
. Client PAN Number
. Client CIN Number
. Client GST Number

Geographic & Ownership Details

. Region Name
. State
. ZIP Code
. Regional Head

Business & Agreement Information

. Product Name
. Agreement Name
. Dealing Mode
. Service Charge
. Trainee Fee

Lifecycle & Status

. Client Onboarding Date
. Status (Approved, Inactive, Draft, Returned)

Contract & Compliance Dates

. Contract Start Date
. Contract End Date
. WC Start Date / WC End Date
. MC Start Date / MC End Date
. GPA Start Date / GPA End Date

📌 This structure enables date-aware compliance tracking, contract validity checks, and lifecycle analysis directly at the reporting layer.
