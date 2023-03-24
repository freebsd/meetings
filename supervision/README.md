# Supervision Workgroup


The goal of the group is improving FreeBSD in the following areas:

- process tracking
- process resource control
- process confinement
- process supervision
- service management
- tools and languages for the above


## Process Tracking

Process tracking is how we reliably track the state of process, such that we can always say if the process is up or down.
For example: Linux PID namespace, tracked but not confined.
cgroups also fit in, if we forget for a moment that cgroups are also resource management tools.
namespace, tracked but not confined. cgroups also fit in, if we forget for a
moment that cgroups are also resource management tools)

## Process Resource Control

Process resource control is how we ensure that a process consumes no more than the allocated amount of resources.
For example: [`rctl(8)`](https://man.freebsd.org/rctl(8)), cgroups.
Resource control relies on process tracking.


## Process Confinement

Process confinement is how we run a process in a deterministic sandbox,
such that the process has no way of escaping (example: chroot, confined but not tracked),
and only is allowed access to a pre-defined environment (files, network interfaces, etc)

Process Confinment requries reliable tracking.


## Process Supervision

Process supervision answers the following questions:
- How do we ensure that a process is always in a desired state?
- What types of supervised processes are there?
- Did the process exit successfully or do we need to restart it?
- How do we reliably and repeatably start and stop the process?

Process supervision requires reliable tracking.

## Service Management

Service management is how we bring groups of processes or the whole system into the desired state.
This in turn requires knowing:
- which services and processes need to be up, in what order?
- how to transition reliably between system states?

Service managemement requires process supervision

# Tools and Languages

Shell, Lua, C

# Existing Supervision-Related Tools

Existing tools and their respective problems:

Tool      | Tracking | Confinment | Resource Control | Supervision
----------|----------| -----------|------------------|-------------
chroot    | No       | limited: only mount namespace| No | No
jail      | JID      | Strong     | via rctl         | No
daemon    | parent/child | No     | No               | very basic
rctl      | imperfect| No         | Yes              | No
login classes| imperfect | No     | Yes + Rctl       | No
process groups| imperfect| No     | No               | No

