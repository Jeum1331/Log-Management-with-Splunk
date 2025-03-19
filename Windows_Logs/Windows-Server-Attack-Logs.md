<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
   
</head>
<body>
    <h1>Part 3: Load Windows Attack Logs</h1>

  <p>In this first part, you will upload Windows attack logs into your Splunk environment.</p>

  <h1>Part 4: Analyze Windows Attack Logs</h1>

  <p>In this part, you will review the reports, alerts, and dashboards that you created for [windows_server_logs.csv](https://github.com/user-attachments/files/19326877/windows_server_logs.zip) and analyze the results. To do so, complete the following steps:</p>
    <h2>Report Analysis for Severity</h2>
    <ol>
        <li>Access the “Reports” tab, and select “Yours” to view the reports that you created on your Windows Server Logs.</li>
        <li>Select the report that you created to analyze the different severities.</li>
        <li>Select “Open in Search.”</li>
        <li>Take note of the percentages of different severities.</li>
        <li>Change the source from windows_server_logs.csv to source="windows_server_attack_logs.csv".</li>
        <li>Select “Save.”</li>
        <li>Review the updated results, and answer the following question in the Project 3 Review Questions document:
            <ul>
                <li>Did you detect any suspicious changes in severity?</li>
            </ul>
        </li>
    </ol>

  <h2>Report Analysis for Failed Activities</h2>
    <ol>
        <li>Access the “Reports” tab, and select “Yours” to view the reports that you created for Windows Server Logs.</li>
        <li>Select the report that you created to analyze the different activities.</li>
        <li>Select “Open in Search.”</li>
        <li>Take note of the failed activities percentage.</li>
        <li>Change the source from windows_server_logs.csv to source="windows_server_attack_logs.csv".</li>
        <li>Select “Save.”</li>
        <li>Review the updated results, and answer the following question in the review document:
            <ul>
                <li>Did you detect any suspicious changes in failed activities?</li>
            </ul>
        </li>
    </ol>

   <h2>Alert Analysis for Failed Windows Activity</h2>
    <ol>
        <li>Access the “Alerts” tab, and select “Yours” to view the alerts that you created for Windows Logs.</li>
        <li>Select the alert for suspicious volume of failed activities.</li>
        <li>Select “Open in Search.”</li>
        <li>Change the source from windows_server_logs.csv to source="windows_server_attack_logs.csv".</li>
        <li>Review the updated results, and answer the following questions in the review document:
            <ul>
                <li>Did you detect a suspicious volume of failed activity?</li>
                <li>If so, what was the count of events in the hour(s) it occurred?</li>
                <li>When did it occur?</li>
                <li>Would your alert be triggered for this activity?</li>
                <li>After reviewing, would you change your threshold from what you previously selected?</li>
            </ul>
        </li>
   

