# Tier 2 asks:

- What happened?

- How bad is it?

- What was accessed?

- Was data stolen?

<br />

**Initial Access**

Phishing Email 

- Attachment: Invoice_20230103.lnk

![image](images/task2-2.png)

<br />

Execution

PowerShell Download Cradle

- Domain: files.bpakcaging.xyz

![image](images/task2-7.png)

MITRE

- T1566.001 - Phishing

- T1059.001 - PowerShell

<br />

**Discovery**

Attacker downloaded

- seatbelt.exe

![image](images/seatbelt.png)

<br />

Purpose

- Host enumeration

![image](images/seatbelt2.png)

<br />

MITRE

- T1082 - System Information Discovery

<br />

**Collection**

Accessed

- C:\Users\j.westcott\AppData\Local\Packages\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe\LocalState\plum.sqlite

![image](images/task3-4.png)

<br />

![image](images/plum.png)

<br />

Purpose

- Harvest Sticky Notes data

<br />

**Sensitive Data Collection**

File

- protected_data.kdbx

Type

- KeePass Password Database

![image](images/keepas.png)

<br /><br />

**Exfiltration**

Tool

- nslookup

Encoding

- hex

Protocol

- DNS

MITRE

- T1048 - Exfiltration Over Alternative Protocol

- T1071.004 - Application Layer Protocol: DNS

![image](images/task4-1.webp)

<br />

![image](images/task4-2.webp)

<br />

![image](images/task4-3.webp)

<br />

![image](images/task4-4.webp)

<br />

![image](images/task4-5.webp)

<br />

![image](images/task4-6.webp)

<br />

![image](images/task4-7.webp)

<br />

![image](images/protected_data.png)

<br />

![image](images/master_key.png)

<br />

![image](images/master_key_2.png)

<br />

![image](images/master_key_3.png)

<br /><br />

## Impact Assessment

Impact:

Sensitive data exposed.

Confirmed access to:

- Sticky Notes database

- KeePass database

Data successfully exfiltrated.

Credit card information recovered from exfiltrated data.

Compromise severity: **HIGH**

<br /><br />

## Tier 2 Recommendations

- Isolate workstation.

- Reset all credentials stored in KeePass.

- Notify financial institution.

- Block attacker infrastructure.

- Review neighboring endpoints.

- Review DNS logs enterprise-wide.






















