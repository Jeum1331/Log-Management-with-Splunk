# Part 3: Load Apache Attack Logs

[apache_attack_logs.zip](https://github.com/user-attachments/files/19326889/apache_attack_logs.zip)


In this part, you will upload Apache attack logs into your Splunk environment. 

<body>
    <h1>Part 4: Analyze Apache Attack Logs</h1>

   <p>In this part, you will review the reports, alerts, and dashboards that you created for the Apache logs, compare and analyze the results. To do so, complete the following steps:</p>

  <h2>Report Analysis for Methods</h2>
    <ol>
        <li>Access the “Reports” tab, and select “Yours” to view the reports that you created for Apache Logs.</li>
        <li>Select the report that analyzes the different HTTP methods.</li>
        <li>Select “Edit” > “Open in Search.”</li>
        <li>Take note of the percent and count of the various methods.</li>
        <li>Change the source from source="apache_logs.txt" to source="apache_attack_logs.txt".</li>
        <li>Select “Save.”</li>
        <img src="https://github.com/user-attachments/assets/2a13e511-fe1a-48d4-951b-d9c696a9eff8" width="700">
 <li>Review the updated results, and answer the following questions in the review document:
            <ul>
                <li>Did you detect any suspicious changes in HTTP methods? If so, which one?</li>
                <li>What is that method used for?</li>
            </ul>
        </li>
    </ol>

  <h2>Report Analysis for Referrer Domains</h2>
    <ol>
        <li>Access the “Reports” tab, and select “Yours” to view the reports that you created for Apache Logs.</li>
        <li>Select the report that analyzes the different referrer domains.</li>
        <li>Select “Edit” > “Open in Search.”</li>
        <li>Take note of the different referrer domains.</li>
        <li>Change the source from source="apache_logs.txt" to source="apache_attack_logs.txt".</li>
        <li>Select “Save.”</li>
        <li>Review the updated results, and answer the following question in the review document:
            <ul>
                <li>Did you detect any suspicious changes in referrer domains?</li>
            </ul>
        </li>
    </ol>

  <h2>Report Analysis for HTTP Response Codes</h2>
    <ol>
        <li>Access the “Reports” tab, and select “Yours” to view the reports that you created for Apache Logs.</li>
        <li>Select the report that analyzes the different HTTP response codes.</li>
        <li>Select “Edit” > “Open in Search.”</li>
        <li>Take note of the different HTTP response codes.</li>
        <li>Change the source from source=apache_logs.txt to source="apache_attack_logs.txt".</li>
        <li>Select “Save.”</li>
        <li>Review the updated results, and answer the following question in the review document:
            <ul>
                <li>Did you detect any suspicious changes in HTTP response codes?</li>
            </ul>
        </li>
    </ol>

  <h2>Now, you will review the alerts that you created on Day 1 and analyze the results.</h2>

  <h3>Alert Analysis for International Activity</h3>
    <ol>
        <li>Access the “Alerts” tab, and select “Yours” to view the alerts that you created for Apache Logs.</li>
        <li>Select the alert for suspicious volume of international activity.</li>
        <li>Select “Open in Search.”</li>
        <li>Change the source from source=apache_logs.txt to source="apache_attack_logs.txt".</li>
        <li>Review the updated results, and answer the following questions in the review document:
            <ul>
                <li>Did you detect a suspicious volume of international activity?</li>
                <li>If so, what was the count of events in the hour(s) it occurred?</li>
                <li>Would your alert be triggered for this activity?</li>
                <li>After reviewing, would you change the threshold you previously selected?</li>
            </ul>
        </li>
    </ol>

   <h3>Alert Analysis for HTTP POST Activity</h3>
    <ol>
        <li>Access the “Alerts” tab, and select “Yours” to view the alerts that you created for Apache Logs.</li>
        <li>Select the alert for suspicious volume of HTTP POST activity.</li>
        <li>Select “Open in Search.”</li>
        <li>Change the source from source="apache_logs.txt" to source="apache_attack_logs.txt".</li>
        <li>Review the updated results, and answer the following questions in the review document:
            <ul>
                <li>Did you detect any suspicious volume of HTTP POST activity?</li>
                <li>If so, what was the count of events in the hour(s) it occurred?</li>
                <li>When did it occur?</li>
                <li>After reviewing, would you change the threshold that you previously selected?</li>
            </ul>
        </li>
    </ol>

  <h2>Now, you will set up a dashboard and analyze the results.</h2>

  <h3>Dashboard Setup</h3>
    <ol>
        <li>Access the Apache Web Server Monitoring dashboard.</li>
        <li>Select “Edit.”</li>
        <li>For each panel that you created, access the panel and complete the following steps:
            <ul>
                <li>Select “Edit Search.”</li>
                <li>Change the source from source="apache_logs.txt" to source="apache_attack_logs.txt".</li>
                <li>Select “Apply.”</li>
            </ul>
        </li>
        <li>Save the whole dashboard.</li>
        <li>Change the time on the whole dashboard to “All Time.”</li>
    </ol>

   <h3>Dashboard Analysis for Time Chart of HTTP Methods</h3>
    <p>Analyze your new dashboard results, and answer the following questions in the review document:</p>
    <ul>
        <li>Does anything stand out as suspicious?</li>
        <li>Which method seems to be used in the attack?</li>
        <li>At what times did the attack start and stop?</li>
        <li>What is the peak count of the top method during the attack?</li>
    </ul>

  <h3>Dashboard Analysis for Cluster Map</h3>
    <p>Analyze your new cluster map results, and answer the following questions in the review document:</p>
    <ul>
        <li>Does anything stand out as suspicious?</li>
        <li>Which new location (city, country) on the map has a high volume of activity?
            <ul>
                <li>Hint: Zoom in on the map.</li>
            </ul>
        </li>
        <li>What is the count of that city?</li>
    </ul>

  <h3>Dashboard Analysis for URI Data</h3>
    <p>Analyze your dashboard panel of the URI data, and answer the following questions in the review document:</p>
    <ul>
        <li>Does anything stand out as suspicious?</li>
        <li>What URI is hit the most?</li>
        <li>Based on the URI being accessed, what could the attacker potentially be doing?</li>
    </ul>

</body>
</html>

