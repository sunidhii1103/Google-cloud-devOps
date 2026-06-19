# Google Cloud Lab: Monitoring and Dashboarding Multiple Projects

## Overview

This lab demonstrates how to implement centralized monitoring across multiple Google Cloud projects using Google Cloud Monitoring. A dedicated Monitoring Project was configured to host a Metrics Scope, allowing resources from multiple projects to be monitored from a single location.

The lab also covers Monitoring Groups, Uptime Checks, Alerting, Custom Dashboards, and Performance Monitoring to provide a complete introduction to Google Cloud Observability.

---

## Objectives

* Configure resource projects with Compute Engine instances.
* Deploy and validate NGINX web servers.
* Create a centralized Metrics Scope.
* Connect multiple projects to a Monitoring Project.
* Create Monitoring Groups and Subgroups using resource labels.
* Configure and test Uptime Checks.
* Investigate monitoring metrics, logs, and alerts.
* Build custom dashboards for observability.
* Generate workload traffic and analyze CPU utilization.

---

## Architecture

```text
                    Monitoring Project
                     (Metrics Scope)
                            |
          ---------------------------------------
          |                                     |
          v                                     v
   Worker Project 1                     Worker Project 2
   ----------------                     ----------------
   worker-1-server                      worker-2-server
   NGINX Web Server                     NGINX Web Server

            Centralized Monitoring & Dashboards
```

---

## Technologies and Services Used

* Google Cloud Monitoring
* Metrics Scope
* Monitoring Groups
* Uptime Checks
* Alerting Policies
* Custom Dashboards
* Compute Engine
* NGINX
* Apache Bench (ab)
* Cloud Logging
* Metrics Explorer

---

## Tasks Performed

### 1. Configured Resource Projects

Created Compute Engine VM instances in two separate projects:

* worker-1-server
* worker-2-server

Configuration:

| Parameter        | Value              |
| ---------------- | ------------------ |
| Machine Type     | e2-medium          |
| Region           | us-west1           |
| Zone             | us-west1-a         |
| Operating System | Debian 12          |
| Firewall         | Allow HTTP Traffic |

Installed and configured NGINX on both servers.

```bash
sudo apt-get update
sudo apt-get install -y nginx
```

Verified web server accessibility through public IP addresses.

---

### 2. Created a Metrics Scope

Configured a dedicated Monitoring Project to host the Metrics Scope.

Added:

* Worker Project 1
* Worker Project 2

Benefits:

* Centralized monitoring
* Cross-project observability
* Unified dashboards
* Simplified alerting

---

### 3. Configured Monitoring Groups

Added labels to VM instances.

#### Worker 1

| Label Key | Label Value |
| --------- | ----------- |
| component | frontend    |
| stage     | dev         |

#### Worker 2

| Label Key | Label Value |
| --------- | ----------- |
| component | frontend    |
| stage     | test        |

Created Monitoring Group:

```text
Frontend Servers
```

Criteria:

```text
component = frontend
```

Created Subgroup:

```text
Frontend Dev
```

Criteria:

```text
component = frontend
AND
stage = dev
```

---

### 4. Configured Uptime Checks

Created an HTTP uptime check for the Frontend Servers group.

Configuration:

| Setting       | Value            |
| ------------- | ---------------- |
| Protocol      | HTTP             |
| Resource Type | Instance         |
| Applies To    | Group            |
| Group         | Frontend Servers |
| Path          | /                |
| Frequency     | 1 Minute         |

Validated successful responses and monitored uptime metrics.

---

### 5. Investigated Monitoring Data

Explored:

* Metrics Explorer
* Logs Explorer
* Uptime Check Metrics
* Alerting Policies

Analyzed:

* Check Passed metrics
* Uptime latency
* Monitoring logs
* Alert generation behavior

---

### 6. Built a Custom Dashboard

Created custom dashboard:

```text
Developer's Frontend
```

Added widgets:

#### Dev Server Uptime

Metric:

```text
VM Instance → Uptime_check → check_passed
```

#### CPU Utilization

Metric:

```text
VM Instance → Instance → CPU Utilization
```

Filtered specifically for:

```text
worker-1-server
```

---

### 7. Performance Testing

Generated traffic using Apache Bench from worker-2-server.

Installed benchmarking tools:

```bash
sudo apt-get install apache2-utils
```

Executed load tests:

```bash
ab -s 120 -n 100000 -c 100 http://<worker-1-ip>/
```

```bash
ab -s 120 -n 500000 -c 500 http://<worker-1-ip>/
```

Observed CPU utilization spikes in Cloud Monitoring dashboards.

---

## Key Concepts Learned

### Metrics Scope

A Metrics Scope allows multiple Google Cloud projects to be monitored from a single monitoring project.

### Monitoring Groups

Logical collections of resources based on labels, regions, or other criteria.

### Uptime Checks

Automated health checks that verify service availability and response times from multiple global locations.

### Alerting

Automatically detects service failures and notifies administrators.

### Dashboards

Visual representations of infrastructure health, resource utilization, and application performance.

### Metrics Explorer

Used to analyze and visualize monitoring metrics.

---

## Skills Demonstrated

* Google Cloud Monitoring
* Cloud Observability
* Multi-Project Monitoring
* Metrics Scope Configuration
* Monitoring Groups
* Uptime Monitoring
* Alert Management
* Dashboard Creation
* Compute Engine Administration
* NGINX Deployment
* Infrastructure Monitoring
* Performance Testing
* Metrics Analysis
* Log Investigation

---

## Learning Outcomes

Through this lab, I learned how to centralize monitoring across multiple Google Cloud projects using Metrics Scopes, organize resources using Monitoring Groups, implement Uptime Checks and Alerting Policies, investigate monitoring data through logs and metrics, and build custom dashboards to visualize infrastructure health and performance trends.

The lab also provided hands-on experience with performance testing and observability practices commonly used by Site Reliability Engineering (SRE) and Cloud Operations teams.

---

## Outcome

Successfully implemented a centralized monitoring solution capable of monitoring resources across multiple Google Cloud projects. Built Monitoring Groups, Uptime Checks, Alerts, and Custom Dashboards while validating system behavior under load using Apache Bench.

This lab strengthened practical skills in Google Cloud Observability, Monitoring, and Site Reliability Engineering concepts.
