# Linux Privilege Escalation

Practical resources, guides, checklists, exploit research, enumeration tools, capabilities, kernel research, and shell references for Linux local privilege escalation.

> Use these resources only on systems you own or are explicitly authorized to test.

This repository is intended as a **practical Linux privilege-escalation reference**, rather than a Linux security theory repository.

The main areas are:

* Enumeration
* Sudo
* SUID / SGID
* Linux capabilities
* Cron jobs
* Services
* Writable files and directories
* Credentials
* Environment / PATH
* Containers
* Kernel vulnerabilities
* Exploit research
* Automated enumeration
* Shell and TTY references

---

## 1. Learn Linux Privilege Escalation

### Comprehensive Guides

* **g0tmi1k - Basic Linux Privilege Escalation**
  https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation

* **PayloadsAllTheThings - Linux Privilege Escalation**
  https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md

* **Sushant 747 - Linux Privilege Escalation Guide**
  https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_-_linux.html

* **HackTricks - Linux Privilege Escalation**
  https://hacktricks.wiki/en/linux-hardening/linux-basics/linux-privilege-escalation/index.html

* **InternalAllTheThings - Linux Privilege Escalation**
  https://swisskyrepo.github.io/InternalAllTheThings/redteam/escalation/linux-privilege-escalation

### Checklists

* **HackTricks - Linux Privilege Escalation Checklist**
  https://hacktricks.wiki/en/linux-hardening/main-system-information/linux-privilege-escalation-checklist.html

---

## 2. Linux Capabilities

Linux capabilities are a distinct privilege-escalation area and deserve their own section.

* **Linux Privilege Escalation Using Capabilities**
  https://www.hackingarticles.in/linux-privilege-escalation-using-capabilities/

* **Linux Capabilities Privilege Escalation - OpenSSL / SELinux**
  https://medium.com/@int0x33/day-44-linux-capabilities-privilege-escalation-via-openssl-with-selinux-enabled-and-enforced-74d2bec02099

* **SUID vs Capabilities**
  https://mn3m.info/posts/suid-vs-capabilities/

### Useful command

```bash
getcap -r / 2>/dev/null
```

---

## 3. Kernel & Exploit Research

### Exploit Databases

* **Exploit-DB**
  https://www.exploit-db.com/

* **SearchSploit**

```bash
searchsploit <software> <version>
```

Example:

```bash
searchsploit samba 2.2.1a
```

### Kernel Exploits

* **Kernel Exploits - lucyoa**
  https://github.com/lucyoa/kernel-exploits

* **OS Kernel - Reference**
  https://en.wikipedia.org/wiki/Kernel_(operating_system)

### Search Operators

Example:

```bash
firefox --search "Linux <software> <version> site:exploit-db.com"
```

Use version-specific searches when researching a suspected vulnerable component.

---

## 4. GTFOBins

* **GTFOBins**
  https://gtfobins.org/

GTFOBins is a practical reference for Unix/Linux binaries that can potentially be abused in security testing.

Particularly useful areas include:

* SUID
* `sudo`
* Capabilities
* Shell escapes
* File read/write
* Command execution

When using a GTFOBins entry, verify that its prerequisites actually exist on the target.

---

## 5. Automated Linux Enumeration

### LinPEAS

* **PEASS-ng - LinPEAS**
  https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS

### LinEnum

* **LinEnum**
  https://github.com/rebootuser/LinEnum

### Linux Exploit Suggester

* **Linux Exploit Suggester**
  https://github.com/The-Z-Labs/linux-exploit-suggester

Status: Updated

### Linux Priv Checker

* **Linux Priv Checker**
  https://github.com/sleventyeleven/linuxprivchecker

### Unix Privilege Escalation Check

* **unix-privesc-check**
  https://github.com/pentestmonkey/unix-privesc-check

### Enumeration Workflow

```text
Automated Enumeration
        ↓
Identify Interesting Finding
        ↓
Manual Validation
        ↓
Confirm Permissions / Configuration
        ↓
Research Applicable Technique
        ↓
Controlled Exploitation
        ↓
Verify Privileges
```

> Automated enumeration should produce leads, not replace manual validation.

---

