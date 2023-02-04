FreeBSD Work Flow Working group
===============================

This repository contains various working documents for the FreeBSD work flow
improvement group.

Next meeting info link:/meetings/agenda.md[here]

.This working group's efforts is focused on the following areas:
. Creating CI pipelines
. What to do about Phabricator
. What to do about Bugzilla
. Best way to accept pull requests
. Making it easier to find relevant feedback
. Vendor Import Issues
. Repo integrity

== Creating CI pipeline

Currently, we use Jenkins to run a CI pipeline after each commit.
However, this is done after the commits are made.
It's difficult for developers to run themselves before commits.
Not currently integrated into gitlab or github CI infrastructure.

The focus of the working group will be to see what we can do to increase access to CI pipelines.

In addition, due to our large testing matrix, are there smart ways that we can optimize the pipelines.

What testing and experimentaiton do we need to do for us to make our decisions?

== Phabricator

The main developers of Phabricator have announced that it is at EOL.
They will not continue to maintain it.
Community efforts, lead primarily by wikimedia, has sprung up.

.Current questions to consider:
* The question that needs to be answered is what do we do with Phabricator?
* Do we join the community efforts to keep it alive?
* Do we stand up another service?
* Do we move to something else hosted elsewhere?
** Github has code review on its pull requests
** Gitlab has code review for its modification requests

== Bugzilla

The project has used Bugzilla for some time now.
We've done some unnatural things with it.
We've also done some cool things to automate some workflows in the project.

* Does Bugzilla fit our needs?
* Are we doing things in Bugzilla that are better done with other tools?
** Pull Requests
** Maintainer Feedback
** ExpRun management

== Pull Requests

A lot of people want to accept pull requests.
Today, the project will land pull requests that wind up in github mirror, but we don't guarantee that.
We have some CI pipelines that run for pull requests, but coverage is weak.

* Should Pull Requests be the primary way to get things into the tree?
* Is there a service that we should use for this?
* What's the relative merits of gitlab vs github for this service?
* Do we want a single point that flows into the tree, or multiple flows into the tree + tooling?
** There's much diversity in how open source projects do this, we should survey to find out what's working and what's not.

== Information Overload

One of the big complaints with project has been dropped patches.
Another complaint from developers is that it's hard to find relevant information to into the tree.
How do we address these issues?

== Vendor Import Issues

We currently have an OK vendor import, but there's problems with it.

* must use `git bisect start --first-parent` only
* openzfs branch doesn't have non-zfs FreeBSD files
* Tag for each import (is this a problem?)
* Why not submodules?
* Alternatively, why not `git subtree merge --squash`?

== Repo Integrity

Do we want to sign all commits?
