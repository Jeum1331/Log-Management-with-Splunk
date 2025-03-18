# Part 1: Load and Analyze Windows Logs
Windows Server Log Analysis in Splunk
In this first part, you will upload and analyze Windows security logs that represent "regular" activity for VSI into your Splunk environment. To do so, complete the following steps:
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
        <li>Briefly analyze the logs and the available fields, specifically examining the following important fields:
            <ul>
                <li><code>signature_id</code></li>
                <li><code>signature</code></li>
                <li><code>user</code></li>
                <li><code>status</code></li>
                <li><code>severity</code></li>
            </ul>
        </li>
    </ol>
