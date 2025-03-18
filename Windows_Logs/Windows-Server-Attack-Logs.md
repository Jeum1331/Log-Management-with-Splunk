Part 1: Load Windows Attack Logs

In this first part, you will upload Windows attack logs into your Splunk environment. To do so, complete the following steps:
Select the “Add Data” option within Splunk.
Since you will upload the provided log file, select the “Upload” option.
Click “Select File.”
Select the windows_server_attack_logs.csv file located in the /splunk/logs/Week-2-Day-3-Logs/ directory.
Click the green “Next” button on the top right.
You will be brought to the “Set Source Type” page.
You don’t need to change any configurations on this page.
Select “Next” again.
You’ll be brought to the “Input Settings” page.
This page contains optional settings for how the data is input.
In the “Host” field value, Splunk uses a random value to name the machine or device that generated the logs.
Update the value to “Windows_server_logs” and then select “Review.”
On the “Review” page, verify that you’ve chosen the correct settings.
Select “Submit” to proceed with uploading your data into Splunk.
Once the file has successfully uploaded, a message that says “File has been uploaded successfully” will appear.
Select “Start Searching.”
⚠️ Important: After the data populates on the search, select “All Time” for the time range.

Part 2: Analyze Windows Attack Logs


In this part, you will review the reports, alerts, and dashboards that you created on Day 1 and analyze the results. To do so, complete the following steps:
Report Analysis for Severity

Access the “Reports” tab, and select “Yours” to view the reports that you created on Day 1.
Select the report that you created to analyze the different severities.
Select “Open in Search.”
Take note of the percentages of different severities.
Change the source from windows_server_logs.csv to source="windows_server_attack_logs.csv".
Select “Save.”
Review the updated results, and answer the following question in the Project 3 Review Questions document:
Did you detect any suspicious changes in severity?
Note: You will use this same document for the remaining review questions.



Report Analysis for Failed Activities

Access the “Reports” tab, and select “Yours” to view the reports that you created on Day 1.
Select the report that you created to analyze the different activities.
Select “Open in Search.”
Take note of the failed activities percentage.
Change the source from windows_server_logs.csv to source="windows_server_attack_logs.csv".
Select “Save.”
Review the updated results, and answer the following question in the review document:
Did you detect any suspicious changes in failed activities?
Now, you will review the alerts that you created on Day 1 and analyze the results.

Alert Analysis for Failed Windows Activity

Access the “Alerts” tab, and select “Yours” to view the alerts that you created on Day 1.
Select the alert for suspicious volume of failed activities.
Select “Open in Search.”
Change the source from windows_server_logs.csv to source="windows_server_attack_logs.csv".
Review the updated results, and answer the following questions in the review document (note that your alerts will not trigger; this is a theoretical exercise):
Did you detect a suspicious volume of failed activity?
If so, what was the count of events in the hour(s) it occurred?
When did it occur?
Would your alert be triggered for this activity?
After reviewing, would you change your threshold from what you previously selected?

Alert Analysis for Successful Logins

Access the “Alerts” tab, and select “Yours” to view the alerts that you created on Day 1.
Select the alert for suspicious volume of successful logins.
Select “Open in Search.”
Change the source from windows_server_logs.csv to source="windows_server_attack_logs.csv".
Review the updated results, and answer the following questions in the review document:
Did you detect a suspicious volume of successful logins?
If so, what was the count of events in the hour(s) it occurred?
Who is the primary user logging in?
When did it occur?
Would your alert be triggered for this activity?
After reviewing, would you change your threshold from what you previously selected?

Alert Analysis for Deleted Accounts

Access the “Alerts” tab, and select “Yours” to view the alerts that you created on Day 1.
Select the alert for suspicious volume of deleted accounts.
Select “Open in Search.”
Change the source from windows_server_logs.csv to source="windows_server_attack_logs.csv".
Review the updated results, and answer the following question in the review document:
Did you detect a suspicious volume of deleted accounts?
Next, you will view your dashboard and analyze the results.

Dashboard Setup

Access the Windows Web Server Monitoring dashboard.
Select “Edit.”
For each panel that you created, access the panel and complete the following steps:
Select “Edit Search.”
Change the source from windows_server_logs.csv to source="windows_server_attack_logs.csv".
Select “Apply.”
Save the dashboard.
Change the time on the whole dashboard to “All Time.”

Dashboard Analysis for Time Chart of Signatures

Analyze your new dashboard results, and answer the following questions in the review document:
Does anything stand out as suspicious?
What signatures stand out?
What time did each signature’s suspicious activity begin and stop?
What is the peak count of the different signatures?

Dashboard Analysis for Users


Analyze your new dashboard results, and answer the following questions in the review document:
Does anything stand out as suspicious?
Which users stand out?
What time did each user’s suspicious activity begin and stop?
What is the peak count of the different users?

Dashboard Analysis for Signatures with Bar, Graph, and Pie Charts

Analyze your new dashboard results, and answer the following questions in the review document:
Does anything stand out as suspicious?
Do the results match your findings from the time chart for signatures?

Dashboard Analysis for Users with Bar, Graph, and Pie Charts


Analyze your new dashboard results, and answer the following questions in the review document:
Does anything stand out as suspicious?
Do the results match your findings from the time chart for users?

Dashboard Analysis for Users with Statistical Charts


Analyze your new dashboard results, and answer the following question in the review document:
What are the advantages and disadvantages of using this report, compared to the other user panels that you created?
