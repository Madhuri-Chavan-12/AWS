# Security Groups (SG)

- Acts as a virtual firewall for EC2 and ENIs

- Stateful
→ If inbound traffic is allowed, the response is automatically allowed (no outbound rule needed)

- Rules are allow-only
❌ No explicit deny rules

- Works at instance / ENI level

- Inbound rules: control incoming traffic

- Outbound rules: control outgoing traffic

- Evaluated after NACL

- Rules are evaluated as a whole (no rule order priority)

- Supports referencing other Security Groups

- Default SG allows:

    1. All outbound traffic

    2. Inbound traffic only from same SG

- Changes apply immediately

- Used for fine-grained access control

---

# Network ACL (NACL)

- Acts as a firewall for subnets

- Stateless
→ You must explicitly allow inbound and outbound traffic

- Supports both allow and deny rules

- Works at subnet level

- Rules are evaluated in numbered order (lowest first)

- Default NACL allows all traffic

- Custom NACL denies all traffic by default

- Applied before Security Groups

- Changes apply immediately

- Used for broad network-level protection

---
## Security Group vs NACL (Comparison Table)  
| Feature            | Security Group        | Network ACL           |
|--------------------|-----------------------|-----------------------|
| **Level**              | Instance / ENI        | Subnet                |
| **Type**               | Stateful              | Stateless             |
| **Rules**              | Allow only            | Allow & Deny          |
| **Rule Order**         | Not ordered           | Ordered (rule number) |
| **Inbound + Outbound** | Response auto-allowed | Must allow both       |
| **Default Behavior**   | Allow outbound        | Allow all (default)   |
| **Scope**              | Fine-grained          | Broad                 |
| **Reference other SG** | ✅ Yes                | ❌ No                 |
| **Applied**            | After NACL            | Before SG             |
| **Use Case**           | App-level security    | Network-level control |

---
[Diagram Resources](https://www.educative.io/answers/differences-between-aws-security-group-nacl-and-iam)

<img width="725" height="536" alt="image" src="https://github.com/user-attachments/assets/6ac96d54-13aa-40a8-aeb2-d43f027709a7" />

---
<img width="622" height="531" alt="image" src="https://github.com/user-attachments/assets/c1ba9106-7678-4977-b4f5-4aca5b83e626" />


