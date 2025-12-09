# -Equipment-Health-Index-Dashboard
An Excel-based dashboard for monitoring equipment condition using key maintenance KPIs such as uptime, MTBF, MTTR, and fuel usage. This project helps maintenance and operations teams make data-driven decisions on preventive maintenance, asset replacement, and resource planning.

Features
Track core KPIs per equipment:

Uptime %

MTBF (Mean Time Between Failures)

MTTR (Mean Time To Repair)

Availability

Fuel usage and fuel efficiency

Equipment Health Index (0–100) combining multiple KPIs

Visual dashboard with charts and status indicators

Identification of “bad actor” equipment (low reliability, high downtime)

Support for monthly trend analysis and maintenance planning

File Structure
Suggested Excel workbook structure:

Dashboard

KPI cards for each equipment (Uptime %, MTBF, MTTR, Health Index)

Overall fleet summary

Charts:

Monthly uptime trend

MTBF and MTTR comparison by equipment

Fuel usage and cost trend

Conditional formatting for red/amber/green status vs targets

Equipment_Master

Static information for each asset:

Equipment_ID

Equipment_Name

Type / Category

Location

Commissioning_Date

Target_Uptime_%

Target_MTBF_Hours

Target_MTTR_Hours

Used as the central reference table for lookups.

Operating_Data

Time-based (daily or monthly) operating records:

Date / Month

Equipment_ID

Planned_Hours

Operating_Hours

Downtime_Hours

Number_of_Failures

Fuel_Consumed (liters)

This sheet is the primary raw data input for uptime, MTBF, and fuel metrics.

Failure_Log

Detailed maintenance event log:

Failure_ID

Equipment_ID

Failure_DateTime

Repair_Start

Repair_End

Repair_Duration_Hours

Failure_Mode

Root_Cause

Parts_Cost

Labor_Hours

Labor_Rate

Used to calculate MTTR and maintenance cost.

KPI_Calculations

Aggregated and calculated metrics per equipment and period:

Total_Planned_Hours

Total_Operating_Hours

Total_Downtime_Hours

Total_Failures

Total_Repair_Duration

Fuel_Consumed

Maintenance_Cost

Calculated fields (examples):

Uptime_% = Total_Operating_Hours / Total_Planned_Hours

MTBF_Hours = Total_Operating_Hours / Total_Failures

MTTR_Hours = Total_Repair_Duration / Total_Failures

Availability = MTBF_Hours / (MTBF_Hours + MTTR_Hours)

Fuel_per_Hour = Fuel_Consumed / Total_Operating_Hours

Intermediate normalized scores for Health Index (0–100 scaling).

Health_Index_Model

Defines how the Equipment Health Index is computed:

Normalized_Uptime_Score

Normalized_MTBF_Score

Normalized_MTTR_Score (inverted, lower MTTR = higher score)

Normalized_Fuel_Efficiency_Score

Example weight configuration:

Uptime: 40%

MTBF: 30%

MTTR: 20%

Fuel_Efficiency: 10%

Health_Index = 0.4 × Uptime_Score + 0.3 × MTBF_Score + 0.2 × MTTR_Score + 0.1 × Fuel_Score

Data Flow
User Inputs

Add or update equipment information in Equipment_Master.

Enter or import operating data into Operating_Data.

Log every failure/repair in Failure_Log.

Calculations

Use pivot tables or formulas to aggregate raw data into KPI_Calculations.

Compute KPI values and normalized scores.

Calculate Equipment Health Index per equipment and per month.

Visualization

Build charts on the Dashboard sheet based on KPI_Calculations and Health_Index_Model.

Add slicers for:

Equipment

Month / Year

Location

Use conditional formatting to highlight:

Uptime below target

MTTR above target

Low Health Index

Example KPIs (per Equipment, per Month)
Uptime_%

Input: Planned_Hours, Operating_Hours

Formula (concept): Operating_Hours / Planned_Hours

MTBF_Hours

Input: Operating_Hours, Number_of_Failures

Formula (concept): Operating_Hours / Number_of_Failures

MTTR_Hours

Input: Total_Repair_Duration, Number_of_Failures

Formula (concept): Total_Repair_Duration / Number_of_Failures

Availability

Input: MTBF_Hours, MTTR_Hours

Formula (concept): MTBF_Hours / (MTBF_Hours + MTTR_Hours)

Fuel_Efficiency

Input: Fuel_Consumed, Operating_Hours

Formula (concept): Operating_Hours / Fuel_Consumed or Fuel_Consumed / Operating_Hours (choose one and keep consistent)

How to Use
Open the Excel workbook.

Populate Equipment_Master with all equipment details.

Enter historical and ongoing data into:

Operating_Data

Failure_Log

Refresh pivot tables or calculated ranges in KPI_Calculations.

Review the Dashboard:

Monitor monthly trends.

Identify low-performing equipment by Health Index.

Plan preventive maintenance where MTBF drops or MTTR rises.

Periodically adjust targets and weights in Health_Index_Model based on business priorities.

Possible Outcomes / Benefits
Improved uptime and availability through visibility of critical KPIs.

Better maintenance planning based on MTBF and MTTR trends.

Identification of equipment needing overhaul, replacement, or design changes.

Optimized fuel usage and reduced operating cost.

Clear, visual communication of asset condition to management.

Customization Ideas
Add cost KPIs: cost per hour, cost per ton, etc.

Add safety indicators (incidents per equipment).

Connect to a CSV export from a CMMS or SCADA system for semi-automatic data refresh.

Protect calculation sheets and expose only input and dashboard sheets to end users.