## 6. Reverse Shells & Payloads

These resources are not Linux privilege-escalation techniques themselves, but are useful when obtaining or maintaining a shell during authorized testing.

### Reverse Shell References

* **InternalAllTheThings - Reverse Shell Cheat Sheet**
  https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet

* **PentestMonkey - Reverse Shell Cheat Sheet**
  https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

* **Kali Linux - Web Shells**

```text
/usr/share/webshells/
```

### PHP Reverse Shell

* **PentestMonkey - PHP Reverse Shell**
  https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php

### Meterpreter / Msfvenom

* **Msfvenom / Meterpreter Cheat Sheet**
  https://nitesculucian.github.io/2018/07/25/msfvenom-cheat-sheet/

### PowerShell

* **HackTricks - Basic PowerShell for Pentesters**
  https://hacktricks.wiki/en/windows-hardening/basic-powershell-for-pentesters/index.html#download--execute

> The PowerShell resource is cross-platform/offensive tooling material rather than Linux-specific PrivEsc.

---

## 7. Reverse Shell Customization

* **RevShells**
  https://www.revshells.com/

Useful for generating and customizing shell commands for authorized testing environments.

---

## 8. Shell Upgrade / TTY

After obtaining a limited shell, an interactive TTY can make enumeration and administration considerably easier.

* **Zachary Eller - Spawning a TTY Shell**
  https://wiki.zacheller.dev/pentest/privilege-escalation/spawning-a-tty-shell

Common concepts covered by TTY resources include:

```text
Limited shell
    ↓
TTY upgrade
    ↓
Interactive shell
    ↓
Improved enumeration
    ↓
Privilege-escalation research
```

---

## 9. Quick Reference

### Basic Enumeration

```bash
id
whoami
hostname
uname -a
cat /etc/os-release
sudo -l
```

### Users & Groups

```bash
cat /etc/passwd
cat /etc/group
id
groups
```

### SUID

```bash
find / -perm -4000 -type f 2>/dev/null
```

### SGID

```bash
find / -perm -2000 -type f 2>/dev/null
```

### Capabilities

```bash
getcap -r / 2>/dev/null
```

### Cron

```bash
cat /etc/crontab
ls -la /etc/cron.*
```

### Processes

```bash
ps aux
ps -ef
```

### Network

```bash
ip addr
ip route
ss -tulpn
```

### Writable Files / Directories

```bash
find / -writable -type f 2>/dev/null
find / -writable -type d 2>/dev/null
```

### Sudo

```bash
sudo -l
```

### Environment

```bash
env
printenv
echo $PATH
```

---

## 10. Main Linux PrivEsc Workflow

```text
Initial Shell
      ↓
Identify User / Groups
      ↓
OS & Kernel Enumeration
      ↓
Sudo Permissions
      ↓
SUID / SGID
      ↓
Linux Capabilities
      ↓
Cron Jobs
      ↓
Services
      ↓
Writable Files / Directories
      ↓
PATH / Environment
      ↓
Credentials / Configuration
      ↓
Containers / Virtualization
      ↓
Kernel / Exploit Research
      ↓
Manual Validation
      ↓
Privilege Escalation
```

---

## Resource Status

| Resource                | Category               | Status             |
| ----------------------- | ---------------------- | ------------------ |
| g0tmi1k                 | PrivEsc Guide          | Reference          |
| PayloadsAllTheThings    | PrivEsc Methodology    | Reference          |
| HackTricks              | PrivEsc Methodology    | Reference          |
| InternalAllTheThings    | PrivEsc Methodology    | Reference          |
| Sushant 747             | PrivEsc Guide          | Reference          |
| LinPEAS                 | Enumeration            | Active             |
| LinEnum                 | Enumeration            | Reference          |
| Linux Exploit Suggester | Exploit Research       | Updated            |
| Linux Priv Checker      | Enumeration            | Legacy             |
| unix-privesc-check      | Enumeration            | Reference          |
| GTFOBins                | Binary Abuse Reference | Active             |
| Kernel Exploits         | Exploit Research       | Reference          |
| RevShells               | Shell Generation       | Reference          |
| UACME                   | -                      | Not Linux-specific |

