# Threat Modeling

## 1. What is threat modeling?

Threat modeling defines and describes the threats thoroughly in order to communicate throughout the development team. In addition, the mitigation methods can be recorded, too.

## 2. How to conduct?

- Begin as a team effort: "multiple team members with different levels of experience and expertise examine a design with respect to where it can be attacked."
- The data flows through the application can help identify the threats.
- Pay attention to the following areas:
  - The application as a whole.
  - Security and privacy features.
  - Features whose failures have security or privacy implications.
  - Features that **cross trust boundaries**.

## 3. STRIDE: where data crosses trust boundaries

The point where data crosses trust boundaries is where we should examine the threats closely, using **STRIDE**:
- **S**: Spoofing
- **T**: Tampering
- **R**: Repudiation
- **I**: Information disclosure
- **D**: Denial of service
- **E**: Elevation of privilege

## 4. Tool: threat tree

Per [1]:

> Threat trees are a graphical representation of the elements that **must exist** for a threat to be realized. Threat trees present a threat in terms of a logical combination of elements, using ANDs and ORs to show the relationships between the required elements. This assists the development team, for if two elements are required, `A AND B`, then the blocking of either A or B will mitigate the threat.

## 5. In development process

Per [1], threat modeling should begin at the start of the project and continues throughout the development effort.

## References

- [1] [FUR-CSSLP] Chapter 4: Software Development Methodologies
