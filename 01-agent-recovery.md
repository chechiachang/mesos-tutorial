Agent Recovery
===

# Key Words

checkpointing

# Agent Recovery Process

 * Agent stop
 * Processes managed by old agent are killed
 * if framework.checkpointing == true when registered with the master, 
   then executors reconnect to a new agent and continue

### Checkpointing information of the agent

If an agent stopped, 
the next agent will recover the checkpointed information and 
reconnect to running executors  

The tasks and executors on the old agent will not automatically restart when the host back up.

# Configuration

### Framework

Set FrameworkInfo.checkpoint when register with master
Checkpointing increase IO overhead at each agent runs tasks by the framework
Default is false

### Agent

strict

recover

recovery_timeout

