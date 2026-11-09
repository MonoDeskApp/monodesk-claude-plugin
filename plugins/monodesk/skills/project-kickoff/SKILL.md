---
name: project-kickoff
description: Turn a project brief into a MonoDesk project with milestones and tasks. Use when the user pastes or describes a brief, scope, proposal or statement of work and wants it set up in MonoDesk, or asks to start, kick off or plan out a new project.
---

# Project kickoff

Turn a brief into a project, milestones and tasks in MonoDesk.

## Steps

1. Read the brief. Pick out the client, the project name, deliverables, deadlines and anything the client must supply.
2. Check whether the client exists with `find`. If it does not, plan to create it. If the project name already exists for that client, ask whether to add to it instead.
3. Call `listTeamMembers` only if the brief names people other than the user. Use `"me"` as the assignee for the user's own tasks.
4. Draft the setup:
   - Client (existing or new).
   - Project name and description.
   - Milestones, each with a name and due date.
   - Tasks under each milestone, each with a name, assignee and due date where the brief gives one.
   Keep task names short and specific. Do not pad the list with generic tasks the brief does not call for.
5. Show the full draft as a list and ask for a yes or changes. Write nothing until the user agrees.

## Writing

Once the user says yes, create in this order:

1. The client with `createClient`, if it is new.
2. The project with `createProject`.
3. Each milestone with `createMilestone`.
4. All tasks in one `batchCreateTasks` call (up to 100 rows). Do not loop `createTask`.
5. Subtasks, if any, with `createSubtask`.

Then link the user to the project with the `url` from the response, and list anything you could not create with the reason.

## Notes

- All tools act in the user's current workspace.
- If the brief has no dates, ask for a target end date before drafting milestones rather than guessing.
