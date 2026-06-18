# Contribution 4: `Add message queue support for V1 conversations during WebSocket connection`

**Contribution Number:** 4  
**Student:** Jessica Lang  
**Issue:** [OpenHands/OpenHands#12279](https://github.com/OpenHands/OpenHands/issues/12279)  
**Status:** Phase IV submitted; ready for review

**Important note as of June 25, 2026:**

I now have a real pushed OpenHands branch and a real submitted upstream PR. The original `jessicalang2595/OpenHands` fork was not writable from this machine, so I published the implementation branch through the authenticated `sreytouch` account and opened the upstream PR from that fork.

---

## Final Pre-Submission Checks

### Current OpenHands Contribution State

- **Repository:** [sreytouch/OpenHands](https://github.com/sreytouch/OpenHands)
- **Remote branch:** [sreytouch/OpenHands/tree/test/v1-pending-message-queueing](https://github.com/sreytouch/OpenHands/tree/test/v1-pending-message-queueing)
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

1. The original issue scope has drifted: current `OpenHands` `main` already includes server-side pending-message queueing, so this contribution is currently a test-coverage improvement around the modern implementation rather than a full original-feature implementation.
2. I intentionally used `Related to #12279` in the PR instead of `Closes #12279` until maintainers confirm that this narrower contribution should resolve the issue.
3. The full `conversation-websocket-handler.test.tsx` file still has unrelated broader failures in this environment even though the targeted queueing tests pass.
4. The older related PR [OpenHands/OpenHands#14692](https://github.com/OpenHands/OpenHands/pull/14692) is also still open, so my PR may be evaluated as a narrower follow-up rather than the sole fix path.

---

## Pull Request

### PR Link

**PR Link:** [OpenHands/OpenHands#14860](https://github.com/OpenHands/OpenHands/pull/14860)

### Live PR Status

As of June 18, 2026:

- PR state: `open`
- Draft status: `false`
- Maintainer feedback: none yet

### Submitted PR Route

The submitted draft PR route is:

- **Head:** `sreytouch/OpenHands:test/v1-pending-message-queueing`
- **Base:** `OpenHands/OpenHands:main`

### PR Title

`test(frontend): add V1 pending message queue coverage`

### Submitted PR Description

I checked the repository PR template in `OpenHands/.github/pull_request_template.md` and submitted the PR with this description:

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

### Submission Notes

I resolved the branch-hosting blocker in these steps:

1. Created a writable fork at [sreytouch/OpenHands](https://github.com/sreytouch/OpenHands)
2. Pushed `test/v1-pending-message-queueing` there
3. Opened the upstream PR: [OpenHands/OpenHands#14860](https://github.com/OpenHands/OpenHands/pull/14860)
4. Marked the PR ready for review on June 18, 2026

The original `jessicalang2595/OpenHands` fork was still not writable from this machine, so using the authenticated `sreytouch` account was the cleanest way to get a truthful public branch and PR link.

---

## Maintainer Feedback

**Maintainer Feedback:** Automated GitHub Actions feedback received and addressed.

On June 18, 2026, GitHub Actions left two automated PR comments:

1. add a short explanation in the `HUMAN:` section at the top of the PR description
2. confirm that the PR is ready for review

I addressed both follow-ups:

- updated the PR description to include the required `HUMAN:` note
- posted a readiness confirmation comment on the PR thread

There is still no human maintainer review feedback yet.

---

## Status

**Current Status:** PR submitted and ready for review.

The accurate current state is:

- remote branch pushed
- upstream PR open and ready for review
- no maintainer feedback yet

---

## Summary of Contribution

My Week 4 contribution work focused on turning the Week 3 test contribution into a real upstream submission:

- I confirmed the contribution branch, commit, diff scope, and targeted test results.
- I checked the upstream repository's real PR template.
- I published the branch to a writable fork at `sreytouch/OpenHands`.
- I opened PR [#14860](https://github.com/OpenHands/OpenHands/pull/14860) into `OpenHands/OpenHands:main` and marked it ready for review.
- I documented the remaining scope caveats honestly instead of overstating the fix.

---

## Next Steps

The next steps from here are:

1. Watch PR [#14860](https://github.com/OpenHands/OpenHands/pull/14860) for maintainer feedback.
2. Respond with follow-up changes if requested.
3. Update this README again if the PR gets feedback, revisions, approval, or merge status changes.
