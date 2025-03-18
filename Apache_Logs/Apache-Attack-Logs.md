Part 3: Load Apache Attack Logs


In this part, you will upload Apache attack logs into your Splunk environment. To do so, complete the following steps:
Return to the “Add Data” option within Splunk.
Since you will upload the provided log file, select the “Upload” option.
Click “Select File.”
Select the apache_attack_logs.txt file 
Click the green “Next” button on the top right.
You will be brought to the “Set Source Type” page.
You don’t need to change any configurations on this page.
Select “Next” again.
You’ll be brought to a page called “Input Settings.”
This page contains optional settings for how the data is input.
In the “Host” field value, Splunk uses a random value to name the machine or device that generated the logs.
Update the value to “Apache_logs” and then select “Review.”
At the “Review” page, verify that you’ve chosen the correct settings.
Select “Submit” to proceed with uploading your data into Splunk.
Once the file has successfully uploaded, a message that says “File has been uploaded successfully” will appear.
Select “Start Searching.”
⚠️ Important: After the data populates on the search, select “All Time” for the time range.

Part 4: Analyze Apache Attack Logs


In this part, you will review the reports, alerts, and dashboards that you created on Day 1 and analyze the results. To do so, complete the following steps:


Report Analysis for Methods

Access the “Reports” tab, and select “Yours” to view the reports that you created on Day 1.
Select the report that analyzes the different HTTP methods.
Select “Edit” > “Open in Search.”
Take note of the percent and count of the various methods.
Change the source from source="apache_logs.txt" to source="apache_attack_logs.txt".
Select “Save.”
Review the updated results, and answer the following questions in the review document:
Did you detect any suspicious changes in HTTP methods? If so, which one?
What is that method used for?

Report Analysis for Referrer Domains

Access the “Reports” tab, and select “Yours” to view the reports that you created on Day 1.
Select the report that analyzes the different referrer domains.
Select “Edit” > “Open in Search.”
Take note of the different referrer domains.
Change the source from source="apache_logs.txt" to source="apache_attack_logs.txt".
Select “Save.”
Review the updated results, and answer the following question in the review document:
Did you detect any suspicious changes in referrer domains?


Report Analysis for HTTP Response Codes

Access the “Reports” tab, and select “Yours” to view the reports that you created on Day 1.
Select the report that analyzes the different HTTP response codes.
Select “Edit” > “Open in Search.”
Take note of the different HTTP response codes.
Change the source from source=apache_logs.txt to source="apache_attack_logs.txt.
Select “Save.”
Review the updated results, and answer the following question in the review document:
Did you detect any suspicious changes in HTTP response codes?
Now, you will review the alerts that you created on Day 1 and analyze the results.

Alert Analysis for International Activity

Access the “Alerts” tab, and select “Yours” to view the alerts that you created on Day 1.
Select the alert for suspicious volume of international activity.
Select “Open in Search.”
Change the source from source=apache_logs.txt to source="apache_attack_logs.txt.
Review the updated results, and answer the following questions in the review document:
Did you detect a suspicious volume of international activity?
If so, what was the count of events in the hour(s) it occurred?
Would your alert be triggered for this activity?
After reviewing, would you change the threshold you previously selected?

Alert Analysis for HTTP POST Activity

Access the “Alerts” tab, and select “Yours” to view the alerts that you created on Day 1.
Select the alert for suspicious volume of HTTP POST activity.
Select “Open in Search.”
Change the source from source="apache_logs.txt" to source="apache_attack_logs.txt".
Review the updated results, and answer the following questions in the review document:
Did you detect any suspicious volume of HTTP POST activity?
If so, what was the count of events in the hour(s) it occurred?
When did it occur?
After reviewing, would you change the threshold that you previously selected?
Now, you will set up a dashboard and analyze the results.


Dashboard Setup

Access the Apache Web Server Monitoring dashboard.
Select “Edit.”
For each panel that you created, access the panel and complete the following steps:
Select “Edit Search.”
Change the source from source="apache_logs.txt" to source="apache_attack_logs.txt".
Select “Apply.”
Save the whole dashboard.
Change the time on the whole dashboard to “All Time.”


Dashboard Analysis for Time Chart of HTTP Methods

Analyze your new dashboard results, and answer the following questions in the review document:
Does anything stand out as suspicious?
Which method seems to be used in the attack?
At what times did the attack start and stop?
What is the peak count of the top method during the attack?


Dashboard Analysis for Cluster Map

Analyze your new cluster map results, and answer the following questions in the review document:
Does anything stand out as suspicious?
Which new location (city, country) on the map has a high volume of activity?
Hint: Zoom in on the map.
What is the count of that city?

Dashboard Analysis for URI Data


Analyze your dashboard panel of the URI data, and answer the following questions in the review document:
Does anything stand out as suspicious?
What URI is hit the most?
Based on the URI being accessed, what could the attacker potentially be doing

