# Tier 3 would take Tier 2 findings and ask:

- Can this happen elsewhere?

- How do we detect it next time?

- Is this campaign targeting others?

<br />

**Threat Hunting**

Hunt for

- files.bpakcaging.xyz
  
- cdn.bpakcaging.xyz

Across

- DNS logs
  
- Proxy logs
  
- SIEM
  
- EDR

<br />

**CTI**

Profile infrastructure

- bpakcaging.xyz
 
Questions

- Is this known malware?

- Has this domain been seen before?

- Any related campaigns?

<br />

**Detection Engineering**

Create detections for:

LNK launching PowerShell

- Parent:

- explorer.exe

- Child:

- powershell.exe

Download Cradle

- Powershell

- (new-object net.webclient).downloadstring

Seatbelt Execution

- seatbelt.exe

DNS Exfiltration

- Large DNS queries

- Hex-encoded subdomains

- Excessive nslookup usage




