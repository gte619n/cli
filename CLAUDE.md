When contributing to this repository, you must strictly follow all guidelines outlined in the AGENTS.md file.

## DRAFTS-ONLY FORK

This is a **drafts-only** fork of `googleworkspace/cli`. All email composition creates Gmail drafts — sending is disabled at three layers:

1. **Helper layer:** `+send` removed, replaced with `+draft`. `+reply`, `+reply-all`, `+forward` all create drafts.
2. **Command tree:** `users.messages.send` and `users.drafts.send` are filtered from the Discovery Document command tree.
3. **Runtime guard:** Even if a method resolves to `messages/send` or `drafts/send`, it is blocked before execution.
4. **OAuth scope:** Uses `gmail.compose` instead of `gmail.modify` — Google's API rejects send calls with this scope.

**Never re-introduce `messages.send` or `drafts.send` paths. Never change the OAuth scope back to `gmail.modify`.**
