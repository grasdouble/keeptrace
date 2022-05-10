---
title: Tooling
permalink: /docs/ci-cd/github-action/tooling/
---

## How to work on Github Action locally

When you start to work for the first time on a github action, you will certainly have the reflex to directly test it on Github.

If sometimes it's enough, you will see the limit if you have to do multiple try to do what you want.

Each time you will want to test, you will have to commit and push your changes and after many tries your git history can become a trash of meaningless messages.

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

For more info: [Act project on Github](https://github.com/nektos/act)
