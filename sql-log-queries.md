🔍 SQL Lab: Querying Security Databases & Employee Logs
📝 Activity Description
In this lab, I applied SQL querying skills to investigate security-related data within an organization's employee and machine databases. The goal was to audit system access, identify potential security risks (such as unauthorized login attempts), and filter organizational records to ensure compliance with identity and access management (IAM) standards.

🛠️ Tools & Technologies Used
SQL (MariaDB/MySQL environment)

Relational Database Management Systems (RDBMS)

SQL Filters & Operators: WHERE, AND, OR, LIKE

Log Auditing & Security Analysis

💻 Step-by-Step Breakdown & Queries
Task 1: Filtering Failed Login Attempts
To check for potential brute-force attacks or unauthorized access attempts after hours, I queried the login logs database.

SELECT * FROM log_in_attempts WHERE login_time > '18:00:00' AND success = 0;

Purpose: This filter isolates failed login attempts occurring after standard business hours, helping identify anomalous user behavior or malicious scanning.

Task 2: Identifying Employees in Sensitive Departments
Auditing which users belong to specific departments helps verify that proper access controls are in place.

SELECT employee_id, first_name, last_name, department FROM employees WHERE department = 'Finance' OR department = 'Information Technology';

Purpose: Isolates employee rosters for high-risk departments to perform routine identity verification audits.

Task 3: Searching for Specific Machine Vulnerabilities
I investigated devices within the network running outdated or specifically flagged software versions.

SELECT device_id, operating_system, status FROM machines WHERE operating_system LIKE 'OS_X%';

Purpose: Uses wildcard filtering to quickly map out infrastructure assets running a specific operating system for patching or vulnerability management.

🎯 Summary & Security Impact
By leveraging SQL filtering, I demonstrated how a security analyst can efficiently parse through thousands of log records in seconds. This capability is critical for:

Incident Response: Speeding up the timeline to track when and where a failed login or malicious query originated.

Compliance Auditing: Ensuring that only authorized personnel appear in sensitive access groups.

Vulnerability Management: Instantly isolating systems that require immediate updates based on asset logs.
