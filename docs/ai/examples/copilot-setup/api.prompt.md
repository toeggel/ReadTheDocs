
```markdown
---
mode: 'ask'
model: Claude Sonnet 4
description: 'Perform a REST API security review'
---

Perform a REST API security review and provide a TOD list of security issues to address.

- Ensure all endpoints are protected by authentication and authoriuation
- Validate all user inputs and sanitize data
- Implement rate limiting and throttling
- Implement logging and monitoring for security events
  
Return a TODO list in markdown format, grouped by priority and issue type.

```