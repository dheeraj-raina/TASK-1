# TASK-1: Scanning for Open Ports with Nmap and Understanding Security Risks

## Introduction

This project demonstrates how to use **Nmap** to scan a host for open ports and discusses the potential security risks associated with having FTP (port 21) and HTTP (port 80) open on your server.

---

## Scanning for Open Ports Using Nmap

Nmap is a powerful command-line tool for network discovery and security auditing. To scan a host for open ports, you can use the following command:

```bash
nmap [target-ip]
```

Replace `[target-ip]` with the IP address of the system you want to scan. For example, to scan the most common 1000 ports on a host:

```bash
nmap 192.168.1.10
```

To scan specific ports, such as 21 and 80:

```bash
nmap -p 21,80 192.168.1.10
```

The output will show which ports are open and what services are running on them[1].

---

## Example Output

```
PORT   STATE SERVICE
21/tcp open  ftp
80/tcp open  http
```

---

## Security Risks of Open Ports

### **Port 21/tcp (FTP)**

FTP is a legacy protocol used for file transfers. Having port 21 open can expose your system to several security risks:

- **Plain Text Authentication:** FTP transmits usernames and passwords in clear text, making them easy targets for interception and credential theft[2][5].
- **Anonymous Access:** Poorly configured FTP servers may allow anonymous users, who can upload or download files without authentication, potentially leading to data breaches or malware uploads[2][5].
- **Brute Force Attacks:** Attackers can use automated tools to guess weak or default passwords, gaining unauthorized access[2].
- **Directory Traversal:** Vulnerable FTP servers may allow attackers to access files outside the intended directories, exposing sensitive data[2][5].
- **Buffer Overflow and Remote Code Execution:** Some FTP servers have vulnerabilities that can be exploited to execute arbitrary code or crash the server[2][5].
- **FTP Bounce Attacks:** Attackers can exploit the FTP protocol to scan other hosts or bypass network restrictions[2].

**Mitigation:**  
Use secure alternatives like SFTP (SSH File Transfer Protocol) or FTPS, disable anonymous access, enforce strong authentication, and regularly audit FTP server configurations[2][5].

---

### **Port 80/tcp (HTTP)**

Port 80 is used for unencrypted web traffic. Leaving this port open can introduce several risks:

- **Unencrypted Data Transmission:** All data, including credentials and personal information, is sent in plain text and can be intercepted by attackers[3].
- **Man-in-the-Middle Attacks:** Attackers can intercept HTTP traffic, modify content, or steal sensitive information[3].
- **Lack of Authentication and Integrity:** HTTP does not provide mechanisms to ensure data integrity or authenticate users, making it vulnerable to various attacks[3].
- **Compliance Issues:** Many regulations require encryption for sensitive data; using HTTP may violate these requirements[3].
- **Legacy Application Vulnerabilities:** Older web applications running on HTTP may be more susceptible to known exploits[3].

**Mitigation:**  
Migrate to HTTPS (port 443), which encrypts web traffic, ensuring data confidentiality and integrity. Regularly update web applications and enforce secure coding practices[3].

---

## Conclusion

Scanning your network with Nmap is an essential first step in identifying open ports and potential vulnerabilities. Open ports 21 (FTP) and 80 (HTTP) are commonly targeted by attackers due to their inherent security weaknesses. To reduce risk, use secure alternatives, enforce strong authentication, and keep all services updated and properly configured.

---

**References:**  
- [How to Use Nmap to Scan for Open Ports][1]  
- [Port 21 Vulnerabilities][2]  
- [Why Blocking Port 80 is Essential][3]  
- [Analyzing TCP port 21 FTP vulnerabilities][5]
