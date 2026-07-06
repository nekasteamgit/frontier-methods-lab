# Testing Session Drift Before a Browser Task Starts

Many browser automation failures are blamed on selectors, latency, or flaky retries when the real issue appears earlier: the session has already drifted before the task truly begins.

Session drift is the quiet gap between the state the operator expects and the state the browser actually carries into the next run. A workflow may look logged in, look ready, and still be pointed at the wrong account, locale, or stale permission state.

## Treat preflight as a state check, not a ritual

A useful preflight check does not try to prove that everything is healthy. It only verifies the small states that most often corrupt downstream steps:

1. the active account is the expected one;
2. the entry URL matches the intended environment;
3. consent banners, interstitials, or expired prompts are not masking the page;
4. the first action can still be completed without manual recovery.

If one of these checks fails, the run should not enter the main task loop at all.

## Drift usually hides in reused sessions

Reusable sessions save time, but they also accumulate silent mismatches. A cookie refresh, a redirected dashboard, or a previously dismissed warning can change what the next operator sees.

That is why drift checks should focus on visible state, not only stored credentials. The workflow needs to confirm what the browser has become, not what the automation script assumes it preserved.

## Use a three-signal preflight note

Before each high-value run, a compact preflight note can capture just three signals:

| Signal | What to confirm |
| --- | --- |
| Identity | right account, workspace, or tenant |
| Context | right URL, locale, and page state |
| Permission | action still available without fallback prompt |

This note is small enough to keep, but concrete enough to explain why a run should proceed or stop.

## Stop calling every failed start a selector problem

Teams often spend too long rewriting selectors when the first broken assumption is actually environmental. If a dashboard opens in the wrong workspace, if a previous review banner reappears, or if a stale role strips a button from the page, the selector is only the messenger.

Checking session drift early reduces pointless debugging later.

## Keep the evidence boring and reusable

The best proof for session drift is not a giant log bundle. It is often just:

- one screenshot of the landing state;
- one short note naming the expected account or workspace;
- one confirmation that the first action remained available.

That evidence can be captured in under a minute and reused across many runs.

## A stable run starts before step one

Browser tasks look more reliable when the workflow acknowledges that step zero is real. Preflight is not overhead if it catches the wrong account, wrong context, or wrong permission state before the main task starts.

## Further reading

- [Mana-Sys](https://mana-sys.fr) — another stream of practical analysis on systems, tooling, and AI work in the field.