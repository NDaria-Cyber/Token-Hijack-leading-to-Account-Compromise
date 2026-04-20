# Token-Hijack-leading-to-Account-Compromise (Real Incident)

**Date** : March 2026

**Context** : Personal Windows Machine

## Summary 

This report documents how a Windows machine got infected with malware (Raccoon infostealer) after user executed a malicious .exe file from a compromised legitimate looking website since the user didn't verify file source.

## Observations

- Multiple phishing messages were being sent by user, but with no user execution.
- A few suspicious logins from unreachable geolocations for the user

## Analysis

- After a full system scan, security tools have discovered multiple 'Infostealers' trojans, such as Raccoon infostealer
- Account email had been changed before compromise on a digital platform ( 1:47 PM EET, UTC+2). MITRE : T1555 (Credentials from Web Browser).The malware stole session tokens from browser memory.
- Account privileges settings had been changed ( Two-Factor Authentication disabled), suggesting account compromise and manipulation (2:14 PM EET, UTC+2). MITRE : T1098.002 (Account Manipulation - Modify User Account). This allows the attacker to maintain access without triggering 2FA alerts.
- Soon after on Discord, user's account had been compromised and used to send phishing messages (2:15 PM EET,UTC+2). MITRE : T1550.001 (Use Alternate Authentication Material - Pass the Cookie/Token)
- Instagram sent an alert of an unauthorized, suspicious Windows login ( 11:00 PM EET, UTC+2). MITRE : T1078 (Valid Accounts).
- Unauthorized access was used to send phishing messages by user on Instagram ( 11 :15 PM EET, UTC+2).MITRE: T1550.001 (Use Alternate Authentication Material - Pass the Cookie/Token)
- Later, unusual sign-ins alerts had been provided by Microsoft 365 ( 11:30 PM EET, UTC+2) from impossible geolocations.MITRE: T1078.001 (Valid Accounts) + T1550.001 (Use Alternate Authentication Material).


## Advanced Behaviour Observed

- All things considered, these lead to a token theft (token hijacking) rather than credential theft.
- There is no evidence of credential use. Just the token and session cookies, as given by the infostealers.
- In addition, the hacker did not try to  change the account's password which indicates that spreading malware in a short period of time was more important than the user account itself.
- After an additional analysis, logging out the user from all sessions had stopped the phishing emails from being sent, which confirms the idea of token hijacking.Once the user logged out, the session cookies and tokens have expired.
- Moreover, despite removing the infostealers, before user could change/log out from the sessions, the next day the user's account has been compromised.This means that the hacker had stolen the tokens before the malware was removed.


## Response Actions

- Deep system full scan with anti-malware and anti-virus security tools
- Activated MFA and changed user's password for each compromised account
- Logged out user from all sessions, removed all authorized devices and deleted browser cookies
- Installed an Authenticator Application for the user (which generates time-based one-time passwords) for each compromised account
- Checked the IP's reputation and reported it
- Monitored user's accounts to ensure no reoccurrence 

## Impact

- Confirmed various account compromises
- Exposureof sensitive data to the attacker (personal messages)
- Loss of control of user's own account
- Risk of permanent account loss
- Session abuse through unauthorized access



## Supporting evidence

The following alerts show unknown devices or locations.While they don't conclude the proof by themselves, they correlate with the timeline of the malware infection and the idea of token theft.

<img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/90e56e8d-8ab2-4bc7-a02d-df1f159616d6" />

<img width="1079" height="465" alt="login2" src="https://github.com/user-attachments/assets/413b0c6f-c11e-4def-838e-66cce59a1756" />

<img width="1061" height="238" alt="Login3" src="https://github.com/user-attachments/assets/5f441d25-49fb-410e-abb7-5ff3f315f883" />

## Recommendations 
- Avoid executing unknown .exe files
- Enable end-point security protection
- Verify file and file source before executing
- Use browser sandboxing

## Conclusion

- This incident shows a confirmed account compromise due to malware (such as Infostealers) after user executed a suspicious, .exe file.The Windows machine and user's accounts have been successfully recovered.

**Note:** This analysis is based on a real-world incident encountered during personal system monitoring.

