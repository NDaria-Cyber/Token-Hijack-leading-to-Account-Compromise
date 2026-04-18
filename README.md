# Token-Hijack-leading-to-Account-Compromise

**Date** : March 2026

**Context** : Personal Windows Machine

## Summary 

This report documents how a Windows machine got infected with malware after user executed a suspicious .exe file, later leading to account compromise due to token hijacking.

## Observations

- Multiple phising messages were being sent by user, but with no user execution.
- A few suspicious logins from unreachable geolocations for the user

## Analysis

- After a full system scan, security tools have discovered multiple 'Infostealers' trojans
- Account email had been changed before compromising for digital platform ( 1:47 PM EET, UTC+2)
- Account privileges settings had been changed (MITRE T1098, Login Verification OFF), suggesting account compromise and manipulation (2:14 PM EET, UTC+2)
- Soon after, on a social media application 1, user's account had been compromised and used to send phishing messages (2:15 PM EET,UTC+2)
- Social media application 2 sent an alert of an unauthorized, suspicious Windows login ( 11:00 PM EET, UTC+2)
- Unauthorized access was used to send phising messages by user on social media application 2 ( 11 :15 PM EET, UTC+2)
- Later, unusual sign-ins alerts had been provided from Microsoft services ( 11:30 PM EET, UTC+2).These were impossible to reach geolocations for user at the time.

## Advanced Behaviour Observed

- All things considered, these lead to a token theft (token hijacking) rather than credential theft.
- The hacker did not know the password,nor the username and only had the token and session cookies, as given by the infostealers.
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
- Expose of sensible data to the attacker (personal messages)
- Loss of control of user's own account
- Potential loss of accounts
- Session abuse through unauthorized access

## Supporting evidence

The following alerts show unknown devices or locations.While they don't conclude the proof by themselves, they corelate with the timeline of the malware infection and the idea of token theft.

<img width="300" height="400" alt="image" src="https://github.com/user-attachments/assets/90e56e8d-8ab2-4bc7-a02d-df1f159616d6" />

<img width="1079" height="465" alt="login2" src="https://github.com/user-attachments/assets/413b0c6f-c11e-4def-838e-66cce59a1756" />

<img width="1061" height="238" alt="Login3" src="https://github.com/user-attachments/assets/5f441d25-49fb-410e-abb7-5ff3f315f883" />

## Conclusion

- This incident shows a confirmed account compromise due to malware (such as Infostealers) after user executed a suspicious, .exe file.

**Note:** This analysis is based on a real-world incident encountered during personal system monitoring.

