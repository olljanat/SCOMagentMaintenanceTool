# SCOM Agent Maintenance Tool
This tool can be used to allow server admins to enable/disable SCOM maintenance from any server.

Tool uses SCOM databases stored procedures (p_MaintenanceModeStart/p_MaintenanceModeStop/p_MaintenanceModeUpdate) which why tool is very fast and using it can be delegated for users who don't have rights to SCOM server.

This project also contains SQL reporting server report "SCOM_ServersOnMaintenanceMode.rdl" which can be used to report which servers are on maintenance mode.

## Installation
Do installation using "Run as administrator.cmd" to single computer and using Install.ps1 for mass deployments.

## Configuring
* Configure SCOM database connection string to "SCOMdbConnectionString" variable on SCOMagentMaintenanceTool.exe.config
* Disable DebugMode after you are tested that application works on your environment

## SCOM database delegations
You can use this these commands to create "SCOMagentMaintenanceToolUser" role to SCOM database and after that you just need give that role for group where all server admins are:
* CREATE ROLE SCOMagentMaintenanceToolUser
* GRANT EXECUTE ON p_MaintenanceModeStart TO SCOMagentMaintenanceToolUser
* GRANT EXECUTE ON p_MaintenanceModeStop TO SCOMagentMaintenanceToolUser
* GRANT EXECUTE ON p_MaintenanceModeUpdate TO SCOMagentMaintenanceToolUser

You also need give db_datareader role for users.

## Build
* Run `build.cmd`

## Screenshots
### Debug mode
![Alt text](https://raw.githubusercontent.com/olljanat/SCOMagentMaintenanceTool/master/Screenshots/DebugMode.PNG "Debug mode")
### Normal mode
![Alt text](https://raw.githubusercontent.com/olljanat/SCOMagentMaintenanceTool/master/Screenshots/NormalMode_after_start.PNG "Normal mode after start")
![Alt text](https://raw.githubusercontent.com/olljanat/SCOMagentMaintenanceTool/master/Screenshots/NormalMode_maintenance_enabled.PNG "Normal mode maintenance enabled")
![Alt text](https://raw.githubusercontent.com/olljanat/SCOMagentMaintenanceTool/master/Screenshots/NormalMode_maintenance_updated.PNG "Normal mode maintenance updated")
![Alt text](https://raw.githubusercontent.com/olljanat/SCOMagentMaintenanceTool/master/Screenshots/NormalMode_maintenance_disabled.PNG "Normal mode maintenance disabled")
### SQL report
![Alt text](https://raw.githubusercontent.com/olljanat/SCOMagentMaintenanceTool/master/Screenshots/SQLreport.PNG "SQL report")