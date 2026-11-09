---
name: lead-follow-up
description: Review open leads in MonoDesk and draft the next follow-up message for each. Use when the user asks about their leads, pipeline or enquiries, wants to know who to chase, or asks for help writing a follow-up to a prospective client.
---

# Lead follow-up

Review the user's open leads and draft the next message for the ones that need it.

## Steps

1. Call `listLeads` to get open leads. If the user names one, resolve it with `find` or pick it from the list.
2. Call `getLead` on each lead you will look at closely, to read its stage, value, notes and last contact.
3. Sort the leads by what needs attention: no reply for a while, a promised date that has passed, or a proposal waiting on an answer. Show a short list with the lead, stage, last contact and why it needs a follow-up.
4. For each lead the user picks, draft a short follow-up message. Base it on the lead's notes and stage. Keep it specific to that person and their project, and end with one clear next step. Do not invent details that are not in the lead.
5. Show the drafts. The user sends them; this skill does not send anything.

## Updating leads

Offer to record the follow-up in MonoDesk. Show exactly what will change and wait for a yes before writing.

- `updateLead` to change the stage, next follow-up date or notes.
- `createTask` with `assigneeId: "me"` for a reminder, or `batchCreateTasks` for several.
- `winLead` only when the user says the lead has been won. Confirm the lead with the user before calling it.
- Link the user to any task you create with its `url`.

## Notes

- All tools act in the user's current workspace.
- If there are no open leads, say so. Do not create leads unless asked; if asked, use `createLead` after showing the details.
