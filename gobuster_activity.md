# Gobuster: Brute-Forcing FakeBank's Hidden Pages

In this challenge, I used a command-line tool called **Gobuster** to brute-force FakeBank's website in order to find hidden directories and pages. Gobuster works by taking a list of potential page or directory names and tries accessing each one; if a page exists, it returns a response. This technique is often used by ethical hackers to identify sensitive or overlooked parts of a website that could pose security risks.

## Step 1: Open a Terminal

To begin, I opened the terminal on my machine. The terminal, also known as the command line, allows me to interact directly with the system without a graphical user interface. On my machine, I clicked the **Terminal** icon to open it.

## Step 2: Use Gobuster To Find Hidden Website Pages

Many websites, including banks, can have hidden pages or directories that are not intended to be publicly accessible. These could contain sensitive data or admin controls. For example, FakeBank could have an admin portal for employees to manage transactions. Due to human error or negligence, these pages might not be properly protected, leaving them open for potential attackers.

I used **Gobuster** to find such hidden pages on FakeBank's website. The command I ran in the terminal was:

gobuster -u http://fakebank.thm -w wordlist.txt dir

=====================================================
Gobuster v2.0.1              OJ Reeves (@TheColonial)
=====================================================
[+] Mode         : dir
[+] Url/Domain   : http://fakebank.thm/
[+] Threads      : 10
[+] Wordlist     : wordlist.txt
[+] Status codes : 200,204,301,302,307,403
[+] Timeout      : 10s
=====================================================
2024/05/21 10:04:38 Starting gobuster
=====================================================
/images (Status: 301)
/bank-transfer (Status: 200)
=====================================================
2024/05/21 10:04:44 Finished
=====================================================

In the output above, Gobuster successfully identified a couple of important directories:

/images (Status: 301 - Redirect)
/bank-transfer (Status: 200 - OK, which indicates the page exists and is accessible)

What I Found:
The /bank-transfer page was of particular interest. This appeared to be a hidden admin portal for transferring funds between accounts. I followed the page using the following link:
http://fakebank.thm/bank-transfer

At this point, I had access to a page that allowed me to transfer funds between bank accounts. An attacker could exploit this to move money between accounts without authorization, which is a major security issue.

My Mission:
I was tasked with transferring $2000 from bank account 2276 to my account number 8881. I performed the transfer and, after refreshing my account page, I saw that my balance had been updated to reflect the $2000 I transferred!

Reflection:
This exercise was a great way to practice web application penetration testing techniques, specifically directory brute-forcing. By finding hidden pages like the /bank-transfer page, I was able to exploit a vulnerability and gain unauthorized access to sensitive operations, mimicking what an attacker might do.

As an ethical hacker, my next steps would be to report this vulnerability to the bank (or relevant authority) so they can patch the issue before malicious actors can exploit it.

Conclusion
This challenge taught me how easily hidden pages or vulnerable admin portals can be found using tools like Gobuster. It's important for companies to properly secure their web applications and ensure that sensitive pages are not publicly accessible without proper authorization.

By completing this challenge, I’ve gained a better understanding of how web application vulnerabilities work and the importance of ethical hacking practices in identifying and fixing these issues before they can be exploited.
