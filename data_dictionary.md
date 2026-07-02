# Data Dictionary

This folder contains a fully synthetic dataset for the **Performance Overview Dashboard** Power BI portfolio project.

## Confidentiality

This dataset is synthetic. It was generated to reflect realistic operational patterns in a surgical operations reporting scenario. No real patient-level data, confidential hospital records, proprietary files, staff names, or identifiable organisational information has been used.

## Tables

### fact_procedures.csv

Main transaction table. Each row represents one scheduled procedure.

Key columns:

- `ProcedureID`: unique synthetic procedure identifier.
- `ScheduledDateKey`: key used to connect to `dim_date`.
- `RequestDate`: synthetic request date.
- `ScheduledDate`: synthetic scheduled procedure date.
- `ActualStartDateTime`: actual start time for completed procedures.
- `ActualEndDateTime`: actual end time for completed procedures.
- `DepartmentID`: connects to `dim_department`.
- `ProcedureCategoryID`: connects to `dim_procedure_category`.
- `OperatingRoomID`: connects to `dim_operating_room`.
- `CaseTypeID`: connects to `dim_case_type`.
- `StatusID`: connects to `dim_status`.
- `CancellationReasonID`: connects to `dim_cancellation_reason`.
- `PriorityGroupID`: connects to `dim_priority_group`.
- `PlannedDurationMinutes`: planned procedure duration.
- `ActualDurationMinutes`: actual duration for completed procedures.
- `WaitingDays`: days between request date and scheduled date.
- `TurnaroundMinutes`: time between completed procedures.
- `OvertimeMinutes`: minutes beyond planned session end time.
- `IsEmergency`, `IsCompleted`, `IsCancelled`, `IsPostponed`: binary flags.

### fact_or_sessions.csv

Supporting capacity table. Each row represents one planned operating room session.

### Dimension tables

- `dim_date.csv`: calendar table.
- `dim_department.csv`: surgical service areas.
- `dim_procedure_category.csv`: synthetic procedure categories.
- `dim_operating_room.csv`: synthetic operating room details.
- `dim_case_type.csv`: elective or emergency.
- `dim_status.csv`: completed, cancelled, postponed.
- `dim_cancellation_reason.csv`: cancellation reason groups.
- `dim_priority_group.csv`: urgency/priority groups.
