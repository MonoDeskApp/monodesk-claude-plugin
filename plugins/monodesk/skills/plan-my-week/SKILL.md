---
name: plan-my-week
description: Plan the user's week from their MonoDesk tasks and schedule. Use when the user asks what to work on this week, wants to prioritise or order their tasks, asks "what's on my plate", or wants a weekly plan built from MonoDesk.
---

# Plan my week

Build an ordered plan for the week from the user's open MonoDesk tasks and schedule.

## Steps

1. Call `getMyProfile` to confirm the current workspace. Tell the user which workspace you are reading if they belong to more than one.
2. Call `getSchedule` for the coming week. It always covers the connected user, so pass no user ID.
3. Call `listTasks` with `assigneeId: "me"` to get the user's open tasks. Leave out the project filter so tasks from every project come back.
4. If the user mentions a client or project by name, use `find` to turn it into an ID instead of calling several list tools.
5. Order the tasks. Put first anything overdue, then anything due this week, then work that blocks other people. Spread the rest over days with free time in the schedule. Keep each day realistic: if the schedule shows a full day, put less on it.
6. Show the plan as a short list per day. For each task give its name, project, due date if it has one, and the `url` from the tool result so the user can open it. Say which tasks you left out and why.

## Changing tasks

Only change tasks if the user asks, for example to set due dates or reorder a board to match the plan.

- Show the exact changes first: each task, the field, the old value and the new value. Ask for a yes before writing.
- Use `batchUpdateTasks` for more than one task. Use `updateTask` only for a single task.
- After writing, link each changed task with the `url` from the response.

## Notes

- All tools act in the user's current workspace, which is shared with their other connected AI clients. Do not switch workspace without asking.
- Do not invent tasks. If the week looks empty, say so and ask whether to plan from a client or project instead.
