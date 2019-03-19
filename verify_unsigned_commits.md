### Workaround to verify unsigned commits in github

**Before anything make sure you have your configuration to sign commit ready!!!**

Lets say you have this PR with one unsigned commit and there is a rule in master to avoid pull requests with unsigned commits.

![pull request example](/imgs/pull_request_example.png)

First check what was the commit id for the commit right before the unsigned one, in this case let's get id for "First paragraph"

```bash
git log
```

![git log example](/imgs/git_log_example.png)

Now we'll start rebasing dev branch

```bash
git rebase --interactive a6a7e9222b122a2e10573545583edddcd3b9b4f3
```

Replace `pick` with `edit` in the unsigned commit and save, in this case "Second paragraph".

![edit vim](/imgs/edit_vim.png)

To verify the unsigned commit we need at least to make one change, so we'll replace the commit message with previous one. Next command will prompt vim so just save with `:wq`

```bash
git commit --amend '-S'
```

We have to finish the rebase process.

```bash
git rebase --continue
```

Now we have this in our working tree, where the second "Second paragraph" has been signed.

![github tree](/imgs/github_tree.png)

- Create a new branch based on this changes, in this we'll name it dev_signed

```bash
git checkout -b dev_signed
```

- Push your changes

```bash
git push --set-upstream origin dev_signed
```

- Finally create a new pull request with dev_signed branch.

![new pr](/imgs/new_pr.png)