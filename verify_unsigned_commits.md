### Workaround to verify unsigned commits in github

**Before anything make sure you have your configuration to sign commit ready!!!**

Lets say you have this PR with one unsigned commit and there is a rule in master to avoid pull requests with unsigned commits.

![pull request example](https://image.ibb.co/b1O3Sz/Screen_Shot_2018_09_07_at_12_34_32_AM.png)

First check what was the commit id for the commit right before the unsigned one, in this case let's get id for "First paragraph"

`git log`

![git log example](https://image.ibb.co/cwXrEe/Screen_Shot_2018_09_07_at_12_39_38_AM.png)

Now we'll start rebasing dev branch

`git rebase --interactive a6a7e9222b122a2e10573545583edddcd3b9b4f3`

Replace `pick` with `edit` in the unsigned commit and save, in this case "Second paragraph".

![edit vim](https://image.ibb.co/jEQ3ue/Screen_Shot_2018_09_07_at_12_46_31_AM.png)

To verify the unsigned commit we need at least to make one change, so we'll replace the commit message with previous one. Next command will prompt vim so just save with `:wq`

`git commit --amend '-S'`

We have to finish the rebase process.

`git rebase --continue`

Now we have this in our working tree, where the second "Second paragraph" has been signed.

![github tree](https://image.ibb.co/diA6fK/Screen_Shot_2018_09_07_at_12_53_15_AM.png)

- Create a new branch based on this changes, in this we'll name it dev_signed

`git checkout -b dev_signed`

- Push your changes

`git push --set-upstream origin dev_signed`

- Finally create a new pull request with dev_signed branch.

![new pr](https://image.ibb.co/gHibfK/Screen_Shot_2018_09_07_at_12_57_42_AM.png)