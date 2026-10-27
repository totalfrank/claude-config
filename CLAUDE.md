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

# Marking Pull Requests Ready for Review

When the coding work for a PR is finished, mark the PR ready for review. Don't
leave it as a draft.

* "Finished" means the requested change is fully implemented, the relevant local
  checks pass (tests, lint, typecheck), and the work is pushed.
* Opening the PR as a draft first is fine. Once the work is finished, flip it with
  `draft: false` (`mcp__github__update_pull_request`, or `gh pr ready <number>`).
  Don't ask for permission first.
* Re-read the PR afterwards to confirm it is no longer a draft. If the flip failed,
  retry once, then tell me.
* Leave it as a draft only when the work is incomplete or a check is failing, and
  say which one.
* Marking the PR ready starts the automated reviews, so continue with the
  `peerreview` loop afterwards.
