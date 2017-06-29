Architecture
===

# Key Words

Master Deamon
Resource offer
Framework
scheduler
executor

Agent Deamon
Task

ZooKeeper quorum

# Master

1. Masters share resources (CPU, RAM...) across frameworks
2. Masters make resource offers to frameworks:
..* agent ID
..* resource1: amount1
..* resource2: amount2
..* ...
3. Masters decide how many resources to offer according to a given organizational policy
..* fair sharing
..* strict priority
..* ...
4. Master employs a modular architecture to add new allocation modules via a plugin mechanism

# Framework

1. Scheuler registers with the master to be offered resources

2. Executor is launched on agent nodes to run framework's tasks

3. Master offer *how many* resourced to each framework,
the framework's schedulers select *which* to use

4. Framework accept resources, passes Mesos a description of tasks to run,
Mesos lauches the tasks on corresponding agents

# Example of recource offer

Mesos Master
Agent1
Agent2
Framework1

1. Agent1 reports to master it has 4 CPUs and 4GB memory free
2. Master invokes allocation policy module, which says framework1 should be offered all resources
3. Master sends a resource offer describing what available on agent1 to framework1
4. Framework1 replies two tasks to run
..1. Task1, using 2 CPUs and 1 GB RAM
..2. Task2, using 1 CPUs and 2 GB RAM
5. Master send tasks to agent1. 
6. Agent1 allocates resources to framework1 executor.
7. Executor launches tasks
8. Agent1 reports to master it has 1 CPU and 1 GB memory free

# Pros

Allow Mesos to scale
Frameworks evolve independently

Delay scheduling
Data locality


