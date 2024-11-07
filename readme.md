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

- jobs
```yml
jobs:
  # This workflow contains a single job called "merge"
  merge:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest
    
    steps:
      # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
      - uses: actions/checkout@v4 
      
      # run multiple command target to merge main to dev and push
      - name: Run merge task
        run: |
          git checkout -b dev
          git merge main
          git push origin dev
```
- `uses: actions/checkout@v4`, actions/checkout@v4 here is someone defined action 

run automerge.yml encounter issue
![alt text](images/automerge-run-issue.png.png)
> remote: Permission to rechardguo/github-action-practise.git denied to github-actions[bot].

**Workround**
[authentication](
https://docs.github.com/zh/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

1. 创建 Personal Access Token (PAT)
登录到你的 GitHub 账户。
转到 Settings > Developer settings > Personal access tokens。
生成一个新的 token，确保选择适当的权限（至少包括 repo 范围，这样它可以读写仓库）。
复制生成的 token，因为你之后需要它。

2. 将 PAT 添加到 GitHub Secrets
转到你的仓库页面。
选择 Settings 标签。
在左侧菜单中选择 Secrets and variables > Actions。
点击 New repository secret。
为你的 token 创建一个新的 secret，例如命名为 PERSONAL_ACCESS_TOKEN，然后粘贴之前复制的 token 作为它的值。



# reference
[spring action](https://docs.github.com/zh/actions)