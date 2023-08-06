# Security Design Principles

The security design principles include:
- Good enough security
- Least privilege
- Defense in depth
- Separate of duties
- Fail safe
- Complete mediation
- Open design
- Economy of mechanism
- Least common mechanism
- Psychological acceptability
- Leverage existing components
- Weakest link
- Single point of failure

## 1. Good enough security

Do not over-engineering the security measures because that can increase the cost.

## 2. Least privilege

The users should be given only the just enough privilege to finish the tasks.

## 3. Defense in depth

If one defense is good, multiple overlapping defenses are better.

For them to be effective, the multiple defenses should be dissimilar in nature (i.e., using different mechanisms).

## 4. Separate of duties

TODO: Learn more about it.

## 5. Fail safe

When a system fails, it should fail to a safe state in which the security attributes (e.g., CIA) are still appropriately maintained.

## 6. Complete mediation

The point is: If the authorization system is circumvented, the damage is limited to immediate requests. So whenever sensitive operations are to be performed, it is important to perform authorization checks.

For example: If a routine is to permit managers to change a key value in a database, then **assuming that the party calling the routine is a manager can result in failures.** Verifying that the party has the requisite authorization as part of the function is an example of complete mediation.

## 7. Open design

Having designs that are open and understandable will prevent activities later in the development process that will weaken or bypass security efforts.

## 8. Economy of mechanism

The point is: The more complex the system is designed to be, the harder for the maintainers to understand the system, so the more likely there are security vulnerabilities and harder to secure the system.

Therefore: **KISS**: Keep it simple, stupid.

## 9. Least common mechanism

The point is: If two components are dissimilar (i.e., working in different mechanisms), when one component is compromised, the other is still likely to be secure.

This principle conflicts with the principle "leverage existing components" because this principle advocates separation while the other one advocates reuse. The designer must determine the correct balance.

## 10. Leverage existing components

The point is: Reusing an existing component can have a few benefits:
- Reduce the development cost.
- If the reused component has been proven robust and secure, reusing it is likely to be the same robust and secure.
- If the reused component is well understood, reusing it can reduce the complexity of the system.

On the other hand, reusing also creates a larger footprint when the reused component does have a failure.

## 11. Psychological acceptability

The point is: To make a security measure truly effective, it must be psychologically acceptable to the users, because when the security measure appears to obstruct the users, the users will always try to work around them to make it more convenient to use.

## 12. Weakest link

The system can only be considered as strong as its weakest link.

Designing a system using the security tenets described in this section will go a long way in preventing local failures from becoming system failures. This limits the effect of the weakest link to local effects.

## 13. Single point of failure

The point is: All points of failures are analyzed and that a single failure does not result in system failure.
