# Strip Miner Loop

This repo is just one loop: **Strip Miner**.

The loop itself is in [`LOOP.md`](./LOOP.md). It is the compact, submission-ready version.

## What This Is

Strip Miner asks a coding agent to look through your past coding-agent sessions and find the workflows you keep doing successfully.

It is not looking for what sounded impressive. It is looking for patterns that actually worked: tasks that ended in accepted work, verified output, shipped changes, or some other real sign of success.

When it finds a strong pattern, it turns that pattern into a reusable local loop file.

## Why It Exists

Agent histories are noisy. A lot of sessions contain partial work, confident summaries, retries, dead ends, copied prompts, tool output, subagent chatter, or tasks that only looked complete.

Strip Miner is meant to sort that out carefully.

It tries to answer:

- What workflows have really worked more than once?
- Which sessions are actually the same task continued later?
- Which patterns failed, needed rescue, or should not be reused?
- What should become a reusable loop, and what should stay blocked or unknown?

## Does It Run Forever?

No. The loop is a prompt, not a background service.

It may run for a very long time. It may also stop pretty quickly. That depends on how much agent history is available, how much of it is new, and whether each batch is still finding useful patterns, blockers, or contradictions.

One run should keep working until it reaches a clear pause point: sources are mapped, useful batches have been sampled, candidates and blockers are written down, and resume state is saved. It should not stop just because the agent gets bored. If it stops, it should say why and leave enough state for the next run to continue.

To make it run again later, you need to launch it again yourself or use a separate scheduler/loop runner. Strip Miner saves state so the next run can continue instead of starting over.

## First-Time Notes

Run it in a scratch output folder.

If you are new to loops, keep an eye on it. Check in every few hours, especially if your agent uses paid model calls or paid tools. How often you check depends on how much you are willing to spend and how much local history you asked it to inspect.

Loop responsibly.

Treat the results as private until you inspect them. The loop reads local agent history as evidence, so its output may include local paths, source anchors, and small excerpts from your own work history.

The main rule is simple: three repeated stories are not enough. A workflow only counts when the evidence shows real successful outcomes.

## Part Two

Strip Miner finds candidate loops.

Loop-de-loop is the next step: replaying, hardening, and improving the best candidates after they have been found.

Loop-de-loop is not included in this repo yet. Part two coming soon.

## What To Look For After A Run

Look for:

- candidate loop files,
- an index of found candidates,
- a root-task ledger,
- blocked patterns,
- guardrails learned from repairs,
- deferred work or resume state,
- replay status.

If something is marked `UNKNOWN`, the loop did not have enough evidence.

If something is marked `CANDIDATE-UNREPLAYED`, treat it as promising but not proven yet.
