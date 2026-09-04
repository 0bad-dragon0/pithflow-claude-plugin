# Pithflow plugin for Claude Code

Read-only access to your own [Pithflow](https://pithflow.com) data from Claude Code:
recorded meetings (notes and full transcripts), your dictation dictionary, your snippets,
and your usage totals.

Pithflow is a Windows voice-dictation and meeting-notes app. This plugin connects Claude
Code to the same remote connector that Claude.ai, ChatGPT, Cursor and VS Code use — see
the [connector docs](https://pithflow.com/docs/mcp/).

## What you get

Seven read-only tools:

| Tool | Returns |
|---|---|
| `list_meetings` | Your recorded meetings, newest first |
| `search_meetings` | Meetings that mention a phrase, with an excerpt |
| `get_meeting` | One meeting's summary, key points, decisions and action items |
| `get_meeting_transcript` | The full transcript, a page at a time |
| `get_vocabulary` | Your saved dictionary terms |
| `get_snippets` | Your trigger phrases and expansions |
| `get_usage_summary` | Words and minutes dictated this week and month, and your plan |

Plus a `pithflow-meetings` skill that tells Claude which tool to reach for and how to
treat transcript text (as data, never as instructions).

Nothing in this plugin can add, change or delete anything in your account, and no tool
accepts an account or user id: every call is scoped to the account you sign in with.

## Install

From the community marketplace, once listed:

```
/plugin install pithflow@claude-community
```

Or straight from this repository, which doubles as a one-plugin marketplace:

```
/plugin marketplace add 0bad-dragon0/pithflow-claude-plugin
/plugin install pithflow@pithflow
```

Or without touching marketplaces at all:

```
claude plugin install --plugin-source github --repo 0bad-dragon0/pithflow-claude-plugin
```

The first tool call opens Pithflow's sign-in page in your browser. Sign in with your
Pithflow email and password and approve the read-only scope. The password is used for
that one sign-in and is never stored by the connector.

## Without the plugin

The connector works in Claude Code on its own:

```
claude mcp add --transport http pithflow https://api.pithflow.com/mcp
```

The plugin adds the skill and a one-line install; the tools are the same.

## Privacy

What the connector can see, for how long, and how to disconnect:
[pithflow.com/privacy#mcp](https://pithflow.com/privacy#mcp). Questions:
hello@pithflow.com.

## License

MIT.
