<!DOCTYPE html>
<html>
<head>
    <title>Comparison Report: Apache Logs vs. Apache Attack Logs</title>
</head>
<body>
    <h1>Comparison Report: Apache Logs vs. Apache Attack Logs</h1>
    
  <h2>1. HTTP Method Analysis</h2>
    <h3>Suspicious Changes in HTTP Methods</h3>
    <p>During the attack, there was a noticeable increase in <strong>POST</strong> method requests, while <strong>GET</strong> method requests decreased. This is indicative of an attack leveraging the POST method for malicious activities.</p>
    
  <pre>
    source="apache_logs.txt" referrer=* | stats count by method
    source="apache_attack_logs.txt" referrer=* | stats count by method
    </pre>
    
   <h3>Method Usage Comparison</h3>
    <ul>
        <li><strong>POST Method</strong>: Used to send data to the server, often to update or create resources. Attackers exploit this for SQL Injection, Cross-Site Scripting (XSS), and API abuse.</li>
        <li><strong>GET Method</strong>: Typically used to request data without modifying server resources.</li>
    </ul>
    
   <h2>2. Referrer Domain Analysis</h2>
    <h3>Suspicious Changes in Referrer Domains</h3>
    <p>The count of referring domains significantly decreased on the day of the attack, indicating potential use of direct requests or automated scripts instead of typical referrer-based traffic.</p>
    
  <h2>3. HTTP Response Code Analysis</h2>
    <h3>Suspicious Changes in HTTP Response Codes</h3>
    <ul>
        <li><strong>200 (OK)</strong>: Decreased, suggesting fewer successful requests.</li>
        <li><strong>404 (Not Found)</strong>: Increased, possibly due to automated scanners probing for vulnerabilities or non-existent resources.</li>
    </ul>
    
  <h2>4. International Activity Alert Analysis</h2>
    <h3>Suspicious Volume of International Activity</h3>
    <pre>
    source="apache_logs.txt" | iplocation clientip | where Country!="United States"
    source="apache_attack_logs.txt" | iplocation clientip | where Country!="United States"
    </pre>
    <p><strong>Key Findings:</strong></p>
    <ul>
        <li>The attack occurred at <strong>8:00 PM</strong>, with a peak count of <strong>937 requests</strong>.</li>
        <li>The alert was triggered since the volume exceeded the predefined threshold of <strong>70 requests</strong>.</li>
        <li>After reviewing, a threshold adjustment was considered to minimize false positives.</li>
    </ul>
    
  <h2>5. HTTP POST Activity Alert Analysis</h2>
    <h3>Suspicious Volume of HTTP POST Activity</h3>
    <pre>
    source="apache_logs.txt" method="POST"
    source="apache_attack_logs.txt" method="POST"
    </pre>
    <p><strong>Key Findings:</strong></p>
    <ul>
        <li>The peak count reached <strong>1296 requests</strong> at <strong>8:00 PM</strong>.</li>
        <li>The attack occurred on <strong>Wednesday, March 25th, 2020</strong>.</li>
        <li>The threshold remains unchanged, but further analysis may warrant adjustments.</li>
    </ul>
    
   <h2>6. Time Chart Analysis for HTTP Methods</h2>
    <h3>Suspicious Trends in HTTP Methods</h3>
    <pre>
    host=apache_logs source="apache_logs.txt"  | timechart count by method
    host=apache_logs source="apache_attack_logs.txt"  | timechart count by method
    </pre>
    <p><strong>Findings:</strong></p>
    <ul>
        <li>The attack started at <strong>7:00 PM</strong> and ended at <strong>9:00 PM</strong>.</li>
        <li>The peak <strong>POST</strong> request count was <strong>1296</strong>.</li>
    </ul>
    
  <h2>7. Cluster Map Analysis</h2>
    <h3>Suspicious International Activity</h3>
    <pre>
    host=apache_logs source="apache_logs.txt" | iplocation clientip |search Country!="United States"| geostats count by clientip
    host=apache_logs source="apache_attack_logs.txt" | iplocation clientip |search Country!="United States"| geostats count by clientip
    </pre>
    <p><strong>Key Findings:</strong></p>
    <ul>
        <li><strong>Kiev:</strong> 438 requests</li>
        <li><strong>Kharkiv:</strong> 432 requests</li>
    </ul>
    
   <h2>8. URI Data Analysis</h2>
    <h3>Suspicious URI Activity</h3>
    <pre>
    source="apache_logs.txt"
    source="apache_attack_logs.txt"
    </pre>
    <p><strong>Findings:</strong></p>
    <ul>
        <li>The most accessed URI was <strong>VSI_Account_logon.php</strong>.</li>
        <li>Potential attack methods:</li>
        <ul>
            <li><strong>Brute-force login attempts</strong>: Repeatedly trying username and password combinations to gain unauthorized access.</li>
            <li><strong>Session hijacking or credential stuffing</strong>: Using stolen credentials to log in.</li>
            <li><strong>Exploiting vulnerabilities</strong>: Testing for SQL Injection, XSS, or authentication bypass.</li>
        </ul>
    </ul>
    
  <h2>Conclusion & Recommendations</h2>
    <h3>Key Takeaways:</h3>
    <ul>
        <li>Spike in HTTP POST Requests: Increased to <strong>1296 requests at 8:00 PM</strong>.</li>
        <li>Changes in Response Codes: A decline in <strong>200 OK</strong> and a rise in <strong>404 Not Found</strong>.</li>
        <li>Unusual International Activity: High request volume from <strong>Kharkiv and Kiev, Ukraine</strong>.</li>
        <li>Referrer Domains and URI Changes: Attackers bypassed referrer-based traffic and targeted login URIs.</li>
    </ul>
    
  <h3>Recommendations:</h3>
    <ul>
        <li>Implement <strong>rate limiting</strong> for POST requests to prevent brute-force attacks.</li>
        <li><strong>Monitor international traffic</strong> and block known malicious sources.</li>
        <li>Strengthen <strong>authentication mechanisms</strong>, including multi-factor authentication (MFA).</li>
        <li>Regularly audit <strong>server logs</strong> to detect and mitigate attacks early.</li>
    </ul>
</body>
</html>

