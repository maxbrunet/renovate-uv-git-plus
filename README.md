# 47575

Reproduction for [renovatebot/renovate#47575](https://github.com/renovatebot/renovate/pull/47575)

## Current behavior

Renovate passes `git+https://github.com/pallets/click` to `git ls-remote`.
Git has no `git+https` remote helper, so the lookup fails with:

```text
git: 'remote-git+https' is not a git command.
fatal: remote helper 'git+https' aborted session
```

## Expected behavior

Renovate strips the `git+` prefix and runs
`git ls-remote https://github.com/pallets/click`. The lookup succeeds.
