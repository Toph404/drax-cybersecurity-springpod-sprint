# Drax: Cyber Security Sprint – Reflection Notes

## Project Overview
This sprint simulated the workflow of a Cyber Defence Centre (CDC) analyst investigating potentially malicious network activity.  
I examined several log images, extracted destination IP addresses, and used VirusTotal and Whois to assess the reputation and ownership of each IP.

The main goal was to determine which connections were safe, suspicious, or anomalous and propose steps to prevent similar incidents in the future.

## Findings Summary

| Log | Verdict | Reasoning |
|-----|----------|------------|
| A | Safe | Whois confirmed AWS ownership; expected destination. |
| B | Suspicious | VirusTotal flagged 7/95 detections; Whois showed Latvia-based 2CloudLtd instead of AWS or Microsoft. |
| C | Safe | AWS range confirmed; consistent HTTPS behavior; no VirusTotal flags. |
| D | Safe | Same behavior as Log C; legitimate AWS IP. |
| E | Borderline | Appeared AWS-owned but had repeated connections; likely internal process but worth monitoring. |

Anomalous IP Identified: 185.176.220.70 (Log B)  
Reason: Non-AWS domain, flagged by VirusTotal, unusual traffic pattern, beaconing behavior noted.

## Reflection

### What I Found Interesting
- How VirusTotal aggregates multiple antivirus engines and reputation systems to assess risks.  
- How Whois reveals ownership and geolocation data, helping distinguish legitimate corporate networks (like AWS) from unknown providers.  
- The use of contextual factors such as frequency, timing, and destination to make real-world security judgments rather than relying solely on threat scores.  

### What I Found Challenging
- Interpreting VirusTotal results and understanding what "7/95 detections" means in context.  
- Differentiating between legitimate cloud activity (AWS) and truly malicious IPs.  
- Writing concise justifications for each log decision while staying technical yet understandable.  

## Lessons Learned
- Always correlate threat intelligence data with log behavior.  
- Not all flagged IPs are malicious, but patterns matter.  
- Automating reputation checks could significantly streamline an analyst’s workflow.  
- Documentation and post-incident reviews help improve future response procedures.  

## Tools Used
- VirusTotal – Threat intelligence aggregation  
- Whois.com – Domain and IP ownership lookup  
- Darktrace Logs (simulation) – Network activity analysis  

## Future Improvements
- Automate IP reputation lookups via APIs.  
- Implement a visualization dashboard for log frequency.  
- Integrate sandbox testing to verify flagged IPs.  


