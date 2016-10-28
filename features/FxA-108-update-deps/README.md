# FxA-108: update dependencies in FxA projects

> https://github.com/mozilla/fxa-features/issues/17

## Problem Summary

It's hard for us to respond to security issues in our dependencies in a timely manner.

This feature milestone deals with the following problems:

* Problem 1: Outdated node modules in FxA code repositories.
* Problem 2: Outdated version of node.js.
* Problem 3: Late response to security issues reported by NSP (Node Security Project).
* Problem 4: Some repositories are not covered by the NSP scanner.


****

## Outcomes

Success criteria to fix the problems listed in the problem summary:

* Update to latest major versions of core server dependencies.
* Production stack running with node 4. Migrated from node 0.10.
* Being able to receive notifications of latest security alerts within a day of a reported issue for all FxA node.js-based repositories.

## Hypothesis

For problems [3] and [4]:

We believe that building a nightly reporter based on a CI service
for all FxA node.js repositories will help us stay informed about security alerts.

We will know this is true when we see better notifications from this NSP CI service.

****

## Detailed design

To solve problem [1]:

Identify changes in latest versions of published modules and make the required changes.

To solve problem [2]:

Work with the DevOPS team to resolve any node 4 issues in staging and production stacks.

To solve problems [3] and [4]:

A script running against a [nightly build setup of Circle CI](https://circleci.com/docs/nightly-builds/)
will be able to report outdated modules for several repositories.
In addition it would forward NSP alerts to Sentry that can provide a visualization of affected repositories and
alert developers using email.

## Results

* Problem 1: Outdated node modules in FxA code repositories.
  * Most important modules, such as hapi, were updated once projects moved to node.js 4+ servers.
* Problem 2: Outdated version of node.js.
  * The node.js version has been updated to version 4 as part of another milestone.
* Problem 3: Late response to security issues reported by NSP (Node Security Project).
* Problem 4: Some repositories are not covered by the NSP scanner.
  * More repositories are now covered using the new NSP scanner.
  * New security alerts are being sent out by email and Slack!
