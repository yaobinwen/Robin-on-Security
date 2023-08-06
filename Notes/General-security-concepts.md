# General Security Concepts

The general security concepts include:
- CIA:
  - Confidentiality
  - Integrity
  - Availability
- AAA:
  - Authentication
  - Authorization
  - Auditing
- Non-repudiation

## 1. Confidentiality

Confidentiality means to prevent the disclosure of information to unauthorized parties. (**"Keep secrets secret."**)

Methods of implementation:

| Methods/Data states | At rest | In transit | In use |
|:-------------------:|:-------:|:----------:|:------:|
| **Access control**  | Yes     |            | Yes    |
| **Encryption**      |         | Yes        |        |

## 2. Integrity

Integrity means to protect the data from unauthorized alteration.

This usually requires finer-grained control of access: a user may be authorized to view information but not change or delete it.

Methods of implementation: **hashing**

## 3. Availability

Availability means when the system needs to be accessed by the authorized parties, it must be accessible to the authorized parties.
- But not all inaccessibility is equally damaging. For example, temporary unavailability of Twitter may not be an issue at all; but unavailability to the industrial plant controlling system or even the military defense system may become a big problem.
- When designing a system, the challenge is to determine th appropriate level of availability.

## 4. Authentication

Authentication is the process of determining the identity of a user. (**Prove you are who you claim to be.**)

Three general methods are used to prove the identity of a user:
- Something users know (e.g., passwords).
- Something users have (e.g., SSH private keys).
- Something users are (e.g., biometrics such as fingerprints or iris pattern).

Two more methods:
- What users do (e.g., dynamic biometrics such as typing patterns or gait).
- Where users are (i.e., actual physical location).

Whenever possible, it is best to leave authentication to established systems.

## 5. Authorization

Authorization is the process of applying access control rules to a user process and determining whether it can access an object.

Authorization involves three elements:
- Requestor (also called subject): the user process that requests to access an object.
- Object: the thing to be accessed, e.g., a file, a program, a network socket.
- Access level: the access operation to be done, e.g., read, write, create, delete, grant access rights to other subjects.

## 6. Accounting (Auditing)

Accounting (auditing) measures whether the system is actually operated as planned.
- Auditing is typically done by logging the key activities of a system so the management can review what happened at a later point in time.
- Auditing logs what actually happens in the system; management can use the logs to measure whether the planned activities were effective, and make correction if not.
- Auditing itself does not create security; it is through the active use of the information that security functionality can be enabled and enhanced.
- Auditing takes resources by itself, so by default it's typically set to log at the minimal level. The key security decision is **the extent and depth of audit log creation**.

A key element in audit logs is the employment of a **monitoring, detection, and response process**. Think about [Prometheus](https://prometheus.io/). Without mechanisms or processes to "trigger" alerts or notifications to admins based on specific logged events, the value of logging is diminished or isolated to a post-incident resource instead of contributing to an **alerting or incident prevention resource**.

## 7. Non-repudiation

Non-repudiation prevents a subject (may or may not be a user) from denying a previous action with an object in a system.

When authentication, authorization, and auditing are properly configured, the ability to prevent repudiation by a specific subject with respect to an action and an object is ensured.
