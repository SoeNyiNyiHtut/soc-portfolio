# 🔐 Brute Force Attack Detection

## 📌 Tool Used
- Splunk (SIEM)

## 📊 Summary
This project demonstrates detection of brute-force login attempts using log analysis in a SIEM environment.

## 🚨 Findings

### 🔹 Attacker 1
- IP Address: 192.168.1.10  
- Behavior:
  - Multiple failed login attempts  
  - Targeted users: admin, root, guest, test  
  - High frequency → indicates automated brute-force attack  

### 🔹 Attacker 2
- IP Address: 203.0.113.5  
- Behavior:
  - Focused on root account  
  - Lower frequency but still suspicious  

## 🔍 Detection Query

index=* "Failed password"
| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| rex "user (?<user>\w+)"
| stats count by user, src_ip

## 🛡️ Conclusion
The analysis confirms a brute-force attack targeting SSH authentication.

## 🔐 Recommendations
- Block attacker IP addresses  
- Enable MFA  
- Monitor login activity
