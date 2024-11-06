# target
This project created for spring action learning.

# note
1. Create .github/workflows folder in current project
2. Workflow is yml format 

# workflow file definition

- name: workflow name
```yml
name: "Greetings"
```

- on : when to trigger workflow

```yml
on: [pull_request_target, issues, push,fork]
```
push : when code push
fork : when someone fork this repo
issues : when someone raise a issue
pull_request_target : when someone raise a pr

```yml
on:
  push:
    branches:
      - main
      - 'releases/**
```
push event condition

# reference
[spring action](https://docs.github.com/zh/actions)