# Siem-Dashboards-Alerts
**Overview**
This project demonstrates how to create custom dashboards, visualizations, and alerts in Splunk. The objective was to ingest log data, analyze failed login activity, visualize the results through dashboard panels, and configure alerts to detect suspicious activity automatically.

**Environment**
Splunk Enterprise
Virtual Machine (Windows/Linux)
Custom test log files
Real-time file monitoring
Log Creation and Data Ingestion

To begin the project, a custom log file was created on the virtual machine and added to Splunk through file monitoring.

The log contained multiple login events, including failed authentication attempts. Once indexed in Splunk, searches were performed using the keyword:

FAILED

This search returned all events containing the word "FAILED", allowing failed login activity to be analyzed and visualized.

**Dashboard Panels**
Panel 1: Failed Logins Over Time (Line Chart)
Search Query:
FAILED | timechart count

This dashboard panel displays the number of failed login events over time, making it easier to identify trends or spikes in authentication failures.

**Visualization**
Line Chart

**Purpose**
Track failed login activity over time
Identify unusual increases in failed logins
Support incident detection and investigations
Panel 2: Failed Logins by User (Pie Chart)
Search Query:
FAILED | stats count by user

This panel displays which user accounts generated the most failed login attempts.

**Visualization**
Pie Chart
**Purpose**
Identify targeted accounts
Detect accounts experiencing repeated login failures
Highlight potential brute-force attempts
Panel 3: Failed Logins by IP Address (Bar Chart)
Search Query:
FAILED | stats count by src_ip

This dashboard panel displays the number of failed login attempts originating from each IP address.

**Visualization**
Bar Chart
**Purpose**
Identify suspicious source IPs
Detect repeated authentication failures from specific hosts
Support threat hunting activities

**Final Dashboard**

The completed dashboard contains:

Failed Logins Over Time (Line Chart)
Failed Logins by User (Pie Chart)
Failed Logins by IP Address (Bar Chart)

Together, these visualizations provide a clear overview of failed authentication activity and potential indicators of brute-force attacks.

**Alert Creation**
**Objective**

Create an alert that triggers when the number of failed login events exceeds a predefined threshold.

Alert Condition

FAILED | stats count

Trigger condition:

count > 5
**Configuration**
Alert Type: Scheduled
Severity: Critical
Schedule: Every 1 minute
Alert Validation
Initial Test

A new test log file containing three failed login events was created and monitored by Splunk in real time.

**Result:**

Failed Event Count = 3
 
Since the count was below the configured threshold, the alert did not trigger.

**Trigger Test**

Six additional failed login entries were added to the monitored log file.

**Result:**

Failed Event Count = 9

Since the count exceeded the alert threshold (greater than 5), the alert was successfully triggered.

**Results**

This project successfully demonstrated:

Log ingestion into Splunk
Search and filtering of authentication events
Dashboard creation and visualization
Data analysis using SPL queries
Alert creation and scheduling
Real-time monitoring and alert validation

**Skills Demonstrated**
Splunk Search Processing Language (SPL)
Dashboard Development
Data Visualization
Security Monitoring
Alert Engineering
Log Analysis
Threat Detection
SOC Analyst Fundamentals
