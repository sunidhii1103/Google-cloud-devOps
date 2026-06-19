# Cloud Audit Logs

## Overview

This lab focused on exploring **Google Cloud Audit Logs**, a logging service that records administrative actions, data access events, system events, and policy-related activities across Google Cloud resources. Audit Logs help answer the critical question:

> **"Who did what, when, and where?"**

Through hands-on exercises, I learned how to enable Data Access audit logs, generate audit events, and investigate audit log entries using Google Cloud Logging.

---

## Objectives

* Enable Data Access Audit Logs for Cloud Storage.
* Generate administrative and data access activities.
* View and analyze Cloud Audit Logs.
* Understand the structure of audit log entries.
* Investigate user actions and resource access events.

---

## Technologies Used

* Google Cloud Logging
* Cloud Audit Logs
* Cloud Storage
* Logs Explorer
* IAM Policies
* Logging Query Language (LQL)

---

## Lab Tasks Completed

### 1. Enabled Data Access Audit Logs

* Configured Data Access logging for Cloud Storage.
* Enabled logging for data read and write operations.
* Explored audit logging configuration through IAM policies.

### 2. Generated Audit Events

Performed actions on Cloud Storage resources to generate audit log entries, including:

* Viewing bucket information
* Accessing stored data
* Administrative operations on storage resources

### 3. Viewed Activity Audit Logs

* Opened Logs Explorer.
* Filtered logs using:

```text
cloudaudit.googleapis.com/activity
```

* Investigated administrative actions performed on cloud resources.
* Examined audit log metadata and user activity.

### 4. Viewed Data Access Audit Logs

* Filtered logs using:

```text
cloudaudit.googleapis.com/data_access
```

* Observed:

  * Data read operations
  * Data write operations
  * Metadata access requests

### 5. Investigated Audit Log Entries

Analyzed important fields within audit log entries:

```text
protoPayload
 ├── authenticationInfo
 ├── methodName
 ├── resourceName
 ├── serviceName
 └── status
```

Used:

```text
protoPayload.authenticationInfo.principalEmail
```

to identify the user responsible for specific actions.

---

## Key Concepts Learned

### Cloud Audit Logs

Cloud Audit Logs maintain records of activities performed on Google Cloud resources and help answer:

> **Who performed an action, what action was performed, where it occurred, and when it happened.**

---

### Types of Audit Logs

#### Admin Activity Logs

Record administrative actions such as:

* Creating resources
* Updating configurations
* Deleting resources

**Enabled by default**

---

#### Data Access Logs

Record access to data and metadata.

Examples:

* Reading files
* Downloading objects
* Accessing bucket metadata

**Disabled by default for most services**

---

#### System Event Logs

Record actions performed by Google Cloud systems.

Examples:

* Automatic infrastructure changes
* Managed service operations

---

#### Policy Denied Logs

Record requests denied due to:

* IAM policies
* Organization policies

---

### Data Access Log Types

| Log Type   | Description                       |
| ---------- | --------------------------------- |
| ADMIN_READ | Reading metadata or configuration |
| DATA_READ  | Reading user data                 |
| DATA_WRITE | Writing or modifying user data    |

---

### Logs Explorer

Used to:

* Search logs
* Filter events
* Investigate user actions
* Troubleshoot resource activity

---

## Skills Gained

* Audit Log Analysis
* Cloud Logging
* Cloud Storage Auditing
* Security Monitoring
* User Activity Investigation
* Data Access Monitoring
* Log Filtering and Querying
* IAM and Audit Configuration

---

## Sample Log Filters

### Activity Logs

```text
logName="projects/PROJECT_ID/logs/cloudaudit.googleapis.com%2Factivity"
```

### Data Access Logs

```text
logName="projects/PROJECT_ID/logs/cloudaudit.googleapis.com%2Fdata_access"
```

### Cloud Storage Resources

```text
resource.type="gcs_bucket"
```

---

## Outcome

By completing this lab, I gained hands-on experience with **Google Cloud Audit Logs**, learned how to enable and analyze Data Access logs, generate audit events, investigate user actions through Logs Explorer, and use audit logging as a security, compliance, and troubleshooting tool within Google Cloud environments.
