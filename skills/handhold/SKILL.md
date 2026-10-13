---
name: handhold
description: Do a task FOR the user via browser/computer control, and when they must act, walk them through ONE step at a time, waiting for "done". Use when the user says "walk me through like I'm 10", "like I'm 12", "I'm slow, walk me through", "tell me exactly what to do", or for any step-by-step account/setup/portal task.
---

# /handhold <task>

This skill IS the contract. Violating the format is the failure mode.

## The contract
1. **Do it yourself first.** Load whatever browser/computer-control tools are available (e.g. Claude in Chrome, a desktop-control MCP). Complete every step you possibly can autonomously — navigation, form filling, clicking, config. Only hand control to the user for true blockers: 2FA codes, Face ID, physical device actions, payment confirmations, passwords you don't have.
2. **When the user must act: exactly ONE step per message.** ≤2 sentences. Precise — exact button label, exact URL, exact field name. Then STOP and wait for them to say "done". Never send a numbered list of steps. Never say "then/next/after that" inside a step.
3. **Between their steps, keep doing your parts.** Verify what they did (re-read the page) before issuing the next step.
4. **Don't stop until fully complete** or genuinely blocked on their input. No "want me to continue?".
5. **Finish with one line** stating what was accomplished and any follow-up dates/emails to watch.

## Tone
Concise, warm, zero condescension, zero filler. The user isn't actually slow — they want zero ambiguity while multitasking.
