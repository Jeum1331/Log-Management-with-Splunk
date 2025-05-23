# Part 1: Load and Analyze Windows Logs

[windows_server_logs.csv](https://github.com/user-attachments/files/19326877/windows_server_logs.zip)


In this first part, you will upload and analyze Windows security logs that represent "regular" activity for VSI into Splunk environment. To do so, ensure that you are logged in and complete the following steps:
<ol>
        <li>Select the “Add Data” option within Splunk.</li>
        <li>Since you will upload the provided log file, select the “Upload” option under “Or get data in with the following methods.”
            <ul>
                <li>Click “Select File.”</li>
                <li>Double-click the <code>windows_server_logs.csv</code> file.</li>
            </ul>
        </li>
        <li>You will be brought to the “Set Source Type” page.
            <ul>
                <li>You don’t need to change any configurations on this page.</li>
                <li>Select “Next” again.</li>
            </ul>
        </li>
        <li>You’ll be brought to the “Input Settings” page.
            <ul>
                <li>This page contains optional settings for how the data is input.</li>
                <li>In the “Host” field value, Splunk uses a random value to name the machine or device that generated the logs.</li>
                <li>Update the value to “Windows_server_logs” and then select “Review.”</li>
            </ul>
        </li>
        <li>On the “Review” page, verify that you’ve chosen the correct settings.
            <ul>
                <li>Select “Submit” to proceed with uploading your data into Splunk.</li>
            </ul>
        </li>
        <li>Once the file has successfully uploaded, a message saying “File has been uploaded successfully” will appear.</li>
        <li>Select “Start Searching.”</li>
        <li><span class="warning">⚠️ Important:</span> After the data populates on the search, select “All Time” for the time range.</li>
        <li>Briefly analyze the logs and the available fields, specifically examining the following important fields:</li>
        
 <table border="1">
    <tr>
        <th>Field</th>
        <th>Value</th>
    </tr>
    <tr>
        <td><code>signature_id</code></td>
        <td><img src="https://github.com/user-attachments/assets/e184d31b-b8cf-4082-a310-c81074c62001" alt="sigID" width="700"></td>
    </tr>
    <tr>
        <td><code>Signature</code></td>
        <td><img src="https://github.com/user-attachments/assets/4dbb9078-87c5-49e5-90b1-fba75f6c0d7d" alt="Signature" width="700"></td>
    </tr>
    <tr>
        <td><code>User</code></td>
        <td><img src="https://github.com/user-attachments/assets/523b150d-3155-47f8-bb5d-daa36ceb9d76" alt="User" width="700"</td>    
    <tr>
        <td><code>Status</code></td>
        <td><img src="https://github.com/user-attachments/assets/09848a41-aecc-4031-8014-b4ba8073ac65" alt="status image" width="700"></td>
    </tr>
    <tr>
        <td><code>severity</code></td>
        <td><img src="https://github.com/user-attachments/assets/c196c877-3ae4-4554-9df1-cad20d75eb68" alt="severity image" width="700"></td>
    </tr>
</table>


# Part 2: Create Reports, Alerts, and Dashboards for the Windows Logs
In this part, you will create reports, alerts, and dashboards to monitor for suspicious activity against VSI’s Windows server. Design the following deliverables to protect VSI from potential attacks by JobeCorp:
<h2>1. Reports</h2>
Design the following reports to assist VSI in quickly identifying specific information:</p>
    <ol>
        <li><strong>A report with a table of signatures and associated signature IDs:</strong>
            <ul>
                <li>This will allow VSI to view reports that show the ID number associated with the specific signature for Windows activity.</li>
                <li><span class="hint">Hint: Research how to remove the duplicate values in your SPL search.</span></li>
                <li>Take a screenshot of the report.</li>
            </ul>
<pre><code>source="windows_server_logs.csv" host="Windows_Server_Logs" | dedup signature_id | table signature_id, signature | sort signature_id</code></pre>
<br>
<img src="https://github.com/user-attachments/assets/7d43017c-2412-47ab-8c9e-f72d92d41c05" width="700">
                
</li>
        <li><strong>A report that displays the severity levels, and the count and percentage of each:</strong>
            <ul>
                <li>This will allow VSI to quickly understand the severity levels of the Windows logs being viewed.</li>
        <pre><code>source="windows_server_logs.csv" host="Windows_Server_Logs" | top severity</code></pre>
        <br>
        <img src="https://github.com/user-attachments/assets/6b6a8baa-c00c-4df5-abd0-6f746f1b2d38" width="700">
            </ul>
 </li>
        <li><strong>A report that provides a comparison between the success and failure of Windows activities:</strong>
            <ul>
                <li>This will show VSI if there is a suspicious level of failed activities on their server.</li>
                <li><span class="hint">Hint: Check the “status” field for this information.</span></li>
            </ul>
        <pre><code>source="windows_server_logs.csv" host="Windows_Server_Logs" | top status</code></pre>
        <br>
<img src="https://github.com/user-attachments/assets/4b94a49a-7caa-4a5d-9de7-e44ed46be987" alt="tatus" width="700">

 </li>
    </ol>

 <h2>2. Alerts</h2>
    <p>Design the following alerts to notify VSI of suspicious activity, and keep this information on hand as you will include it in your presentation:</p>
    <ol>
        <li><strong>Determine a baseline and threshold for the hourly level of failed Windows activity:</strong>
        <pre><code>source="windows_server_logs.csv" host="Windows_Server_Logs" status="failure" | timechart span=1h count as failed_attempts</code></pre>
        <br>
        <img src="https://github.com/user-attachments/assets/6bb3a333-cf09-49fb-a859-c770fa3ce18b" width="700">
        <br>
        After determining the baseline and threshold this is the query used for the alert:  
 <pre><code>source="windows_server_logs.csv" host="Windows_Server_Logs" status="failure" | timechart span=1h count as failed_attempts | where failed_attempts > 12</code></pre>
<ul>
                <li>Create an alert that’s triggered when the threshold has been reached.</li>
                <li>The alert should trigger an email to <code>SOC@VSI-company.com</code>.</li>
 <table border="1">
         <tr>
                <td><img src="https://github.com/user-attachments/assets/58465e43-aae6-4c62-867c-1c062ec76bf4" width="650"></td>
                <td><img src="https://github.com/user-attachments/assets/b771d3cb-4967-4419-bfaa-825412e418a8" width="600"></td>
            </tr>
 </table>

</ul>
        </li>
        <li><strong>Determine a baseline and threshold for the hourly count of the signature “an account was successfully logged on.”</strong>
        <pre><code>host=Windows_Server_Logs source="windows_server_logs.csv" signature_id="4624"| timechart span=1h count as successful_logins</code></pre>
        <br>
        <img src="https://github.com/user-attachments/assets/dd71966d-0e07-48c3-8456-31c54579ac78" width="700"
">
            <ul>
                <li>Create an alert that’s triggered when the threshold has been reached.</li>
                <li>The alert should trigger an email to <code>SOC@VSI-company.com</code>.</li>
                <li>Design the alert based on the corresponding signature ID, as the signature name sometimes changes when the Windows system updates.</li>
         <table border="1">
         <tr>
         <td><img src="https://github.com/user-attachments/assets/b75ffe46-de80-49ab-ba42-9d43f43a1d11" width="650"></td>
         <td><img src="https://github.com/user-attachments/assets/68338ff0-a168-4ed2-a010-ee6d973cb483" width="600"></td>
</tr>
 </table>

</ul>
        </li>
        <li><strong>Determine a baseline and threshold for the hourly count of the signature “a user account was deleted.”</strong>
        <pre><code>host="Windows_Server_Logs" source="windows_server_logs.csv" signature_id="4726" | timechart span=1h count as deleted_accouts</code></pre>
        <br>
        <img src="https://github.com/user-attachments/assets/6790c574-951c-4de3-b506-fab5574b0d87" width="700">
            <ul>
                <li>Design the alert based on the corresponding signature ID, as the signature name sometimes changes when the Windows system updates.</li>
                <li>Create an alert that's triggered when the threshold has been reached.</li>
                <li>The alert should trigger an email to <code>SOC@VSI-company.com</code>.</li>
<table border="1">
         <tr>
                <td><img src="https://github.com/user-attachments/assets/55617aa1-0b67-40b5-82e8-151d9bc11f4f" width="650"></td>
                <td><img src="https://github.com/user-attachments/assets/32cf597b-8838-4eb9-9afb-dfcd5af1165c" width="600"></td>
</tr>
 </table>

</ul>
        </li>
    </ol>

<h2>3. Visualizations and Dashboards</h2>
    <p>Design the following visualizations, and add them to a dashboard called “Windows Server Monitoring”:</p>
    <ol>
        <li><strong>A line chart that displays the different “signature” field values over time:</strong>
            <ul>
<pre><code>host="Windows_Server_Logs" source="windows_server_logs.csv" | timechart span=1hr count by signature</code></pre>
          <br>
<img src="https://github.com/user-attachments/assets/979623b4-d90d-4346-8ac4-9512a5d2f77b" width="700">                    
   
</ul>
        </li>
        <li><strong>A line chart that displays the different “user” field values over time:</strong>
            <ul>
<pre><code>host="Windows_Server_Logs" source="windows_server_logs.csv" | timechart span=1hr count by user</code></pre>
<br>
<img src="https://github.com/user-attachments/assets/3f08afda-a3bf-4b70-8df1-248e749426d2" width="700">                    
</ul>
        </li>
        <li><strong>Any visualization that illustrates the count of different signatures:</strong>
            <ul>
              <pre><code>host="Windows_Server_Logs" source="windows_server_logs.csv" | stats count by signature | sort -count</code></pre>
              <br>
        <img src="https://github.com/user-attachments/assets/e12f68e1-b834-4a6f-b9ba-cfcce1face63" width="700">
            </ul>
        </li>
        <li><strong>Any visualization that illustrates the count of different users:</strong>
            <ul>
        <pre>code>host="Windows_Server_Logs" source="windows_server_logs.csv" | stats count by user | sort - count</code></pre>
        <br>
 <table border="1">
         <tr>
                <td><img src="https://github.com/user-attachments/assets/a42bffd3-f4a5-46bb-b685-a5578e2f152e" width="650"></td>
                <td><img src="https://github.com/user-attachments/assets/9cf029c6-99ef-4bf3-9656-c157f51ab13f" width="650"></td>
        </tr>
 </table>
 </ul>
     

<h2>4. Dashboard Setup</h2>
    <p>On your dashboard, add the ability to change the time range for all visualizations:</p>
    <ul>

![image](https://github.com/user-attachments/assets/d5400895-ad3f-4a1d-a0bd-5d446edda6ac)

</ul>
