# Trust Boundary

## 1. What is a trust boundary?

As [1] says, a **trust boundary**

> ... describes a boundary where program data or execution changes its level of "trust," or where two [principals](https://en.wikipedia.org/wiki/Principal_(computer_security)) with different capabilities exchange data or commands.

[2] uses some simple, everyday examples to illustrate the concept of trust boundary:

> ... we put locks on the front doors of our houses or office buildings, but not on every internal door within them, ..., or that we have to enter a password to log on to our computer, but not re-enter it every time we perform a different action whilst using it.
>
> ...
>
> A nearly universal example of trust boundaries is the case of the basic separation of the public internet from the internal corporate network at the physical and logical levels using a firewall and router. In a very simple configuration, traffic within the internal network may transit freely across the network, but traffic sourced from the public internet is restricted or prevented from entering the network.

We can connect the examples in [2] with the explanation in [1]:

- In the example of locks, the people outside the front doors are the principals that are not supposed to be trusted; people who have the right keys and thus can enter the front doors become trusted so they automatically get the permissions to open every door. In the same scenarios, the mail packages that are outside the front doors are the "data" that are not supposed to be trusted; once the mail packages are examined and allowed to enter the building, they become trusted.
  - Therefore, if a mail package outside the door is not carefully examined and allowed into the building, this package can be potentially dangerous. This is a case of "trust boundary violation".
- In the example of internet and intranet, the data senders outside the intranet are not supposed to be trusted. The data they send must be verified before allowed into the intranet. Once the data is verified and allowed into the intranet, the data can be exchanged freely. The data providers outside the intranet and the data consumers inside the intranet are principals with different capabilities: the outsiders typically can't change the internal system while the insiders typically can.

## 2. What is trust boundary violation?

> A trust boundary can be thought of as line drawn through a program. On one side of the line, data is untrusted. On the other side of the line, data is assumed to be trustworthy. The purpose of **validation** logic is to allow data to safely cross the trust boundary - to move from untrusted to trusted. A **trust boundary violation** occurs when a program blurs the line between what is trusted and what is untrusted. By **combining trusted and untrusted data in the same data structure**, it becomes easier for programmers to **mistakenly trust un-validated** data.

## 3. Other examples

An SQL injection attack [4] is an example of data crossing trust boundaries without proper validation:
- The boundary of the software system is a trust boundary in this case.
- The users who are outside the software system (thus outside the trust boundary) are not supposed to be trusted. They can enter malicious data intentionally or unintentionally. They don't have the permissions to change the internal data states, either.
- The code that runs inside the software system (thus inside the trust boundary) has the permissions to change the internal data states so the code has "higher privilege" than the users outside.
- If the software system doesn't appropriately validate the data that the users enter, it gives the users a chance to perform the SQL injection attacks: the un-validated data from the outside of the system is mistakenly trusted by the code inside the system and is used to change the data states, thus potentially cause various harm.

## References

- [1] [Wikipedia: Trust boundary](https://en.wikipedia.org/wiki/Trust_boundary)
- [2] [AppCheck: What is a trust boundary and how can I apply the principle to improve security?](https://appcheck-ng.com/what-is-a-trust-boundary-and-how-can-i-apply-the-principle-to-improve-security)
- [3] [CWE-501: Trust Boundary Violation](https://cwe.mitre.org/data/definitions/501.html)
- [4] [OWASP: SQL Injection](https://owasp.org/www-community/attacks/SQL_Injection)
