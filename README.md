# 🛡️ Phishing Email Analysis Project Using PhishTool, Sublime Text, CyberChef, and VirusTotal

## 📌 Project Title
**Comprehensive Phishing Email Analysis Using Multi-Tool Approach**

---

## 🎯 Project Objectives
- Extract and interpret metadata from a phishing email sample
- Use multiple tools to analyze headers, body, URLs, and attachments
- Answer target questions to assess the legitimacy of the email
- Document analytical thinking and use of open-source tools

---

## 💼 Tools Used
- [PhishTool Community](https://www.phishtool.com/community)
- [CyberChef](https://gchq.github.io/CyberChef/)
- [VirusTotal](https://www.virustotal.com/)
- Sublime Text (for raw `.eml` analysis)
- Sample `.eml` file (redacted for safety)

---

## 📥 Setup and Workflow Overview

### Step 1: Prepare Your Environment
- Register and log in to PhishTool Community
  <img width="1262" alt="01-Register for community " src="https://github.com/user-attachments/assets/7219509e-9b3a-4852-9fd4-48c8157e74bd" />
  
<img width="397" alt="02-signup" src="https://github.com/user-attachments/assets/b619396a-8fbd-4a43-9b2f-ff6025a31191" />

<img width="1195" alt="03-Dashboard" src="https://github.com/user-attachments/assets/8ba39b9a-f6cc-4253-8c6d-dd4c0ee05625" />

- Access CyberChef in browser
  <img width="1274" alt="06-Cyberchef" src="https://github.com/user-attachments/assets/4a800a3d-d048-4f2b-b248-a12a61f02b32" />

- Open VirusTotal
  <img width="1256" alt="07-VirusTotal" src="https://github.com/user-attachments/assets/ed082f4d-e6be-40f5-91d6-58c91bbfdff1" />

- Launch Sublime Text for local `.eml` viewing
  <img width="1142" alt="08-Sublime" src="https://github.com/user-attachments/assets/df7c0457-7175-4323-997e-a9fb5a5d446f" />


### Step 2: Upload `.eml` to PhishTool
- Navigate to "Upload Email" in PhishTool dashboard
  <img width="1244" alt="04 Analyze-Choose file" src="https://github.com/user-attachments/assets/d092cc1d-1483-464f-b4e1-f3c5371cdd3a" />
  
- Upload the sample `.eml` file;
 - <img width="668" alt="09-select eml file" src="https://github.com/user-attachments/assets/5a8a5ea4-6fb8-48ac-9986-3289a1c04d29" />

- Analyze header and body metadata
<img width="617" alt="10-header" src="https://github.com/user-attachments/assets/3fa6c566-04a4-4337-a45c-e2be716b4eb8" />

### Step 3: Answer Target Questions

1. **Full date and time of email delivery:**
   - Found in the `Date:` header field in Sublime Text
<img width="809" alt="11-date sublime" src="https://github.com/user-attachments/assets/42dc153b-38ac-4ab3-8910-ce8f201f5361" />

2. **Subject of the email:**
   - Extracted from `Subject:` header
     <img width="875" alt="13-Subject" src="https://github.com/user-attachments/assets/3e1850eb-19d5-49c4-9e5d-7c97a046d33b" />


3. **Recipient of the email:**
   - Check `To:` field
<img width="878" alt="14-To" src="https://github.com/user-attachments/assets/dae76628-5559-4322-acdf-66a525f648d8" />

4. **Sender's display name:**
   - Extracted from `From:` field (before the `<email>` part)
<img width="529" alt="15-sender-display name" src="https://github.com/user-attachments/assets/251b48a0-ac2c-489e-a5f7-6167c5cc3e97" />

5. **Sender's email address:**
   - Found in `From:` header within `< >`
<img width="867" alt="16-Sender - email" src="https://github.com/user-attachments/assets/b61f36b3-16d5-47ac-906e-d22dc287680b" />

6. **Bounce/return path address:**
   - Found in `Return-Path:` header
     <img width="752" alt="17-return path" src="https://github.com/user-attachments/assets/2dbb97f6-8765-4903-8314-a7cdf0aced5a" />

   - Compare with `From:` address to determine spoofing
    <img width="635" alt="17-return path-phish" src="https://github.com/user-attachments/assets/3ab7a469-5b74-4680-a64c-19293a3a74e3" />

7. **Sender's IP address:**
   - Extracted from `Received:` headers (bottom-most IP is likely the sender)
<img width="610" alt="18-Sender IP" src="https://github.com/user-attachments/assets/5f85e828-ab5f-42c8-907a-afcc3a36bb3f" />

8. **Sender resolved hostname:**
   - Use `nslookup` or IP lookup via VirusTotal or AbuseIPDB
<img width="570" alt="19-resolved hostname" src="https://github.com/user-attachments/assets/8b5e3919-c6c7-4289-a6fa-e8b760ee9b77" />

9. **Owner of the sender's IP address:**
   - Found via VirusTotal IP details or WHOIS lookup
<img width="652" alt="20-IP Owner" src="https://github.com/user-attachments/assets/c6cd451e-e460-4dc8-b560-348e5ebc4b76" />

10. **SPF Check:**
   - Check `Authentication-Results:` header
<img width="609" alt="21-SPF" src="https://github.com/user-attachments/assets/852bd366-959a-4cb8-9d00-e406e15429ed" />

11. **Encoding used in the body content:**
   - Look for `Content-Transfer-Encoding:` field (e.g., `base64`, `quoted-printable`)
<img width="730" alt="22-encoding" src="https://github.com/user-attachments/assets/6779fb30-e1c7-4913-a536-06088272c57b" />

12. **Second URL (defanged format):**
   - Extract URLs using CyberChef → "Extract URLs" recipe
     <img width="1261" alt="23-Extract URL" src="https://github.com/user-attachments/assets/d18b29ea-1a9c-4460-9e0d-ceb2acb0a410" />

   - Defang by replacing `.` with `[.]` and `http` with `hxxp`
<img width="1264" alt="24-Defang" src="https://github.com/user-attachments/assets/ae7ab4fe-311b-420e-a2d1-ea6091072db3" />

13. **VirusTotal verdict (Fortinet):**
   - Paste second URL into VirusTotal
     - <img width="726" alt="25-virusTotal" src="https://github.com/user-attachments/assets/30babd00-0fa5-40d2-a898-54dcc23f5397" />

   - Under "Community" or "Details" tab, check Fortinet's verdict (e.g., `Malicious`)
<img width="1217" alt="26-Fortinet" src="https://github.com/user-attachments/assets/4c4a4beb-365f-403d-9a29-161eb3e6621b" />

14. **[Yes/No] - Is the email genuine?**
   - Based on red flags from metadata, content, links, and VirusTotal scan, conclude.
     
*`The email is not genuine`*
---

### 📄 Email Analysis Report

**Subject:** Reset your password urgently

**Date Received:** Tue, 31 Oct 2023 10:10:04 -0900

**To:** dderringer@mighty-solutions.net

**From (Display Name):** Outlook Support Team

**From (Email):** social201511138@social.helwan.edu.eg 

**Return-Path:** social201511138@social.helwan.edu.eg  

**Sender IP Address:** 40.107.22.60 

**Resolved Hostname:** mail-am6eur05on2060.outbound.protection.outlook.com 

**IP Ownership:** AS8075 MICROSOFT-CORP-MSN-AS-BLOCK, US. Registered Mar 31, 1997 - via WHOIS lookup 

**SPF Result:** PASS (sender authorized for domain)  

**DKIM Result:** DKIM: BODY HASH DID **NOT** VERIFY

**Encoding:** base64  

**Second Extracted URL (defanged):** hxxps[://]0[.]232[.]205[.]92[.]host[.]secureserver[.]net/lclbluewin08812/

**VirusTotal Verdict (Fortinet):** Malicious – Phishing  

### 🔍 Final Verdict
**Is this email genuine?** ❌ **No**

> The email contains multiple indicators of phishing: forged sender address, obfuscated URL, and malware-related verdict from Fortinet via VirusTotal.

---

## ✅ Summary
This project showcases a thorough phishing investigation using a multi-tool approach: PhishTool for structured header analysis, Sublime Text for raw view, CyberChef for URL extraction, and VirusTotal for threat intel. It demonstrates your capability to detect malicious elements in emails — a critical skill in IT Security and SOC roles.
