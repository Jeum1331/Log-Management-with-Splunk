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
       <li>Review the updated results, and answer the following questions in the review document:
            <img src="https://github.com/user-attachments/assets/2a13e511-fe1a-48d4-951b-d9c696a9eff8" width="700">
            <ul>
                <li>Did you detect any suspicious changes in HTTP methods?</li>
    <p>Yes, there is a spike in the <code>POST</code> method reaching a peak of 1296 requests in the time span.</p>

 <li>What is that method used for?</li>
 <p>The <code>POST</code> method is used in HTTP requests to send data to a server to create or update a resource. It is commonly used in web applications for submitting forms, uploading files, and sending data to an API.</p>
    <p>In cybersecurity, attackers can exploit the <code>POST</code> method in various ways to manipulate or exploit web applications. Some common attack vectors include:</p>
    <ul>
        <li>SQL Injection (SQLi)</li>
        <li>Cross-Site Scripting (XSS)</li>
        <li>API Abuse & Enumeration</li>
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
        <img src="https://github.com/user-attachments/assets/0bd9611c-09d3-485a-90b6-01c71b0da90a" width="700">
            <ul>
                <li>Did you detect any suspicious changes in referrer domains?</li>
                <p>Yes, the count of the referring domains significantly decreased in the day of the attack.</p>
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
            <img src="https://github.com/user-attachments/assets/e2657e75-12d9-4336-968c-0315208a642f" width="700">
            <ul>
                <li>Did you detect any suspicious changes in HTTP response codes?</li>
                <p>Yes, I detected changes in HTTP code:</p>
                  <ul>
                   <li>-200(OK): The day of the attack it decreased the count.</li>
                   <li>-404(not found): tThe day of the attack it increased.</li>
            </ul>
        </li>
    </ol>

  <h2>Now, you will review the alerts that you created for the <code>Apache_logs.txt</code> and analyze the results.</h2>

  <h3>Alert Analysis for International Activity</h3>
    <ol>
        <li>Access the “Alerts” tab, and select “Yours” to view the alerts that you created for Apache Logs.</li>
        <li>Select the alert for suspicious volume of international activity.</li>
        <li>Select “Open in Search.”</li>
        <li>Change the source from source=apache_logs.txt to source="apache_attack_logs.txt".</li>
        <li>Review the updated results, and answer the following questions in the review document:
            <img src="https://github.com/user-attachments/assets/98818e58-d565-4d6c-a8df-9056119983af" width="700">
            <ul>
                <li>Did you detect a suspicious volume of international activity?</li>
               <p>Yes, I was able to detect suspicious volume.</p>
                <li>If so, what was the count of events in the hour(s) it occurred?</li>
                <p>It happened at 15:00 with a count of 864.</p>
                <li>Would your alert be triggered for this activity?</li>
                <p>Yes it would have since the threshold was set to 70.</p>
                <li>After reviewing, would you change the threshold you previously selected?</li>
                <p>I would increase it a bit to avoid false positives.</p>
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
            <img src="https://github.com/user-attachments/assets/b5b39e82-7a5f-4c39-b851-3f59131be58e" width="700">
            <ul>
                <li>Did you detect any suspicious volume of HTTP POST activity?</li>
                <p>Yes.</p>
                <li>If so, what was the count of events in the hour(s) it occurred?</li>
                <p>It reached a peak of 1296.</p>
                <li>When did it occur?</li>
                <p>Wednesday, March 25th, 2020 at 20:00.</p>
                <li>After reviewing, would you change the threshold that you previously selected?</li>
                <p>Yes, it would've since the threshold was set to 10.</p>
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
        <img src="https://github.com/user-attachments/assets/cced04ce-f92e-4968-badd-517f1b4aa101" width="700">
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

