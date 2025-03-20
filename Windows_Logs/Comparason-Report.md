<!DOCTYPE html>
<html>
<head>
    <title>Comparison Report: Windows Server Logs vs. Windows Attack Logs</title>
</head>
<body>
    <h1>Comparison Report: Windows Server Logs vs. Windows Attack Logs</h1>
    
   <h2>1. Severity Analysis</h2>
    <h3>Suspicious Changes in Severity</h3>
    <p>There was an increase in high-severity events from <strong>6.90%</strong> to <strong>20.22%</strong>, indicating a significant rise of <strong>13.31%</strong>.</p>
    
  <pre>
    host=Windows_Server_Logs  source="windows_server_logs.csv"  |  top severity
    host=Windows_Server_Logs  source="windows_server_attack_logs.csv"  |  top severity
    </pre>
    
   <h2>2. Failed Activities Analysis</h2>
    <h3>Suspicious Changes in Failed Activities</h3>
    <p>A drop in failure count from <strong>142</strong> to <strong>93</strong> was observed. While this may indicate improvements, further investigation is necessary to rule out hidden issues.</p>
    
  <pre>
    host=Windows_Server_Logs  source="windows_logs.csv"   |  top status
    host=Windows_Server_Logs  source="windows_server_attack_logs.csv"   |  top status
    </pre>
    
   <h2>3. Alert Analysis for Failed Windows Activity</h2>
    <p>Suspicious rise in failed login attempts detected within an hour.</p>
    <ul>
        <li><strong>Count of failed attempts:</strong> 35</li>
        <li><strong>Time:</strong> March 25, 2020, at 08:00 AM</li>
        <li><strong>Alert Trigger:</strong> Yes (threshold: 15)</li>
        <li><strong>Threshold Review:</strong> No changes needed (current baseline: 9-10)</li>
    </ul>
    
   <h2>4. Alert Analysis for Successful Logins</h2>
    <pre>
    host=Windows_Server_Logs source="windows_server_logs.csv" signature_id="4624"| timechart span=1h count as successful_logins
    host=Windows_Server_Logs source="windows_server_attack_logs.csv" signature_id="4624"| timechart span=1h count as successful_logins
    </pre>
    <p><strong>Findings:</strong></p>
    <ul>
        <li><strong>Suspicious period:</strong> 09:00 AM (16 logins), 10:00-11:00 AM (0 logins), 12:00 PM (4 logins)</li>
        <li><strong>Primary user:</strong> User_a</li>
        <li><strong>Time:</strong> March 25, 2020, at 02:00 AM</li>
        <li><strong>Alert Trigger:</strong> Yes (threshold: 10)</li>
        <li><strong>Threshold Review:</strong> Consider increasing to avoid false alerts.</li>
    </ul>
    
  <h2>5. Alert Analysis for Deleted Accounts</h2>
    <p>Suspicious drop in account deletions between <strong>9:00 AM - 11:00 AM</strong>, possibly to avoid detection.</p>
    
  <h2>6. Time Chart Analysis for Signatures</h2>
    <p><strong>Suspicious Signatures:</strong></p>
    <ul>
        <li><strong>4740:</strong> Locked out accounts (01:00 AM - 02:00 AM, peak: 896)</li>
        <li><strong>4624:</strong> Successful logins (11:00 AM - 12:00 PM, peak: 196)</li>
        <li><strong>4724:</strong> Password resets (09:00 AM - 10:00 AM, peak: 1258)</li>
    </ul>
    
  <h2>7. User Activity Analysis</h2>
    <pre>
    host=Windows_Server_Logs | timechart span=1h count by user
    host=Windows_Server_Logs source="windows_server_attack_logs.csv" | timechart span=1h count by user
    </pre>
    <p><strong>Suspicious Users:</strong></p>
    <ul>
        <li><strong>User_a:</strong> 01:00 AM - 03:00 AM (peak: 984)</li>
        <li><strong>User_j:</strong> 11:00 AM - 12:00 PM (peak: 196)</li>
        <li><strong>User_k:</strong> 09:00 AM - 10:00 AM (peak: 1256)</li>
    </ul>
    
   <h2>8. Statistical vs. Graphical Analysis</h2>
    <p>Using statistical charts makes it easy to see event counts per user, but bar and pie charts offer better visualization for volume differences.</p>
    
   <h2>Conclusion & Recommendations</h2>
    <h3>Key Takeaways:</h3>
    <ul>
        <li>Severity increase of <strong>13.31%</strong> detected.</li>
        <li>Failed login attempts peaked at <strong>35</strong> in an hour.</li>
        <li>Suspicious user activity for <strong>User_a, User_j, User_k</strong>.</li>
        <li>Potential attacker activity detected by avoiding account deletions.</li>
    </ul>
    
   <h3>Recommendations:</h3>
    <ul>
        <li>Enhance <strong>monitoring</strong> for high-severity events.</li>
        <li>Adjust <strong>alert thresholds</strong> to reduce false positives.</li>
        <li>Implement <strong>multi-factor authentication (MFA)</strong> for critical accounts.</li>
        <li>Analyze and audit <strong>user activity logs</strong> regularly.</li>
    </ul>
</body>
</html>

