Part 1: Load and Analyze Apache Logs
In this part, you will upload and analyze Apache web server logs that represent “regular” activity for VSI into your Splunk environment. To do so, complete the following steps:
Return to the “Add Data” option within Splunk.
Since you will upload the provided log file, select the “Upload” option.
Click “Select File.”
Select the apache_logs.txt file.
Click the green “Next” button in the top right.
You’ll be brought to the “Set Source Type” page.
You don’t need to change any configurations on this page.
Select “Next” again.
You’ll be brought to the “Input Settings” page.
This page contains optional settings for how the data is input.
In the “Host” field, Splunk uses a random value to name the machine or device that generated the logs.
Update the value to “Apache_logs” and then select “Review.”
On the “Review” page, verify that you’ve chosen the correct settings, as the following image shows:

Select “Submit” to proceed with uploading your data into Splunk.
Once the file has successfully uploaded, a message that says “File has been uploaded successfully” will appear on the screen.
Select “Start Searching.”
⚠️ Important: After the data populates on the search, select “All Time” for the time range.
Briefly analyze the logs and the available fields, specifically examining the following important fields:
method
referer_domain
status
clientip
useragent

Part 2: Create Reports, Alerts, and Dashboards for the Apache Logs
In this part, you will create reports, alerts, and dashboards to monitor for suspicious activity against VSI’s Apache web server. To do so, complete the following steps:
Design the following deliverables to protect VSI from potential attacks by JobeCorp:
Reports: Design the following reports to assist VSI in quickly identifying specific information (make sure to grab screenshots of each report):
A report that shows a table of the different HTTP methods (GET, POST, HEAD, etc.).
This will provide insight into the type of HTTP activity being requested against VSI’s web server.
A report that shows the top 10 domains that refer to VSI’s website.
This will assist VSI with identifying suspicious referrers.
A report that shows the count of each HTTP response code.
This will provide insight into any suspicious levels of HTTP responses.
Alerts: Design the following alerts:
Determine a baseline and threshold for hourly activity from any country besides the United States.
Create an alert that’s triggered when the threshold has been reached.
The alert should trigger an email to SOC@VSI-company.com.
Determine an appropriate baseline and threshold for the hourly count of the HTTP POST method.
Create an alert that’s triggered when the threshold has been reached.
The alert should trigger an email to SOC@VSI-company.com.
Visualizations and dashboards: Design the following visualizations, and add them to a dashboard called “Apache Web Server Monitoring” (be creative with your visualizations, and make sure to grab screenshots of each):
A line chart that displays the different HTTP “methods” field values over time.
Hint: Add the following after your search: timechart span=1h count by method.
A geographical map showing the location based on the “clientip” field.
Any visualization of your choice that displays the number of different URIs.
Hint: You can add brand-new custom visualizations by accessing this page inside your VM: Additional Viz.
Any visualization of your choice that displays the count of the top 10 countries that appear in the log.
Any visualization that illustrates the count of different user agents.
A single-value visualization of your choice that analyzes any single data point: e.g., radial gauge, marker gauge, or a custom visualization from http://localhost:8000/en-US/manager/search/appsremote?content=visualizations&type=app).
On your dashboard, add the ability to change the time range for all visualizations.
Be sure to title all of your panels appropriately.
Organize the panels on your dashboard as you see fit.
