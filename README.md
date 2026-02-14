# Networking Lab  — Windows Server AD DS + DHCP + DNS + IIS + Group Policy (Azure)

This lab builds a small Windows domain environment and verifies core enterprise services: **Active Directory Domain Services (AD DS)**, **DNS**, **DHCP**, **IIS**, and **Group Policy**.  
It includes configuration validation via command output (e.g., `ipconfig /all`, `nslookup`, `gpresult`) and screenshots aligned with the lab checklist.

---

## Lab Objectives
- Configure a Windows Server domain controller (**DC1**) with a static IP
- Install and configure **AD DS** and create a new domain (`myclass.local`)
- Install and configure **DNS** and verify name resolution
- Configure **DHCP** scopes and lease distribution to domain clients
- Join Windows client machines to the domain and verify authentication
- Host a basic website using **IIS** and confirm it loads from the server
- Apply and verify **Group Policy** (e.g., restrictions / wallpaper)

---

## Environment
**Platform:** Azure Virtual Machines  
**Server:** Windows Server (DC1)  
**Client:** Windows 10/11 (LAB-PC1)

**Domain:** `myclass.local`  
**Example IP scheme (from lab):**
- DC1: `10.0.0.4/24`
- Gateway: `10.0.0.1`
- DHCP Scope: `10.0.0.50 – 10.0.0.100`

---

## What’s Included in This Repo
- `Networking lab4 report 2.0.docx` — full lab report with steps + evidence

> Note: Screenshots and command outputs are embedded inside the report document.

---

## Verification / Evidence Checklist
Below are the key validations performed during the lab:

### 1) Network + IP Configuration
- Confirm DC1 uses a static IP (`ipconfig /all`)
- Confirm client receives correct IP settings (DHCP / DNS)

### 2) DNS Resolution
- Validate domain name resolution:
  - `nslookup dc1.myclass.local`
  - `nslookup myclass.local`
- Confirm the client can locate the domain controller

### 3) DHCP Scope + Leases
- Create DHCP scope
- Verify leases are being assigned to client systems

### 4) Domain Join
- Join LAB-PC1 to `myclass.local`
- Log in with a domain user account

### 5) IIS Web Server
- Configure IIS and deploy `index.html`
- Verify the website loads from the server (browser test)

### 6) Group Policy
- Link a GPO to the appropriate OU
- Validate policy application:
  - `gpresult /r`
  - visible restriction (e.g., Control Panel blocked / wallpaper applied)

---

## Commands Used (Quick Reference)
```bash
ipconfig /all
ping <ip>
nslookup <name>
gpupdate /force
gpresult /r

```

## What I Learned
- Importance of DNS in Active Directory environments
- DHCP/DNS interaction in domain networks
- Troubleshooting domain join failures
- IIS configuration and default document handling
- Group Policy scope, linking, and enforcement
- Real-world Windows server administration practices

