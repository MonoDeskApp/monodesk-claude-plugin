---
name: log-my-day
description: Turn a description of the user's day into MonoDesk time entries. Use when the user describes what they worked on and wants it logged, asks to fill in their timesheet, or says things like "log my time", "I spent the morning on X" or "record my hours for today".
---

# Log my day

Turn the user's account of their day into time entries on the right MonoDesk tasks.

## Steps

1. Read the description and split it into blocks of work, each with a duration or start and end time, and the task or project it belongs to. Use today's date unless the user gives another.
2. Call `listTimeLogs` for that date to see what is already logged, so you do not log the same work twice. It covers the connected user only.
3. Match each block to a task. Use `find` for named tasks or projects. If a name matches more than one task, ask which. If no task fits, offer to log against a new task and include it in the draft.
4. Show the draft as a table: date, task, project, duration and a short note. Show the day's total and flag anything that overlaps existing entries. Ask for a yes or changes.

## Writing

- After the user says yes, log every entry in one `batchLogTimeEntries` call (up to 100 rows). Pass `projectId` on each row so a task name shared by two projects resolves to the right one.
- Use `logTimeEntry` only when there is exactly one entry. Never call it in a loop.
- If the draft included a new task, create it first with `createTask` (or `batchCreateTasks` for several), then log time against it.
- Report what was logged and link each task with its `url`.

## Notes

- All tools act in the user's current workspace.
- Round to the nearest five minutes unless the user gave exact times.
- If a block has no duration, ask rather than guess.
