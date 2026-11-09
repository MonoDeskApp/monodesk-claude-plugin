# MonoDesk

MonoDesk is a workspace for freelance creatives: clients, projects, task boards, time logs, leads and files. This plugin connects Claude to your MonoDesk account and adds skills for jobs freelancers do every week.

You need a MonoDesk account. Sign up at https://www.monodesk.com/.

## Install

On claude.ai, add MonoDesk from **Customize > Plugins**. In Claude Code, run:

```
/plugin marketplace add MonoDeskApp/monodesk-claude-plugin
/plugin install monodesk@monodesk
```

The first line adds this repository as a marketplace. The install fails with "not found in marketplace" if you skip it.

## Skills

- **plan-my-week**: reads your open tasks and schedule and proposes an order for the week.
- **client-update**: drafts a progress update for a client from task activity, comments and logged time.
- **project-kickoff**: turns a brief into a project with milestones and tasks.
- **log-my-day**: turns a description of your day into time entries.
- **move-to-monodesk**: imports clients, projects and tasks from a spreadsheet or another tool's export.
- **lead-follow-up**: reviews your open leads and drafts the next message for each.

Claude picks the right skill from what you ask. For example: "What should I work on this week?", "Write this week's update for Acme", or "I spent two hours on the Acme logo and an hour on invoices, log it."

Before any skill creates or changes anything in MonoDesk, Claude shows you what it will write and waits for you to say yes. Messages and updates are drafts for you to send yourself.

## Connecting

The plugin includes the MonoDesk connector at `https://api.monodesk.com/api/mcp`. On claude.ai, open the plugin's Connectors tab and connect it, then sign in with your MonoDesk account. Claude Code asks you to sign in the first time a skill uses it.

All your connected AI clients (Claude, ChatGPT, Cursor and others) share one active MonoDesk workspace. If you belong to more than one, switching workspace from one client changes it for the others too.

## Data

The skills read and write data in your MonoDesk account through the MonoDesk connector only. That includes tasks, projects, clients, leads, comments, time logs and files you choose to import. The plugin sends nothing to any other service and stores nothing itself. What Claude can see and change depends on your permissions in the workspace.

## Support

Get support at https://www.monodesk.com/help or email support@monodesk.com.

## Privacy

The MonoDesk privacy policy is at https://www.monodesk.com/privacy.

## Licence

This plugin is released under the MIT licence (see `LICENSE`). The licence covers this plugin repository only, meaning the skills, manifest and docs. It does not cover the MonoDesk app or service.
