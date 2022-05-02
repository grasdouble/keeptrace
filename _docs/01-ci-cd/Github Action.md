---
layout: default
title: Gtihub Action
parent: CI - CD
nav_order: 1
---

# How to work on Github Action

When you start to work for the first time on a github action, you will certainly have the reflex to directly test it on Github.

If sometimes it's enough, you will see the limit if you have to do multiple try to do what you want.
\
\
Each time you will want to test, you will have to commit and push your changes and after many tries your git history can become a trash of meaningless messages.
\
\
To give you an example of my git history when I was struggling to do what I wanted:

```
- fix the bug
- fix
- another try to fix
- try another solution
- ....
```

Of course sometimes, there is no other choice than test it directly on Github but when it's possible, I invite you to use **ACT**.

**ACT** is a tool working with **Docker** who will run you github action locally and give you some insights if a problem occurred.

For more info: https://github.com/nektos/act

# Good to know about Github Action

## About CRON

- An action triggered by CRON config will use the default branch

> As workaround, on the checkout phase, set explicitly the branch to use

## About Inputs

- If you want to use a boolean input and you want to test it, you will have to compare the value like a String. [Issue on Github action repository](https://github.com/actions/runner/issues/1483)
  > if: $\{\{ github.event.inputs.my_boolean == 'false'}}

# Limitation of the Github Action

## The result of a workflow can't trigger another one

If you have an action who is supposed to be triggered when a pull request is created (for example to run tests) and another one who will generate a pull request, the first one will not be triggered

> As workaround, it's possible to use a personal access token instead of the one provided by default by Github

## It's not possible to overpass branch security

If you define some rules on your branch to force developer to use Pull request to push on it (including Administrator), the same rules will be applied on the Github Action.

# Which actions to use

## The basics

- [Checkout](https://github.com/marketplace/actions/checkout): An action to checkout the content of your repository.
- [Setup node](https://github.com/marketplace/actions/setup-node-js-environment): An action to setup node.

## Some others

- [GitHub Create Tag Release](https://github.com/marketplace/actions/github-create-tag-release): An action to create a release tag.
- [GitHub Action for creating Pull Requests](https://github.com/marketplace/actions/github-action-for-creating-pull-requests): An action that will create a pull request between two branches.
- [Sync branches](https://github.com/marketplace/actions/sync-branches): An action to sync one branch when another is updated.
- [Cache](https://github.com/marketplace/actions/cache): An action to manage cache of yarn, npm, ...

# External links

- [Github documentation](https://docs.github.com/en/actions): The root path to start to learn how to use Github Action.
