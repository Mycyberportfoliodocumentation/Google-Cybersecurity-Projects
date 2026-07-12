🐧 Linux Lab: Automating Data Streams & I/O Redirection
📝 Activity Description
In this lab, I explored the mechanics of Linux input/output (I/O) streams, data pipe automation, and command-line text manipulation. I practiced managing standard input (stdin), standard output (stdout), and standard error (stderr) to filter log data, redirect command outputs to files, and efficiently string multiple utilities together using piping.

🛠️ Tools & Technologies Used
Linux CLI (Ubuntu/Debian-based environment)

I/O Redirection Operators: >, >>, 2>

Piping & Filters: | (pipe), grep, head, wc

Text Streams: stdin (0), stdout (1), stderr (2)

💻 Step-by-Step Breakdown & Commands
Task 1: Redirecting Output to a File
Instead of printing command outputs to the terminal screen, I saved tool outputs directly to tracking logs.

echo "System Audit Initiated" > audit_log.txt
echo "Running Vulnerability Scan..." >> audit_log.txt

Purpose: The > operator creates or completely overwrites a file with new data, while the >> operator appends data safely to the end of an existing file without wiping it.

Task 2: Capturing and Isolating Error Logs
To debug a failing utility or capture unauthorized access alerts, I redirected standard error (stderr) independently from regular outputs.

ls /root 2> error_log.txt

Purpose: Directs any permission denied messages or standard errors (2>) away from the screen and into a dedicated log file for automated troubleshooting.

Task 3: Piping and Filtering Live Data Streams
I used the pipeline operator to pass the live text output of one command directly as the input for another command to filter specific indicators of compromise.

cat /var/log/auth.log | grep "Failed password" | head -n 5

Purpose: Reads an entire authorization log, pipes it to grep to isolate only failed authentication attempts, and pipes those matches to head to display just the 5 most recent occurrences.

🎯 Summary & Security Impact
Mastering streams and automation via the Linux shell allows a security professional to handle massive amounts of unstructured data rapidly. This activity highlighted:

Log Management: Automatically piping or appending security telemetry out into persistent log directories.

Efficient Triage: Using pipelines (|) and filters like grep to quickly strip out noisy data and find critical alerts without needing to open enormous log files manually.
