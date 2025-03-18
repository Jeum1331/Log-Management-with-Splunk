## Download Log Files
<ul>
  <li><a href="https://github.com/user-attachments/files/19321507/apache_logs.zip">apache_logs</a></li>
  <li><a href="https://github.com/user-attachments/files/19321540/apache_attack_logs.zip">apache_attack_logs</a></li>
  <li><a href="https://github.com/user-attachments/files/19321542/windows_server_logs.zip">windows_server_logs</a></li>
</ul>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Log Files README</title>
</head>
<body>
    <h1>README - Log Files for Splunk Management</h1>

    <p>Welcome to the log files provided for use in Splunk analysis. Below are the details for each dataset:</p>

    <h2>1. Windows Server Logs</h2>
    <p>This dataset contains logs from a Windows Server that houses the intellectual property for VSI's next-generation virtual-reality programs. The logs include crucial information for monitoring and securing this critical infrastructure.</p>
    <p>Usage: These logs should be analyzed for any potential security incidents, system events, or performance issues that could affect the intellectual property hosted on this server.</p>

    <h2>2. Apache Server Logs</h2>
    <p>This dataset contains logs from the Apache server running VSI's main public-facing website, <a href="https://vsi-company.com">vsi-company.com</a>. These logs track HTTP requests, errors, and other web traffic related to the site.</p>
    <p>Usage: The Apache logs are ideal for analyzing web traffic patterns, identifying potential security vulnerabilities (e.g., DDoS attacks or SQL injection attempts), and understanding how users are interacting with the public website.</p>

    <h2>3. Links to Documentation and Datasets</h2>
    <p>For detailed documentation and more information on these datasets, please visit the following links:</p>
    <ul>
        <li><a href="https://splunkbase.splunk.com/">Splunkbase</a></li>
        <li><a href="https://docs.splunk.com/Documentation">Splunk Documentation</a></li>
        <li><a href="https://docs.splunk.com/Documentation/AddOns/released/Overview/AboutSplunkAdd-ons">About Splunk Add-ons</a></li>
    </ul>

    <h2>Usage Instructions</h2>
    <p>To analyze these logs using Splunk, follow the instructions provided in the <a href="https://github.com/Jeum1331/Log-Management-with-Splunk/blob/main/Datasets.md">Log Management with Splunk</a> guide. You will find detailed instructions on how to ingest, search, and analyze these logs to gain insights into system performance, security, and usage patterns.</p>

    <h2>Important Notes</h2>
    <ul>
        <li>The Windows Server Logs contain sensitive data about VSI’s intellectual property. Please ensure this dataset is handled securely and only accessible to authorized personnel.</li>
        <li>The Apache Server Logs are publicly accessible data but may still contain personal data depending on the site's traffic. Use caution when analyzing this data to avoid privacy violations.</li>
    </ul>
</body>
</html>
