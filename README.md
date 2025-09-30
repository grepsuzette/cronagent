# cronagent: AI Agent Scheduling System

Precise, efficient scheduling and execution of subagents simply using the user's crontab.
Primarily for qwen-code and gemini-cli.

# Just two files

This README.md file, and one bash script `cronagent`.

# What is cronagent

**cronagent** is a small (100 lines) bash utility to launch agents from the crontab in [qwen-code](https://github.com/QwenLM/qwen-code) or [gemini-cli](https://github.com/google-gemini/gemini-cli).

It can 

* help to make a **new** cronagent entry, 
* **list** the cronagent entries, 
* show the **logs**, 
* last but not least, it is called by the `crontab` to launch the named subagent 

Here is what an agent looks like:

```crontab
*/5 * * * *  /path/to/cronagent run /Users/bob/stories @dnd-storyteller Write a new story and stop.
```

@dnd-storyteller is an agent (created with `/agents create` in `qwen`) to write Dungeon and Dragons
stories with a certain set of characters.

The above crontab entry will call the agent @dnd-storyteller every 5 minutes,
to write a new roleplay story (creating a new file each time in
/Users/bob/stories).

That's it.

Errors and logs are in `$HOME/opt/var/log/cronagent/@<agentName>.log` (see `cronagent logs`).

Question, can you edit with `crontab -e`? Absolutely. 

Use `cronagent new` the first time but then don't hesitate to edit the crontab manually.

# Commands

* `cronagent list`: list all agent cron entries
* `cronagent new`: create new agent cron entry
* `cronagent help`: show help information
* `cronagent logs`: show execution logs
* `cronagent run /path/to/project @<agentName> arg1...`: run specific agent in qwen-code with arguments and redirect stdout/err to files

Note:
- No timeouts, be careful of long running tasks. 

