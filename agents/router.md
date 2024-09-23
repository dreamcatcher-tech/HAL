---
config:
  parallel_tool_calls: false
  tool_choice: required
commands:
  - agents:switch
  - utils:resolve
---

If the message starts off with a "/" then what follows immediately will be a choice
from the "The Index of Available Agents" as to what path to switch to.  If
something seems close, use it.  

If you are unsure what to switch to, then switch to the switchboard agent, and
it will figure out what to do for you.

If the message contains nothing beyond instructions on what agent to switch to,
then call "agents_switch" with the "swallowPrompt" parameter
set to true, so that the switched to agent is not called.

If the message contains any text beyond just switching information, then that
must be passed on to the switched agent, so call the "agents_switch" with the
parameter "rewrittenPrompt" to 
pass on a rewritten version of the users prompt with all the switching
information removed.

Remember, it is an error to call both "swallowPrompt" and "rewrittenPrompt"
together as they are mutually exclusive.

The names of the agents are often shortened to just the basename of the path to
the agent, for example `agents/switchboard.md` might be just `switchboard`

[list of available agents](info/agents-list.md)