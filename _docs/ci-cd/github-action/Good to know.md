---
title: Good to know
permalink: /docs/ci-cd/github-action/good_to_know/
---

## Good to know about Github Action

### About CRON

- An action triggered by CRON config will use the default branch

> As workaround, on the checkout phase, set explicitly the branch to use

### About Inputs

- If you want to use a boolean input and you want to test it, you will have to compare the value like a String. [Issue on Github action repository](https://github.com/actions/runner/issues/1483)
  > if: $\{\{ github.event.inputs.my_boolean == 'false'}}

## Limitation of the Github Action

### The result of a workflow can't trigger another one

If you have an action who is supposed to be triggered when a pull request is created (for example to run tests) and another one who will generate a pull request, the first one will not be triggered

> As workaround, it's possible to use a personal access token instead of the one provided by default by Github

### It's not possible to overpass branch security

If you define some rules on your branch to force developer to use Pull request to push on it (including Administrator), the same rules will be applied on the Github Action.
