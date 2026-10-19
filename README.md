# SSH Brute-Force Detection and Investigation with Wazuh

## Project Overview
This project demonstrates how a Security Operations Center (SOC) analyst can investigate repeated SSH authentication failures using Wazuh SIEM in an isolated virtual lab.

## Lab Environment
- **SIEM:** Wazuh 4.14.8
- **Analyst system:** Kali Linux
- **Target system:** Metasploitable 2
- **Log source:** SSH daemon (`sshd`) and PAM authentication logs
- **Log collection:** Remote syslog forwarding

## Objective
Detect and investigate repeated SSH login failures, review Wazuh alerts, identify the source and target systems, and map relevant activity to MITRE ATT&CK.

## Detection Evidence
- **Wazuh Rule ID:** 2502
- **Alert level:** 10
- **MITRE ATT&CK technique:** T1110 — Brute Force
- **Tactic:** Credential Access
- **Observed message:** PAM reported additional authentication failures.

## Investigation Process
1. Generated a small number of controlled failed SSH login attempts in the isolated lab.
2. Forwarded target-system logs to the Kali system.
3. Reviewed the resulting alerts in Wazuh Threat Hunting.
4. Examined the rule ID, severity, timestamp, source, target, and log details.
5. Saved screenshots and documented the investigation.

## Findings
Wazuh generated an alert associated with repeated SSH authentication failures. The observed event was mapped to MITRE ATT&CK T1110.

A single alert does not establish that a sustained brute-force campaign or account compromise occurred. Correlation across multiple events would be required for a stronger conclusion.

## Recommendations
- Monitor repeated SSH authentication failures.
- Investigate source IP addresses and event timelines.
- Use strong, unique passwords and restrict SSH access.
- Review authentication logs for successful logins following repeated failures.

## Evidence
Screenshots are stored in the `screenshots/` directory. Investigation notes are stored in `reports/investigation-notes.txt`.

## Skills Demonstrated
Wazuh SIEM, Linux log analysis, SSH authentication investigation, syslog, alert triage, MITRE ATT&CK mapping, and incident documentation.

## Disclaimer
This project was performed in an isolated, authorized virtual lab for educational purposes.
