### Workaround to verify unsigned commits in github

All commits started from 8fd7b22 will be rebased with no changes except signing.

```bash
git rebase --exec 'git commit --amend --no-edit -n -S' -i 8fd7b22
git push --force
```

![Source](https://stackoverflow.com/questions/41882919/is-there-a-way-to-gpg-sign-all-previous-commits)

