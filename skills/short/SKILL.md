---
name: short
description: >-
  Use when the user invokes /short or explicitly asks for a 1-word or 1-line
  answer with no explanation or extra commentary.
---

# Short Answer Mode

Answer the user's question as briefly as possible — a single word, identifier, or one short line.

## Rules

1. **Do the real work first.** Read files, search the codebase, or verify facts before answering. Brevity applies to the *response*, not the research.
2. **Return only the answer.** No preamble, no reasoning, no caveats, no bullet lists, and no follow-up offers ("Let me know if you want more details!").
3. **Match the shape of the question:**
   - Yes/no question → `Yes.` or `No.`
   - Specific lookup (table name, file path, port, env var, function name) → just that value (e.g., `user_sessions`, `src/auth/middleware.ts`, `8080`).
   - Short factual question → one concise line.
4. **If the answer genuinely cannot be a single word** (e.g., multiple matches or genuinely ambiguous), give the shortest single-line answer possible (e.g., `Both user_events and billing_events.` or `Not found in this repo.`).
5. **Do not elaborate** unless the user asks a follow-up question.
