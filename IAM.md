### IAM

- Identity and Access Management
- Global service
- Root account created by default
  - should NOT be used or shared
  - use it to create users -> can be grouped
- users/groups can be assigned policies (JSON)
  - define the permissions of users
  - don't give more perms than a users needs -> "Principle of Least Privilege"

### Policy Structure

- `Version`: policy language version
  - always include "2012-10-17"
- `Id`: optional identifier
- `Statement`: required, one or more
  - `Sid`: optional identifier
  - `Effect`: Allow or Deny
  - `Principal`: account/user/role to apply to
  - `Action`: list of actions allowed/denied
  - `Resource`: list of resources actions applied to
  - `Condition`: optional, when the policy applies

### IAM ROles

- Set up like users
- used by AWS services to do stuff on my behalf

### IAM Best Practices

- don't use root account except for setup
- one physical user = one aws user
- put users in groups, assign perms to groups
- create a strong password policy
- use access keys for programatic access
- audit perms using IAM Credentials Report and IAM Access Advisor

### Shared Responsibility Model

**AWS**

- infrastructure (global network security)
- configuration and vulnerability analysis
- compliance validation

**You**

- users/groups/roles/policies management and monitoring
- enable MFA on all accounts
- rotate all your keys often
- use IAM tools to apply appropriate permissions
- analyze access patters and review permissions
