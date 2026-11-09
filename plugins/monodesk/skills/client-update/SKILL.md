---
name: client-update
description: Draft a weekly progress update for a client from their MonoDesk projects. Use when the user wants to write a client update, status report, progress email or weekly summary for a client, or asks what got done for a client this week.
---

# Client update

Draft a progress update for one client, based on what happened in MonoDesk over the period the user names. Default to the last seven days.

## Steps

1. Resolve the client with `find`. If more than one client matches, ask which one.
2. Call `listProjects` for that client to get its active projects.
3. For each project, call `listTasks` to see open and recently completed work, and `listTaskActivity` for what moved during the period.
4. Call `listComments` on the tasks that changed, to pick up decisions, questions and anything waiting on the client.
5. Call `listTimeLogs` for the period if the user wants hours included. It covers the connected user only, so say so if other team members also worked on the client.
6. Write the draft:
   - A one-line summary of where things stand.
   - Done this period, grouped by project.
   - In progress and what comes next.
   - Anything needed from the client, with dates.
   - Hours logged, only if the user asked for them.
   Keep it short and in plain language. Leave out internal notes, task IDs and comments that were clearly not meant for the client.
7. Show the draft and ask what to change. The update is for the user to send; this skill does not send it.

## Saving the update

If the user wants the update kept in MonoDesk, offer to save it as a project note with `createProjectNote`. Show the note text and the project it will go on, and wait for a yes before writing. Link the user to the project with its `url`.

## Notes

- All tools act in the user's current workspace.
- Report only what the data shows. If a project had no activity, say that rather than filling the gap.
