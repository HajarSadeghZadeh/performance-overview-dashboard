# Performance Overview Dashboard

A Power BI portfolio project demonstrating healthcare operations reporting, data modelling, DAX measure development, and executive dashboard design.

## Project Summary

This project presents an end-to-end business intelligence solution for monitoring surgical operations performance. The dashboard is designed to help stakeholders understand procedure activity, elective and emergency demand, waiting times, cancellations, department-level performance, and operating room utilisation.

The project demonstrates how operational data can be transformed into a structured reporting model and an executive-level Power BI dashboard that supports performance monitoring and service planning.

## Dashboard Preview

![Executive Overview](images/executive_overview.png)

## Business Context

Healthcare operations teams often need to monitor activity across multiple service areas, including elective and emergency procedures, waiting lists, cancellations, operating room capacity, and department performance.

A key challenge is converting detailed operational records into clear, decision-ready insights. This dashboard addresses that challenge by bringing key metrics into one reporting view and allowing users to analyse performance by time period, department, case type, procedure status, and other operational dimensions.

## Key Questions Answered

This dashboard helps answer questions such as:

- How many procedures were scheduled and completed?
- What proportion of procedures were elective versus emergency?
- Which departments have the highest procedure volume?
- How are waiting times changing over time?
- Which departments have higher cancellation rates?
- How effectively is operating room capacity being used?
- Where may operational pressure or service bottlenecks exist?

## Dashboard Features

- Executive KPI cards for high-level performance monitoring
- Monthly procedure trend analysis
- Elective versus emergency case mix
- Department-level performance comparison
- Cancellation and waiting time indicators
- Interactive slicers for year, department, case type, and procedure status
- Star-schema data model designed for scalable Power BI reporting
- DAX measures for operational KPIs and performance metrics

## Data Model

The Power BI model is designed using a star-schema structure with fact and dimension tables.

Main fact tables:

- `fact_procedures`
- `fact_or_sessions`

Dimension tables:

- `dim_date`
- `dim_department`
- `dim_procedure_category`
- `dim_operating_room`
- `dim_case_type`
- `dim_status`
- `dim_cancellation_reason`
- `dim_priority_group`

![Data Model](images/data_model.png)

More details are available in:

- [Data Model & Dataset Design](documentation/02_data_model_and_dataset_design.md)
- [Data Dictionary](documentation/data_dictionary.md)

## DAX Measures

The report includes DAX measures for:

- total procedures
- completed procedures
- cancellation rate
- emergency rate
- average waiting days
- operating room utilisation
- overtime hours
- capacity-related cancellations

Example measure:

```DAX
Cancellation Rate =
DIVIDE(
    [Cancelled Procedures],
    [Total Procedures]
)
```

Full measure documentation is available here:

- [DAX Measures](documentation/dax_measures.md)

![DAX Measures](images/dax_measures.png)

## Repository Structure

```text
performance-overview-dashboard/
├── README.md
├── data/
│   ├── fact_procedures.csv
│   ├── fact_or_sessions.csv
│   ├── dim_date.csv
│   ├── dim_department.csv
│   ├── dim_procedure_category.csv
│   ├── dim_operating_room.csv
│   ├── dim_case_type.csv
│   ├── dim_status.csv
│   ├── dim_cancellation_reason.csv
│   └── dim_priority_group.csv
├── documentation/
│   ├── 01_business_requirements.md
│   ├── 02_data_model_and_dataset_design.md
│   ├── data_dictionary.md
│   └── dax_measures.md
├── images/
│   ├── executive_overview.png
│   ├── data_model.png
│   └── dax_measures.png
└── powerbi/
    └── performance_overview_dashboard.pbix
```

## Tools and Skills Demonstrated

- Power BI dashboard development
- Data modelling and star-schema design
- DAX measure development
- KPI design
- Healthcare operations reporting
- Executive dashboard design
- Data storytelling
- Performance monitoring
- GitHub project documentation

## Project Files

- [Business Requirements](documentation/01_business_requirements.md)
- [Data Model & Dataset Design](documentation/02_data_model_and_dataset_design.md)
- [Data Dictionary](documentation/data_dictionary.md)
- [DAX Measures](documentation/dax_measures.md)

## Data Note

This public portfolio project uses a structured demonstration dataset designed to reflect realistic healthcare operations patterns. No confidential, proprietary, patient-level, or identifiable organisational information is included.

## Author

**Hajar Sadegh Zadeh**  
Business Intelligence | Healthcare Analytics | Data Modelling | Power BI | Optimisation
