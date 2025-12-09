# Equipment Health Index Dashboard

Excel-based dashboard to monitor equipment performance using maintenance KPIs (Uptime, MTBF, MTTR, Fuel Usage) and a combined Health Index.

## Features
- Tracks Uptime %, MTBF, MTTR, Availability, Fuel usage  
- Equipment Health Index (0–100) from weighted KPIs  
- Charts for trends and comparison  
- Highlights bad actors for maintenance focus  

## Sheets
- `Dashboard` – KPIs, charts, status (RAG)  
- `Equipment_Master` – equipment list, basic details, KPI targets  
- `Operating_Data` – period-wise hours, failures, fuel  
- `Failure_Log` – breakdowns, repair time, cost  
- `KPI_Calculations` – aggregated metrics and formulas  
- `Health_Index_Model` – normalization and Health Index weights  

## How to Use
1. Fill `Equipment_Master`, `Operating_Data`, and `Failure_Log`.  
2. Refresh calculations/pivots in `KPI_Calculations`.  
3. Review `Dashboard` to monitor health and plan maintenance.
