# Contribution 4: `Add message queue support for V1 conversations during WebSocket connection`

**Contribution Number:** 4  
**Student:** Jessica Lang  
**Issue:** [OpenHands/OpenHands#12279](https://github.com/OpenHands/OpenHands/issues/12279)  
**Status:** Phase IV submission prep in progress

**Important note as of June 16, 2026:**

I am working on Phase IV honestly based on the current state of my contribution, not the ideal end state. I have a real local OpenHands branch and a real local commit, but I do **not** yet have a submitted upstream pull request because the GitHub account authenticated on this machine is `SreytouchLang`, while the repositories I need to update are owned by `jessicalang2595`.

---

## Final Pre-Submission Checks

### Current OpenHands Contribution State

- **Repository:** [jessicalang2595/OpenHands](https://github.com/jessicalang2595/OpenHands)
- **Local branch:** `test/v1-pending-message-queueing`
- **Local commit:** `789fba303da66ea87f0439211ed108fd2c499414`
- **Commit message:** `test(frontend): add V1 pending message queue coverage`

### What the Current Change Includes

The current code contribution adds targeted frontend tests to `OpenHands` for the V1 pending-message fallback path:

1. a test confirming that `sendMessage` queues through `PendingMessageService` when the WebSocket is not connected
2. a test confirming that queueing failures are surfaced to the caller and to the frontend error message store

### Diff Scope Check

I reviewed the current branch diff against `OpenHands` `main` and it contains only one file change:

- `frontend/__tests__/conversation-websocket-handler.test.tsx`

This is a clean, issue-related diff with no unrelated formatting or debug changes.

### Test Check

I verified the new targeted tests pass under the bundled workspace Node runtime:

- **Bundled Node version used for testing:** `24.14.0`
- **Targeted result:** `2 passed, 40 skipped`

The exact passing command was:

```bash
/Users/sreytouch/.cache/codex-runtimes/codex-primary-runtime/dependencies/node/bin/node \
  /Users/sreytouch/Desktop/ReactJs/OpenHands/frontend/node_modules/vitest/vitest.mjs \
  run __tests__/conversation-websocket-handler.test.tsx \
  -t "queue user messages through PendingMessageService|surface queueing errors when PendingMessageService fails"
```

### Remaining Pre-Submission Risks

1. I still do not have a pushed branch on my fork because `git push` returns GitHub permission errors.
2. The original issue scope has drifted: current `OpenHands` `main` already includes server-side pending-message queueing, so this contribution is currently a test-coverage improvement around the modern implementation rather than a full original-feature implementation.
3. Because of that scope drift, I would not use `Closes #12279` in a PR until maintainers confirm that this narrower contribution should resolve the issue.

---

## Pull Request

### PR Link

**PR Link:** Not available yet. The PR has not been submitted because the branch is not yet pushed to GitHub.

### Planned PR Route

When GitHub authentication is fixed, the PR route should be:

- **Head:** `jessicalang2595/OpenHands:test/v1-pending-message-queueing`
- **Base:** `OpenHands/OpenHands:main`

### Draft PR Title

`test(frontend): add V1 pending message queue coverage`

### Draft PR Description

I checked the repository PR template in `OpenHands/.github/pull_request_template.md`. Based on that template, this is the PR description I would submit:

~~~md
## Why

V1 conversations already fall back to `PendingMessageService` when the WebSocket
is unavailable, but the frontend WebSocket handler test suite did not clearly
cover that disconnected queueing path or its error-handling behavior.

## Summary

- add a V1 test that verifies disconnected `sendMessage` calls queue through
  `PendingMessageService`
- add a V1 test that verifies queueing failures surface both to the caller and
  to the frontend error message store
- keep the change scoped to frontend test coverage only

## Issue Number

Related to #12279

## How to Test

Run:

```bash
/Users/sreytouch/.cache/codex-runtimes/codex-primary-runtime/dependencies/node/bin/node \
  /Users/sreytouch/Desktop/ReactJs/OpenHands/frontend/node_modules/vitest/vitest.mjs \
  run __tests__/conversation-websocket-handler.test.tsx \
  -t "queue user messages through PendingMessageService|surface queueing errors when PendingMessageService fails"
```

Expected result:

- 2 tests pass for the V1 queue fallback scenarios

## Video/Screenshots

Not applicable. This PR adds automated frontend test coverage only.

## Type

- [x] Bug fix
- [ ] Feature
- [ ] Refactor
- [ ] Breaking change
- [ ] Docs / chore

## Notes

- This PR adds targeted coverage for the current V1 queue fallback path.
- I am intentionally using `Related to #12279` instead of `Closes #12279`
  because the current contribution strengthens coverage around the existing
  implementation rather than clearly resolving the entire original issue scope.
~~~

### Why the PR Is Not Open Yet

I attempted to push the `OpenHands` branch with:

- `git push -u origin test/v1-pending-message-queueing`

That first failed over HTTPS because the stored credential resolved to the wrong GitHub identity, and it failed again after switching the remote to SSH:

- `ERROR: Permission to jessicalang2595/OpenHands.git denied to SreytouchLang.`

Because the branch is not on GitHub, I cannot truthfully open the upstream PR yet.

---

## Maintainer Feedback

**Maintainer Feedback:** None yet.

No upstream PR has been opened, so there are currently no maintainer comments, requested changes, or approval states to report.

---

## Status

**Current Status:** Not yet submitted; blocked before review.

This means I am not marking this contribution as `Awaiting review`, `Iterating`, `Approved`, or `Merged` yet. The accurate current state is:

- PR draft prepared
- local branch ready
- local commit ready
- push blocked by GitHub account/repository ownership mismatch

---

## Summary of Contribution

My Week 4 contribution work focused on preparing a professional PR-ready submission package for the `OpenHands` test coverage I added in Week 3:

- I confirmed the contribution branch, commit, diff scope, and targeted test results.
- I checked the upstream repository's real PR template.
- I drafted the PR title and full PR description in the format OpenHands expects.
- I documented why the PR is not yet submitted and what must happen next.
- I verified that SSH authentication on this machine works, but only for the `SreytouchLang` GitHub account.

---

## Next Steps

To complete Phase IV for real, I need to do these in order:

1. Use a GitHub login or SSH key that has write access to the `jessicalang2595` repositories, or grant `SreytouchLang` collaborator access to them.
2. Open the upstream PR from my fork branch into `OpenHands/OpenHands:main`.
3. Update this README with the actual PR link.
4. Document any maintainer feedback and my follow-up changes.
5. Change the status to `Awaiting review`, `Iterating`, `Approved`, or `Merged` once that becomes true.

At the moment, this README is an accurate Phase IV preparation record, but not yet a Phase IV completion record.
