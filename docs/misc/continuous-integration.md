---
tags:
  - DevOps
---

# Continuous Integration

Merge to main at least daily. This means, we cannot (always) merge a full feature. This means that, if we now also practice Continuous Development we will eventually end up with **incomplete features in production**. This basically forces us to separate deployment from release. We have those options for that: 

- Dark Launch
	- We deploy it in a *hidden* place. Remember: a user might still access it!
- Branch by abstractions 
	- We create abstractions for existing logic and use the old logic. We then migrate one by one to new logic by simple switch the implementation behind the abstraction. 
- Feature Flags
	- See: [Feature toggling](../architecture/06-tools/tools.md#Feature%20toggling))