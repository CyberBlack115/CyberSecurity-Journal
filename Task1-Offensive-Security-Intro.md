# 🛡️ Room: Offensive Security Intro
**Platform:** TryHackMe
**Date:** Feb 10, 2026
**Topic:** Web Hacking Basics

## 🚀 What I Learned
- **Offensive Security (Red Team):** The process of simulating attacks to find security flaws before malicious hackers do.
- **Defensive Security (Blue Team):** The process of protecting networks and investigating attacks.

## 🛠️ Tools Used
- **Dirbuster (dirb):** A tool used to find hidden files and directories on a website.
- **Command:** `dirb http://fakebank.thm`

## 💻 The Hack
1.  **Reconnaissance:** I used the command line to scan the "FakeBank" website.
2.  **Discovery:** The tool found a hidden page called `/bank-transfer`.
3.  **Exploitation:** I navigated to `http://fakebank.thm/bank-transfer` which bypassed the login screen.
4.  **Action:** Successfully transferred $2000 from the admin account (ID: 8881) to my account.

## 🔑 Key Takeaway
Security isn't just about strong passwords. Developers often leave "hidden" pages accessible. Tools like `dirb` can easily find these if they aren't properly secured.
