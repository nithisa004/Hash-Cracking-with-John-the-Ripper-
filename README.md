# 🔐 Hash Cracking with John the Ripper

## GraySentinel Cyber Defence Research Program

This project was completed as part of the **GraySentinel Cyber Defence Research Program**. It demonstrates password hash analysis and dictionary-based password cracking in an authorized **Metasploitable 2** lab environment.

---

## 🎯 Objectives

* Understand Linux password storage and hashing.
* Extract password hashes from `/etc/shadow`.
* Combine `/etc/passwd` and `/etc/shadow` using `unshadow`.
* Perform dictionary-based password cracking.
* Analyze password security and weak-password risks.

---

## 🛠️ Tools Used

* **Kali Linux**
* **Metasploitable 2**
* **John the Ripper**
* **unshadow**
* **rockyou.txt**
* **SSH **

---

## 🧪 Lab Environment

| Component   | Details          |
| ----------- | ---------------- |
| Attacker    | Kali Linux       |
| Target      | Metasploitable 2 |
| Hash Tool   | John the Ripper  |
| Wordlist    | rockyou.txt      |
| Hash Source | `/etc/shadow`    |

---

## 🔄 Methodology

```text
Metasploitable 2
       │
       ▼
/etc/passwd + /etc/shadow
       │
       ▼
    unshadow
       │
       ▼
 Combined Hash File
       │
       ▼
John the Ripper
       │
       ▼
  rockyou.txt
       │
       ▼
Password Recovery
```

---

## 🚀 Procedure

### 1. Obtain the password files

The password files were obtained from the authorized Metasploitable 2 laboratory machine.

```bash
sudo cp /etc/shadow ~/shadow.txt
sudo cp /etc/passwd ~/passwd.txt
```

The files were then transferred to Kali Linux using SCP.

### 2. Combine the files

```bash
unshadow ~/passwd.txt ~/shadow.txt > ~/unshadow.txt
```

Verify the generated file:

```bash
ls -lh ~/unshadow.txt
```

### 3. Run John the Ripper

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt ~/unshadow.txt
```

### 4. Display recovered passwords

```bash
john --show ~/unshadow.txt
```

---

## 📊 Results

John the Ripper was used to perform a dictionary attack against the recovered password hashes.

| Account      | Hash Type | Result                  |
| ------------ | --------- | ----------------------- |
| Lab accounts | MD5-crypt | Tested with rockyou.txt |

Actual recovered passwords are **not published** in this repository.

---

## 🔐 Security Insights

This project demonstrates how weak passwords can potentially be recovered through dictionary attacks when attackers obtain password hashes.

Strong, unique passwords and modern password-hashing mechanisms are important for reducing password-cracking risks.

---

## ⚠️ Ethical Disclaimer

This project was performed in an **authorized and isolated cybersecurity laboratory environment** using Metasploitable 2.

The techniques demonstrated in this project should only be used on systems for which you have explicit authorization.

---

## 📚 Learning Outcomes

* Linux password-file structure
* Password hashing
* MD5-crypt hash identification
* Dictionary attacks
* John the Ripper
* `unshadow`
* Password security assessment
* Ethical hacking fundamentals

---

### 👩‍💻 Program

**GraySentinel Cyber Defence Research Program**

**Project:** Hash Cracking with John the Ripper
**Focus:** Hash Cracking & Password Security
