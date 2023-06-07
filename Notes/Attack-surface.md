# Attack Surface

## 1. What is attack surface?

Per [1]:

> The attack surface of a software environment is the sum of the different points (for ["attack vectors"](https://en.wikipedia.org/wiki/Attack_vector)) where an unauthorized user (the "attacker") can try to enter data to or extract data from an environment.

Note:
- Att"In computer security, an attack vector is a specific path, method, or scenario that can be exploited to break into an IT system, thus compromising its security."

Per [2]:

> The set of points on the boundary of a system, a system element, or an environment where an attacker can try to enter, cause an effect on, or extract data from, that system, system element, or environment.

Per [3]:

> The attack surface of software is the code within the system that can be accessed by unauthorized parties. This is not just the code itself, but can also include a wide rage of resources associated with the code, including user input fields, protocols, interfaces, resource files, and services.

## 2. Listing attack surface elements

One needs a way to enumerate the ways that the software can be accessed by the unauthorized parties. Only after listing all the attack surface elements would one be able to effectively manage them.

### 2.1 Well-known lists

Per [3], here is a published list from Microsoft (but [3] doesn't give the source link of the list):

- Open sockets
- Open remote procedure call (RPC) endpoints
- Open named pipes
- Services
- Services running by default
- Services running as SYSTEM
- Active web handlers (ASP files, HTR files, and so on)
- Active Internet Server Application Programming Interface (ISAPI) filters
- Dynamic webpages (ASP and such)
- Executable virtual directories
- Enabled accounts
- Enabled accounts in admin group
- Null sessions to pipes and shares
- Guest account enabled
- Weak ACLs in the file system
- Weak ACLs in the registry
- Weak ACLs on shares

### 2.2 History of known vulnerabilities in previous development

The second source is the history of known vulnerabilities associated with previous development. Per [3], "Determining the root cause of old vulnerabilities is good for fixing them and preventing future occurrences, and it is also valuable information that can be used in determining the attack surface."

## 3. Evaluation

Attack surface can be measured in two ways:
- Unweighted (i.e., sheer) number of how many such elements there are.
- Weighted number of how many such elements there are.

Bottom line: **The larger the number is, the greater the risk.**

## 4. Code quality

**The presence of attack surface does not reflect the code quality.** It does not mean there are flaws. Attack surface is inevitable in software and merely measures how many items can be used by attackers for attack.

However, **the success of attacks means the code has flaws** that can be exploited by the attackers.

## References

- [1] [Wikipedia: Attack surface](https://en.wikipedia.org/wiki/Attack_surface)
- [2] [NIST: Computer Security Resource Center: attack surface](https://csrc.nist.gov/glossary/term/attack_surface)
- [3] [CSSLP Certification Exam Guide (2e)](https://www.amazon.com/CSSLP-Certification-All-Guide-Second/dp/1260441687)
