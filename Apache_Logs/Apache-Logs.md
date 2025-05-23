<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
    <h1>Part 1: Load and Analyze Apache Logs</h1>

   [apache_logs.txt](https://github.com/user-attachments/files/19326857/apache_logs.zip)

   <p>In this part, you will upload and analyze Apache web server logs that represent “regular” activity for VSI into your Splunk environment. To do so, complete the following steps:</p>


   <ol>
        <li>Return to the “Add Data” option within Splunk.</li>
        <li>Since you will upload the provided log file, select the “Upload” option.
            <ul>
                <li>Click “Select File.”</li>
                <li>Select the apache_logs.txt file.</li>
                <li>Click the green “Next” button in the top right.</li>
            </ul>
        </li>
        <li>You’ll be brought to the “Set Source Type” page.
            <ul>
                <li>You don’t need to change any configurations on this page.</li>
                <li>Select “Next” again.</li>
            </ul>
        </li>
        <li>You’ll be brought to the “Input Settings” page.
            <ul>
                <li>This page contains optional settings for how the data is input.</li>
                <li>In the “Host” field, Splunk uses a random value to name the machine or device that generated the logs.</li>
                <li>Update the value to “Apache_logs” and then select “Review.”</li>
            </ul>
        </li>
        <li>On the “Review” page, verify that you’ve chosen the correct settings, as the following image shows:
            <ul>
                
![image](https://github.com/user-attachments/assets/ba09e75b-0175-445d-85e6-b8cd0a8e4d8f)
    <li>Select “Submit” to proceed with uploading your data into Splunk.</li>
            </ul>
        </li>
        <li>Once the file has successfully uploaded, a message that says “File has been uploaded successfully” will appear on the screen.</li>
        <li>Select “Start Searching.”</li>
        <li>⚠️ Important: After the data populates on the search, select “All Time” for the time range.</li>
        <li>Briefly analyze the logs and the available fields, specifically examining the following important fields:
            <ul>
         <table border="1">
    <tr>
        <th>Field</th>
        <th>Value</th>
    </tr>
    <tr>
        <td><code>method</code></td>
        <td><img src="https://github.com/user-attachments/assets/43f13f60-1c84-4662-a525-3fd49db9ea75" width="700"></td>
    </tr>
    <tr>
    <td><code>referer_domain</code></td>
    <td><img src="(https://github.com/user-attachments/assets/5efc72c6-b13a-4dba-a50f-f0d05f0dd0c9" width="700"></td>
    </tr>
    <tr>
     <td><code>status</code></td>
     <td><img src="https://github.com/user-attachments/assets/fc313bf7-b56c-4488-9b9a-e91042326907" width="700"></td>
    </tr>  
    <tr>
    <td><code>clientip</code></td>
    <td><img src="https://github.com/user-attachments/assets/6c545a46-722f-4738-b455-418fc37c32dd" width="700"></td>
    </tr>
    <tr>
    <td><code>useragent</code></td>
    <td><img src="https://github.com/user-attachments/assets/7350d18f-89cb-4330-9e1a-926d47d2a972" width="700"></td>
    </tr>
   </table>
</ul>
        </li>
    </ol>

   <h1>Part 2: Create Reports, Alerts, and Dashboards for the Apache Logs</h1>

  <p>In this part, you will create reports, alerts, and dashboards to monitor for suspicious activity against VSI’s Apache web server. To do so, complete the following steps:</p>

   <ol>
        <li>Design the following deliverables to protect VSI from potential attacks by JobeCorp:
            <ul>
                <li><b>Reports:</b> Design the following reports to assist VSI in quickly identifying specific information:
                    <ul>
                        <li>A report that shows a table of the different HTTP methods (GET, POST, HEAD, etc.).
                            <ul>
                                <li>This will provide insight into the type of HTTP activity being requested against VSI’s web server.</li>
             <pre><code>source="</code>source="apache_logs.txt"  method="GET"</pre>

<table border="1">
    <tr>
        <td>GET</td>
        <td><img src="https://github.com/user-attachments/assets/7f7aff24-a43a-4b9a-8f4a-25b577a0d18a" width="700"></td>
    </tr>
       </table> 
    <br>
                                
 <pre><code>source="apache_logs.txt"  method="POST"</code></pre>                      
 <table border="1">
<tr>
        <td>POST</td>
        <td><img src="https://github.com/user-attachments/assets/46d29f23-fa08-4d75-834a-269b0ffc41b1" width="700"></td> 
    </tr>
     </table> 
    <br>
                                
 <pre><code>source="apache_logs.txt"  method="HEAD"</code></pre>                        
  <table border="1">    
<tr>
        <td>HEAD</td>
        <td><img src="https://github.com/user-attachments/assets/1f9ff09f-739b-49a5-b486-3c086c210ef7" width="700"></td>
    </tr>
             </table>         
</ul>
                        </li>
                        <li>A report that shows the top 10 domains that refer to VSI’s website.
                            <ul>
                                <li>This will assist VSI with identifying suspicious referrers.</li>
                                <pre><code>source="apache_logs.txt" referer=* | stats count by referer | sort - count | head 10</code></pre>
                                <br>
    
![image](https://github.com/user-attachments/assets/18e74f20-c967-44e2-977d-e526e4605d96)

 </ul>
                        </li>
                        <li>A report that shows the count of each HTTP response code.
                            <ul>
                                <li>This will provide insight into any suspicious levels of HTTP responses.</li>
            <pre><code>source="apache_logs.txt" | stats count by status</code></pre>
            <br>
                <img src="https://github.com/user-attachments/assets/581e27b4-9c2a-46e2-8ce0-5216340e18bb" width="700">

 </ul>
                        </li>
                    </ul>
                </li>
                <li><b>Alerts:</b> Design the following alerts:
                    <ul>
                        <li>Determine a baseline and threshold for hourly activity from any country besides the United States.
<pre><code>source="apache_logs.txt" referer=* | iplocation clientip| where Country!="United States" | bin _time span=1h | stats count by _time, Country</code></pre>
<br>
<img src="https://github.com/user-attachments/assets/f2211a9e-5006-45ee-a32a-abcbc0011465" width="700">

<ul>
                                <li>Create an alert that’s triggered when the threshold has been reached.</li>
                                <li>The alert should trigger an email to SOC@VSI-company.com.</li>
    </ul>
                        </li>
<table border="1">
    <tr>
        <td><img src="https://github.com/user-attachments/assets/66f9d6c3-8cce-4c1c-802f-323d4a6d5c4e" width="600"></td>
        <td><img src="https://github.com/user-attachments/assets/d1ba950c-10b6-441d-a0b4-adea830336d2" width="650"></td>
    </tr>
</table>
                        <li>Determine an appropriate baseline and threshold for the hourly count of the HTTP POST method.
<pre><code>source="apache_logs.txt"  method="post" | timechart span=1h count as post_method</code></pre>
<br>
<img src="https://github.com/user-attachments/assets/6e3805a1-180f-4364-bca0-1b3c81632503" width="700">
                            <ul>
                                <li>Create an alert that’s triggered when the threshold has been reached.</li>
                                <li>The alert should trigger an email to SOC@VSI-company.com.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
    <table border="1">
    <tr>
        <td><img src="https://github.com/user-attachments/assets/dabc302e-d82d-4bed-81b0-d7ce63e10f1a" width="600"></td>
        <td><img src="https://github.com/user-attachments/assets/cfe067f4-7b34-47d7-bda5-467ff52579a5" width="650"></td>
    </tr>
    </table>
                <li><b>Visualizations and Dashboards:</b> Design the following visualizations, and add them to a dashboard called “Apache Web Server Monitoring”:
                    <ul>
                        <li>A line chart that displays the different HTTP “methods” field values over time.</li>
         </ul>                
    <pre><code>source="apache_logs.txt" | timechart span=1h count by method</code></pre>                    
 <br>                 
 <table border="1">
    <tr>
        <td><img src="https://github.com/user-attachments/assets/4ff92095-1c84-4b55-9a24-0d6e4621b790" width="600"></td>
        <td><img src="https://github.com/user-attachments/assets/8bf1129a-9b8e-4a23-9d06-22d0a0922384" width="600"></td>
    </tr>
         </table>


  </li>
                        <li>A geographical map showing the location based on the “clientip” field.</li>
     <pre><code>source="apache_logs.txt" | iplocation clientip | geostats count by clientip</code></pre>              
<img src="https://github.com/user-attachments/assets/25247b40-1558-4c68-87b8-57e094af1f83" width="700">
<br>
<li>Any visualization of your choice that displays the number of different URIs.
      <pre><code>source="apache_logs.txt" | stats count by uri | sort - count</code></pre>               
    <table border="1">
    <tr>
        <td><img src="https://github.com/user-attachments/assets/d73ce288-e2cf-4975-8df2-0451465d30ee" width="600"></td>
        <td><img src="https://github.com/user-attachments/assets/15d16dc7-7cc6-407e-affb-34b4f2e0bdaa" width="600"></td>
    </tr>
 </table>

</li>
                        <li>Any visualization of your choice that displays the count of the top 10 countries that appear in the log.</li>
    <pre><code>source="apache_logs.txt" | iplocation clientip | search Country!="United States"|top Country</code></pre>
       <img src="https://github.com/user-attachments/assets/08503d97-9118-41f0-b89c-5ffc6c05f124" width="700">

<li>Any visualization that illustrates the count of different user agents.</li>
<pre><code>source="apache_logs.txt" | timechart span=1h count by useragent</code></pre>
<img src="https://github.com/user-attachments/assets/150f83bd-5b09-424e-b63a-0f5e4387c5ef" width="700">

<li>A single-value visualization of your choice that analyzes any single data point:</li>
<pre><code>source="apache_logs.txt" |search status=404 | stats count as "404 Count"</code></pre>
<img src="https://github.com/user-attachments/assets/cdc31830-28fc-4ab4-8a06-85e91bc22e4b" width="700">

 </ul>
                </li>
            </ul>
        </li>
        <li>On your dashboard, add the ability to change the time range for all visualizations.
            <ul>
                <br>
        <img src="https://github.com/user-attachments/assets/013d5336-52e3-4cb1-9c36-6dd84535e1f2" width="1000">
    </ul>
        </li>
    </ol>
</body>
</html>

