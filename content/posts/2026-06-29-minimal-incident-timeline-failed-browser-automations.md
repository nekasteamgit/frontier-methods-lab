# A Minimal Incident Timeline for Failed Browser Automations

A browser automation run does not need a giant observability stack before it becomes easier to debug.

In many small pilots, the missing piece is simpler: nobody can reconstruct what happened in the two minutes before the run went wrong. A compact incident timeline often explains more than a long wall of retry logs.

## Start with five fixed checkpoints

A small timeline becomes useful when it answers the same questions on every failed run:

- when the run started;
- which target page or task was involved;
- which step first drifted from the expected path;
- what the operator actually saw;
- when the run was stopped or handed off.

These checkpoints are boring on purpose. They reduce the temptation to write a dramatic summary after the fact.

## Capture state changes, not every heartbeat

Teams often log too much of the wrong thing. They store repeated success messages but forget the moment a session changed account, a modal blocked the page, or a selector returned a partial match.

A better incident note favors state changes:

1. page loaded with the expected URL or not;
2. authentication state looked valid or stale;
3. target element was visible, missing, or unstable;
4. the step produced a usable result, a partial result, or no result.

That level of detail is usually enough to separate a timing issue from a structural failure.

## Keep screenshots tied to the timeline

A screenshot folder without timestamps becomes a memory test. A better habit is to capture only the images that correspond to the first visible anomaly and the final state before exit.

Two screenshots with short labels often beat twenty generic captures:

- first unexpected UI state;
- final state before abandonment or manual takeover.

## The smallest useful template fits in one table

A minimal review table can stay compact:

| Time | Step | Observed state | Evidence |
| --- | --- | --- | --- |
| 09:14:03 | Login check | Session reused successfully | screenshot-01 |
| 09:14:18 | Search form submit | Spinner never cleared | network log snippet |
| 09:14:46 | Retry 1 | Same blocked state | screenshot-02 |
| 09:15:02 | Run stopped | Escalated for manual review | operator note |

If a team cannot fill four lines like these, the workflow is usually under-instrumented at the wrong layer.

## Review the first divergence before tuning retries

The timeline matters because it forces attention onto the first divergence, not only the last visible error. That is where weak assumptions usually show up: stale sessions, hidden overlays, changed labels, or pages that loaded in the wrong context.

Retries may still help afterward, but they should come after the workflow can explain its own failure in plain language.

## Further reading

- [Mana-Sys](https://mana-sys.fr) — another stream of direct analysis on practical systems, tooling, and AI.
