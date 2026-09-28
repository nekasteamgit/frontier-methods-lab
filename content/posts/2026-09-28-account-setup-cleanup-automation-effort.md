# Account for Setup and Cleanup When Estimating Automation Effort

A browser workflow can finish its visible task in seconds and still consume a meaningful block of operator time. Someone may need to restore an account, prepare test records, dismiss a prompt, or return a shared environment to a known state. If an estimate counts only the time between the first click and the final result, it describes runtime—not the effort required to operate the workflow.

## Separate the phases of a run

A small pilot does not need a large accounting system. It does need consistent boundaries. Record the work in a few phases so that a fast interaction is not confused with a low-maintenance process.

| Phase | Examples to include |
| --- | --- |
| Preparation | Sign-in, permissions, test data, and environment reset |
| Active run | Time when the workflow is executing its intended task |
| Waiting | Page loads, queued work, and external responses |
| Recovery | Diagnosis, safe retry, or manual completion after a failure |
| Cleanup | Removing test data and restoring the next known starting state |

The categories can be adjusted to the task, but they should stay stable across the runs being compared. Otherwise, one run may count a manual reset while another quietly treats it as free.

## Keep operator work visible

A person waiting for a page is not always doing active work, but that interval still affects how long the task takes to finish. Record elapsed time separately from hands-on time. This helps answer two different questions: how long until the result is ready, and how much operator attention does the process require?

The distinction matters when a workflow is unattended for part of a run but needs supervision at a few critical steps. It also prevents a long wait from being misreported as either continuous labor or negligible effort.

## Use representative conditions

Setup and cleanup vary with account state, data volume, and the page being tested. A single unusually clean run can make a pilot look easier to operate than it is. Capture the starting conditions and repeat the same small task under ordinary conditions before turning the result into an estimate.

When a run fails, record the recovery work rather than folding it into the active runtime. That makes it easier to see whether the problem came from a transient wait, a changed interface, or an incomplete reset. The purpose is not to assign blame; it is to identify which part of the operating process needs attention.

## Make the estimate useful for a decision

A short run record can include the task, starting state, active runtime, waiting time, hands-on preparation, recovery, cleanup, and final outcome. A few consistent entries are more useful than a precise-looking total assembled from different definitions.

The resulting estimate should say what it includes and which conditions it assumes. That gives the next operator a realistic picture of the work around the automation—not just the part that happens inside the browser.
