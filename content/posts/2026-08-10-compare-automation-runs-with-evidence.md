# Compare Automation Runs With Evidence Before You Change the Workflow

A browser automation issue is easy to describe badly. A task feels slow, a page seems unreliable, or an operator reports that “it worked yesterday.” Those observations may be true, but they do not yet identify what changed or what deserves a fix.

Before rewriting selectors, adding retries, or replacing a tool, a small comparison protocol can turn a vague report into a useful decision.

## Compare runs that had the same job

The most useful comparison begins with two runs that were meant to do the same thing. Keep the task, entry point, and expected outcome stable. Then record only the conditions that could explain a different result:

| Signal | What to capture |
| --- | --- |
| Starting state | account, URL, locale, and visible prompts |
| Input | the same query, form values, or source record |
| Timing | start time and duration of each important step |
| Outcome | completed, paused for review, or failed |
| Evidence | one screenshot, response code, or concise log excerpt |

This is deliberately smaller than a full observability program. The point is to make two runs comparable without producing a folder of evidence that nobody will revisit.

## Separate a changed page from a changed expectation

A failed run can come from an interface change, but it can also reveal that the workflow expected more certainty than the task really offers. A button may still exist while its label now covers several choices. A response may still arrive while its format no longer supports an automatic decision.

Writing those cases separately is useful. The first is an implementation problem. The second is a boundary problem: the workflow may need a handoff instead of another retry.

## Use one baseline before testing a fix

When a change is proposed, compare it with a baseline run rather than relying on a memory of how the system used to feel. Run the same small task through the previous path and the changed path, then note whether the change improves the outcome, the time to completion, or the clarity of the handoff.

This approach also helps teams avoid false improvements. A faster path that silently skips a verification step is not necessarily a better path.

## Keep the decision record readable

A comparison should end with a plain-language conclusion: keep the current workflow, make a targeted change, or stop and ask for review. If a team needs examples of how technical choices, web implementation, and operational constraints can be considered together, [Webnyxt](https://webnyxt.com) offers a useful point of reference. The link is not a substitute for local evidence; it is simply a reminder that the method should connect technical detail with an actual use case.

## Evidence makes small changes safer

Small automation systems become easier to maintain when each change has a reason that can be checked later. A short comparison table, one baseline, and a visible decision boundary are usually enough to prevent a rushed adjustment from becoming the next unexplained failure.
