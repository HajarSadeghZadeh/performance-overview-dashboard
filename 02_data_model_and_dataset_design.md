# Performance Overview Dashboard
## Data Model & Dataset Design

### 1. Purpose of the Dataset

This dataset supports a public Power BI portfolio project based on a surgical operations reporting scenario.

The dataset represents a synthetic version of hospital operational data, including scheduled procedures, completed procedures, cancellations, waiting times, emergency demand, operating room utilisation, and department-level performance.

No real patient records, confidential hospital data, proprietary data, or identifiable information is included.

### 2. Dataset Design Approach

The dataset is designed using a star schema / multi-fact star schema.

The model includes:

- One main fact table for procedure-level activity.
- One supporting fact table for operating room session capacity.
- Dimension tables for dates, departments, procedure categories, operating rooms, case types, statuses, cancellation reasons, and priority groups.

### 3. Fact Tables

#### Fact_Procedures

Each row represents one scheduled procedure.

Key fields:

- ProcedureID
- ScheduledDateKey
- RequestDate
- ScheduledDate
- ActualStartDateTime
- ActualEndDateTime
- DepartmentID
- ProcedureCategoryID
- OperatingRoomID
- CaseTypeID
- StatusID
- CancellationReasonID
- PriorityGroupID
- PlannedDurationMinutes
- ActualDurationMinutes
- WaitingDays
- TurnaroundMinutes
- OvertimeMinutes
- IsEmergency
- IsCompleted
- IsCancelled
- IsPostponed

#### Fact_OR_Sessions

Each row represents one planned operating room session.

Key fields:

- SessionID
- DateKey
- OperatingRoomID
- DepartmentID
- SessionType
- PlannedStartDateTime
- PlannedEndDateTime
- PlannedMinutes
- AvailableMinutes
- IsEmergencySession

### 4. Dimension Tables

The model includes:

- Dim_Date
- Dim_Department
- Dim_ProcedureCategory
- Dim_OperatingRoom
- Dim_CaseType
- Dim_Status
- Dim_CancellationReason
- Dim_PriorityGroup

### 5. Recommended Relationships

| Dimension Table | Column | Fact Table | Column |
|---|---|---|---|
| Dim_Date | DateKey | Fact_Procedures | ScheduledDateKey |
| Dim_Date | DateKey | Fact_OR_Sessions | DateKey |
| Dim_Department | DepartmentID | Fact_Procedures | DepartmentID |
| Dim_Department | DepartmentID | Fact_OR_Sessions | DepartmentID |
| Dim_ProcedureCategory | ProcedureCategoryID | Fact_Procedures | ProcedureCategoryID |
| Dim_OperatingRoom | OperatingRoomID | Fact_Procedures | OperatingRoomID |
| Dim_OperatingRoom | OperatingRoomID | Fact_OR_Sessions | OperatingRoomID |
| Dim_CaseType | CaseTypeID | Fact_Procedures | CaseTypeID |
| Dim_Status | StatusID | Fact_Procedures | StatusID |
| Dim_CancellationReason | CancellationReasonID | Fact_Procedures | CancellationReasonID |
| Dim_PriorityGroup | PriorityGroupID | Fact_Procedures | PriorityGroupID |

### 6. Data Period

The synthetic dataset covers 1 January 2022 to 31 December 2024.

### 7. Synthetic Data Logic

The dataset reflects realistic operational patterns including weekday activity, emergency demand, variation in procedure durations, waiting times, cancellations, and utilisation.
