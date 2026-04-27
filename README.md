# Token-Hijack-leading-to-Account-Compromise (Real Incident)

**Date** : March 2026

**Context** : Personal Windows Machine

## Summary 

This report documents how a Windows machine got infected with malware (Raccoon Infostealer) after user executed a malicious .exe file from a compromised legitimate looking website.

## Root Cause 

**Social Engineering** : user executed a malicious .exe file which imitated a legitimate service (Krita - digital painting). The deception worked given :

- The same name as the legitimate service (krita.io instead of krita.org)
- Virtually identical web design
- User didn't check the URL name (fake domain name)

**Technical Level** : the malware was able to persist and hijack the accounts since :

- The installer of the application stopped at 100% for a long period of time which might have provided time for the malware to execute background payload
- No real-time protection enabled on the machine
- Malware didn't depend on Wifi, but on the execution of the malicious file
- No VPN /VM/Sandbox connected, hence the attacker connected directly to the host machine
- Lack of MFA/2FA (Multiple Factor Authentication/2 Factor Authentication) in some accounts


## Observations

- Multiple phishing messages were being sent by user, but with no user interaction
- A few suspicious logins from unreachable geolocations for the user at that time
- PC being slower than usual and unusual high CPU spikes

## Analysis

- After a full system scan, security tools have discovered multiple 'Infostealers' trojans, such as 'Raccoon Infostealer'
- Account email had been changed before compromise on an EA account( 1:47 PM EET, UTC+2).
- Account privileges settings had been changed ( Two-Factor Authentication disabled), suggesting account compromise and manipulation (2:14 PM EET, UTC+2).This allows the attacker to maintain access without triggering 2FA alerts.
- Soon after on Discord, user's account had been compromised and used to send phishing messages (2:15 PM EET,UTC+2).
- Instagram sent an alert of an unauthorized, suspicious Windows login ( 11:00 PM EET, UTC+2). 
- Unauthorized access was used to send phishing messages by user on Instagram ( 11 :15 PM EET, UTC+2).
- Later, unusual sign-ins alerts had been provided by Microsoft 365 ( 11:30 PM EET, UTC+2) from impossible geolocations.


## Advanced Behaviour Observed

- All things considered, these lead to a token theft (token hijacking) rather than credential theft.
- There is no evidence of credential use. Just the token and session cookies, as given by the infostealers. It had time to steal the cookies and tokens while the installation was at 100% for at least 10 minutes, then terminated.
- In addition, the hacker did not try to  change the account's password which indicates that spreading malware in a short period of time was more important than the user account itself.
- After an additional analysis, logging out the user from all sessions had stopped the phishing emails from being sent, which confirms the idea of token hijacking.Once the user logged out, the session cookies and tokens have expired.
- Moreover, despite removing the infostealers, before user could change/log out from the sessions, the next day the user's account has been compromised.This means that the hacker had stolen the tokens before the malware was removed. Even with the removal, the cookies had already been stolen.
- The phishing messages were sent within seconds one after another, indicating tools, AI bots or automated scripts that were used in this compromise. ( Eg : 50 messages at the same hour). Another hint is that all DM's were muted so the user cannot be informed by the account compromise or an utility of the automated script/AI bot.
- Session cookies/ Token theft is common in account takeovers incidents.


## MITRE ATT&CK MAPPING 

- Initial Compromise (T1204.002 - User Execution: Malicious File) : the user executes the malicious file
- Execution (T1547.001 - Registry Run Key) : after the file was executed, it persisted through scripts at every boot up (HKLM\SOFTWARE\MICROSOFT\WINDOWS NT\CURRENTVERSION\SCHEDULE\TASKCACHE\PLANID\...)
- Session/Cookies theft ( T1539 - Steal Web Session Cookie) : attacker steals the session cookies to gain access to web applications and related information in browser history
- Credential Access (TA0006) - Steal Application Token (T1528) and T1539 - steal   Web Session Cookies
- Potential Account Discovery ( T1087) : attacker tries to get a listing of valid accounts, usernames or email addresses in order to takeover
- Two-Factor Authentication disabled ( T1098.002 - Account Manipulation - Modify User Account)
- Command & Control (C2) (T1071.001 - Web Protocol) : adversary talks through HTTP/S to the C2 server


## Response Actions

- Deep system full scan with anti-malware and anti-virus security tools
- Activated MFA and changed user's password for each compromised account and application
- Logged out user from all sessions, removed all authorized devices and deleted browser cookies
- Deleted all browsers and reinstalled them for extra measurements and clean data
- Installed an Authenticator Application for the user (which generates time-based one-time passwords) for each compromised account
- Monitored user's accounts to ensure no reoccurrence 

## Impact

- Confirmed various account compromises
- Potential exposure of sensitive data to the attacker (personal messages, posts, photos)
- Loss of control of user's own account without notice
- Risk of permanent account loss if the response time was later
- Session abuse through unauthorized access



## Supporting evidence

The following alerts show unknown devices or locations.While they don't conclude the proof by themselves, they correlate with the timeline of the malware infection and the idea of token theft.

<img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/90e56e8d-8ab2-4bc7-a02d-df1f159616d6" />

<img width="1079" height="465" alt="login2" src="https://github.com/user-attachments/assets/413b0c6f-c11e-4def-838e-66cce59a1756" />

<img width="1061" height="238" alt="Login3" src="https://github.com/user-attachments/assets/5f441d25-49fb-410e-abb7-5ff3f315f883" />

## Recommendations 
- Avoid executing unknown .exe files from untrusted sources
- Revoke all active sessions after compromise
- Verify file and file source before executing
- Use browser sandboxing for suspicious or for files you don't trust
- Enable MFA on all accounts
- Monitor login activity and new device alerts


## Conclusion

- This incident shows a confirmed account compromise due to malware (such as Infostealers) after user executed a suspicious, .exe file.The Windows machine and user's accounts have been successfully recovered.

**Note:** This analysis is based on a real-world incident encountered during personal system monitoring.

