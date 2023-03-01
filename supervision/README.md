# Supervision Workgroup


The goal of the group is improving FreeBSD in the following areas:

- process tracking
- process resource control
- process confinment
- process supervision
- service management
- tools and languages for the above


## Process Tracking

Process tracking is how do we reliably track the state of the process, such
that we can always say if the process is up or down (example: linux PID
namespace, tracked but not confined. cgroups also fit in, if we forget for a
moment that cgroups are also resource management tools)

## Process Resource Control

Process resource control is how do we make sure that process consumes no
more than allocated amount of resources (example: rctl, cgroups).
Resource control relies on process tracking.


## Process Confinment

Process confinement is how do we run a process in a deterministic sandbox,
that process has no way of escaping (example: chroot, confined but not
tracked) and only allows access to a pre-defined environment (files,
network interfaces, etc,)

Process Confinment requries reliable tracking.


## Process Supervision

Process supervision answers the following questions:
- How do we make sure that process is always is in desired state?
- What types of supervised processes are there?
- Did the process exit successfully or do we need to restart it?
- How do we reliably and repeatably start and stop the process?

Process supervision requries reliable tracking.

## Service Management

Service management is how do we bring groups of processes or  the whole system
into the desired state, what services and processes need to be up, in what
order. How to transition between system states reliably?

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
login classes| imperfect | No     | Yes + Rctl       | Now
process groups| imperfect| No     | No               | Now

