# MonoDesk plugin for Claude

This repository holds the MonoDesk plugin for Claude and a Claude Code marketplace that lists it.

The plugin adds six skills and the MonoDesk connector (`https://api.monodesk.com/api/mcp`). The skills plan your week, draft client updates, set up projects from a brief, log time from a description of your day, import data from other tools, and draft lead follow-ups. A MonoDesk account is required. The plugin's own README, at `plugins/monodesk/README.md`, is the text the directory listing shows.

All connected AI clients share one active MonoDesk workspace. Switching workspace from Claude changes it for ChatGPT, Cursor and any other connected client as well.

## Layout

```
.claude-plugin/marketplace.json   marketplace file; lists the plugin below
plugins/monodesk/                 the plugin folder (submit this path to the directory)
  .claude-plugin/plugin.json      manifest
  .mcp.json                       MonoDesk connector
  assets/icon.png                 listing icon, 1024 x 1024 PNG
  skills/<name>/SKILL.md          one folder per skill
  README.md                       listing description
```

The plugin lives in a subfolder so that repository files are not installed with it or read by the directory scan.

## Install

### claude.ai and the Claude apps

Once the plugin is listed, open **Customize > Plugins**, find MonoDesk and add it. Then connect MonoDesk from the plugin's **Connectors** tab and sign in.

Before then, add this repository as a marketplace: **Customize > Plugins > Add > Add marketplace**, and enter the GitHub URL.

### Claude Code

```
claude plugin marketplace add MonoDeskApp/monodesk-claude-plugin
claude plugin install monodesk@monodesk
```

Or, inside a session:

```
/plugin marketplace add MonoDeskApp/monodesk-claude-plugin
/plugin install monodesk@monodesk
```

To try a local copy without installing: `claude --plugin-dir ./plugins/monodesk`.

## Licence, support and privacy

This repository is released under the MIT licence (see `LICENSE`). The licence covers this plugin repository only, meaning the skills, manifest and docs. It does not cover the MonoDesk app or service.

Support is at https://www.monodesk.com/help. The privacy policy is at https://www.monodesk.com/privacy.

## Check before pushing

```
claude plugin validate .
claude plugin validate ./plugins/monodesk
```
