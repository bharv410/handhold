# /handhold

**A Claude Code skill: Claude does the task itself. When it needs you, you get exactly one step, and it waits for "done".**

I typed "walk me through this like I'm 10" into Claude Code 20+ times before I turned it into a skill.

## The problem

Ask an AI to help you set up an account, a portal, a DNS record, a developer console:

```
1. Go to the dashboard and click Settings
2. Under Security, enable two-factor
3. Scan the QR code, then enter the code
4. Now go to API Keys and...
   (10 more)
```

You do step 2, the page looks different from what it described, and you are now scrolling a wall of text with a phone in one hand.

## What /handhold does instead

```
> /handhold turn on 2FA for my registrar account and add the TXT record for domain verification

  (Claude opens the registrar, navigates to Security, starts the 2FA flow)

Claude: Open your authenticator app and scan the QR code on screen. Say "done".
> done

  (Claude re-reads the page, confirms the code prompt is showing)

Claude: Type the 6-digit code into the "Verification code" box. Say "done".
> done

  (Claude confirms 2FA is on, goes to DNS, adds the TXT record, saves, checks it resolves)

Claude: 2FA is on and the TXT record is live. Verification usually completes within an hour.
```

The contract, in five rules:

1. **Claude does it first.** Navigation, form filling, clicking, config. You only get pulled in for real blockers: 2FA codes, Face ID, payment confirmations, passwords it doesn't have.
2. **One step per message.** Two sentences max. Exact button label, exact URL, exact field name. Then it stops.
3. **It verifies before moving on.** After you say "done", it re-reads the page instead of trusting you.
4. **It doesn't stop early.** No "want me to continue?".
5. **It ends with one line.** What got done, and what to watch for.

The whole skill is [19 lines](skills/handhold/SKILL.md).

## Install

As a plugin, inside Claude Code:

```
/plugin marketplace add bharv410/handhold
/plugin install handhold@handhold
```

Or copy the file:

```bash
mkdir -p ~/.claude/skills/handhold
curl -fsSL https://raw.githubusercontent.com/bharv410/handhold/main/skills/handhold/SKILL.md \
  -o ~/.claude/skills/handhold/SKILL.md
```

## Use

```
/handhold set up Stripe payouts to my bank
/handhold renew my domain and turn on auto-renew
/handhold get me an API key from the Google Cloud console
```

It also triggers on plain language: "walk me through this like I'm 10", "tell me exactly what to do".

## Requirements

For Claude to do the steps itself it needs a way to drive the screen, for example [Claude in Chrome](https://claude.com/chrome) or a desktop-control MCP server. Without one, the skill still works as a strict one-step-at-a-time walkthrough.

## License

MIT
