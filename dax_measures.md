# DAX Measures

This document lists the key DAX measures used in the **Performance Overview Dashboard**.

## Core Measures

```DAX
Total Procedures =
COUNTROWS('fact_procedures')
```

```DAX
Completed Procedures =
CALCULATE(
    [Total Procedures],
    'fact_procedures'[IsCompleted] = 1
)
```

```DAX
Cancelled Procedures =
CALCULATE(
    [Total Procedures],
    'fact_procedures'[IsCancelled] = 1
)
```

```DAX
Postponed Procedures =
CALCULATE(
    [Total Procedures],
    'fact_procedures'[IsPostponed] = 1
)
```

```DAX
Emergency Procedures =
CALCULATE(
    [Total Procedures],
    'fact_procedures'[IsEmergency] = 1
)
```

```DAX
Elective Procedures =
CALCULATE(
    [Total Procedures],
    'fact_procedures'[IsEmergency] = 0
)
```

```DAX
Completion Rate =
DIVIDE(
    [Completed Procedures],
    [Total Procedures]
)
```

```DAX
Cancellation Rate =
DIVIDE(
    [Cancelled Procedures],
    [Total Procedures]
)
```

```DAX
Emergency Rate =
DIVIDE(
    [Emergency Procedures],
    [Total Procedures]
)
```

## Waiting Time Measures

```DAX
Average Waiting Days =
CALCULATE(
    AVERAGE('fact_procedures'[WaitingDays]),
    'fact_procedures'[IsCompleted] = 1
)
```

```DAX
Median Waiting Days =
CALCULATE(
    MEDIAN('fact_procedures'[WaitingDays]),
    'fact_procedures'[IsCompleted] = 1
)
```

## Duration and Utilisation Measures

```DAX
Average Procedure Duration =
CALCULATE(
    AVERAGE('fact_procedures'[ActualDurationMinutes]),
    'fact_procedures'[IsCompleted] = 1
)
```

```DAX
Total Actual Minutes =
SUM('fact_procedures'[ActualDurationMinutes])
```

```DAX
Total Available Minutes =
SUM('fact_or_sessions'[AvailableMinutes])
```

```DAX
Operating Room Utilisation =
DIVIDE(
    [Total Actual Minutes],
    [Total Available Minutes]
)
```

```DAX
Overtime Minutes =
SUM('fact_procedures'[OvertimeMinutes])
```

```DAX
Overtime Hours =
DIVIDE(
    [Overtime Minutes],
    60
)
```
