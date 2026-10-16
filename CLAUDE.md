# Resolving Merge Conflicts

When a PR branch conflicts with its target branch (default `origin/dev`), rebase
instead of merging:

* Never merge the target branch into the PR branch. Do not create merge commits.
* `git fetch origin <target>` then `git rebase origin/<target>`, resolve conflicts
  per commit, and regenerate lockfiles and generated files with the repo tooling.
* Re-run the relevant checks, then push with `git push --force-with-lease`.
  Never use a plain `--force`.
* Only rebase branches you created. Ask the author before rebasing anyone else's
  branch.
