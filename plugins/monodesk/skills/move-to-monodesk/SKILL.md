---
name: move-to-monodesk
description: Import clients, projects or tasks into MonoDesk from a spreadsheet or another tool's export. Use when the user shares a CSV or Excel file, or an export from Trello, Asana, Notion, Monday, ClickUp, Airtable or a similar tool, and wants the contents brought into MonoDesk.
---

# Move to MonoDesk

Bring the user's data from a spreadsheet or another tool's export into MonoDesk.

## Steps

1. Get the file into MonoDesk. If the user attached it in the chat, upload it: call `createFileUploadUrl`, upload the file to the returned URL, then call `confirmFileUpload`. If it is already in MonoDesk, find it with `listFiles`.
2. Call `readImportFile` to see the columns and a sample of rows. For large sheets, use `readFileRows` to page through. Use `readFileContent` for a text or document export that is not a table.
3. Work out what each row is (client, project or task) and map the columns to MonoDesk fields: name, client, project, assignee, due date, status column, labels. Ask about any column you cannot map.
4. Call `previewFileImport` with that mapping. Show the user the preview: how many clients, projects and tasks will be created, a few sample rows, and any rows that will be skipped and why. Ask for a yes or changes.
5. When the user says yes, call `confirmFileImport`.
6. Report what was created and link the main projects with their `url`.

## When the file import tools do not fit

If the data is not a file, for example a list pasted into the chat, build the records yourself:

- Check existing names with `find` first so you do not create duplicates.
- Show the full list of what will be created and wait for a yes.
- Use `batchCreateClients`, `batchCreateProjects` and `batchCreateTasks` (up to 100 rows each), in that order. Do not create records one at a time in a loop.
- Create any missing labels with `createLabel` before the tasks that use them; check `listLabels` first.

## Notes

- All tools act in the user's current workspace. Confirm it with `getMyProfile` before a large import.
- Comments, attachments and time history from other tools may not carry over. Tell the user what was left out.
