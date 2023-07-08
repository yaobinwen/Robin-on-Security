# Threat Modeling

## 1. What is threat modeling?

Threat modeling:
- Defines (i.e., identifies) and documents all the threats to the system.
- Communicates the threats throughout the development team.
- Records the mitigation methods.

## 2. When to conduct?

Threat modeling begins early in the development process and goes through the entire development process.

## 3. How to conduct?

Threat modeling is a **team effort**: "multiple team members with different levels of experience and expertise examine a design with respect to where it can be attacked." [1]

Threat modeling can be done in the following sequence:
- 1). Identify security objectives.
- 2). System decomposition.
- 3). Threat identification.
- 4). Mitigation analysis.
- 5). Threat model validation.

### 3.1 Identify security objectives

The security objectives can come from a number sources such as
- legal
- contractual
- corporate standards and objectives

It is a **mistake** to leave the decision of what data to protect and how to protect it up to the development team.

The point is: the **entire team** instead of just the development team should **all** care about the security objectives.

### 3.2 System decomposition

In order to fulfill the security objectives, the designers must ensure the system design can cover the security objectives. The system design thus needs to be decomposed into pieces for review, to make sure all the security objectives are covered.

Because the target of security is typically the data that flows through the system, the best tool to decompose the system is thus the **data flow diagrams** (DFDs).

The DFDs must cover all of the following:
- The data processing **processes**, i.e., how the data is transformed from one state to another state.
- Data **stores**, i.e., where the data is stored.
- Data **flows**, i.e., the paths the data flows from one data store to another data store.

In large, complex systems, breaking down the DFDs into **scenario-based pieces** may make the work easier.

**Note** that this step only decomposes the system and does not identify the threats yet. The threat identification is the next step.

### 3.3 Threat identification

Use the **STRIDE** method (see below) anywhere you want to understand the security implications.

Special attention should be given to [**trust boundaries**](../Notes/Trust-boundary.md) where data crosses from one zone of trust to another. When data crosses trust boundaries, they must be validated appropriately before any use. A "trust boundary violation" is a source of vulnerabilities.

**Avoid becoming distracted by things that the application cannot control**. For example, if the system administrator decides to violate the system trust, this is an operating system issue, not an application issue. Another example is "someone steals the hard drive". The application cannot control the safety of the hard drive because that is an IT management issue of the organization. The only thing that the application can do is encrypt the data that's stored on the hard drive, but protecting the hard drive from being stolen is outside the scope of the application.

### 3.4 Mitigation analysis

#### 3.4.1 Mitigation methods

Each threat requires mitigation of one of the following types:
- 1). Redesign to eliminate vulnerability: If possible, this is the **best option** because it removes the risk.
- 2). Apply a standard mitigation: This is the **next best option** because:
  - The standard mitigation methods (such as ACLs) are well understood and known to be effective.
  - "They will apply across a large number of specific vulnerability points, making them an economical choice."
- 3). Invent a new mitigation: This method itself is risky because the method was not proven effective before; it is more costly because it didn't exist and requires development effort.
- 4). Accept the vulnerability: The least desired option but may be the only option in some cases.

#### 3.4.2 Threat tree model: understand how an attack happens

Use the [**threat tree model**](../Notes/Threat-tree-model.md) to understand how an attack can become effective in the system so to understand the best option to block it.

#### 3.4.3 Prioritize the threats

Not all the threats are the same. Some are more serious than others. Therefore, it makes sense to prioritize the threats and deal with them in the order of from the higher to the lower priorities.

There are two common methods to prioritize the threats:
- Probability + impact
- DREAD

**Probability** and **impact** work as follows:
- 1). Define probability:
  - High = 3 (for example)
  - Medium = 2
  - Low = 1
- 2). Define impact:
  - High = 3 (for example)
  - Medium = 2
  - Low = 1
- 3). Threat score = $probability \times impact \in \{1, 2, 3, \ldots, 8, 9\}$
- 4). Deal with the threats with the higher scores first, then lower scores.

**DREAD** stand for:
- **D**: Damage potential (impact)
- **R**: Reproducibility (probability)
- **E**: Exploitability (probability)
- **A**: Affected users (impact)
- **D**: Discoverability (probability)

Assign a value from `0` (nothing), to `5` (moderate), to `10` (severe) for each element. Sum them and divide by 5, which will yield a score from 0 to 10.

An alternative method is to assume `D` always be `10` and analyze the other factors.

### 3.5 Threat model validation

As the software development process moves through the phases of the SDL, at gates between the phases, the current version of the threat model should be validated to assess the quality of the threats and mitigation:
- For threats, it is important to ensure that they describe the attack and the impact in detail relevant to the context of the application.
- For mitigations, it is important that they are associated with a threat and are completely described in terms relevant to the context of the application.

## 4. Other aspects

The following items should be documented in the threat model:
- The **dependencies** that the application's security functions rely on, because those dependencies themselves can become risks.
- The **assumptions** that are made as part of the development process, because one day the assumptions may no longer hold.

## 5. STRIDE

The point where data crosses trust boundaries is where we should examine the threats closely, using **STRIDE**:
- **S**: Spoofing
- **T**: Tampering
- **R**: Repudiation
- **I**: Information disclosure
- **D**: Denial of service
- **E**: Elevation of privilege

## 6. In development process

Per [1], threat modeling should begin at the start of the project and continues throughout the development effort.

## References

- [1] [FUR-CSSLP] Chapter 4: Software Development Methodologies
- [2] [FUR-CSSLP] Chapter 8: Design Processes
