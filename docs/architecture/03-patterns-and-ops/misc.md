# Misc

## Distributed Communications Failure

> Failure is always an option

We have 4 option to handle distributed exceptions.

- Ignore
	- Swallow exceptions
- Retry
	- How many times?
	- Ensure no duplication (-> idempotent)
- Undo
	- Does a logical undo exist?
	- What do we do if Undo fails?
- Coordination
	- Two-Phase Commit (Prepare with all involved resources -> Commit)
	- Distributed transaction (usually doesn't work with web APIs)
	- ❌Costly
4. Communicator (Two phase commit, )

For each case and each possible failure (call to XY failed, message to service bus could not be published) we need to consider the 4 options and choose the best.

## Metrics

### Hotspot for Code Churn vs (Cyclomatic or Cognitive) Complexity

- Many code changes with high complexity