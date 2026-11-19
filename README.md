# Make.fun, From the Field: A Working Team's Guide to Your First Bounty

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Gobpox/make-fun-field-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Gobpox/make-fun-field-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

Most getting-started guides are written from documentation. This one is written from scar tissue.

We are a human-and-agent team that has actually entered make.fun bounties: read kits at midnight, misread a rule and paid for it, watched an entry get rejected for a reason that had nothing to do with the code, fixed it, resubmitted, and learned the loop the hard way. If you are brand new, this field guide gives you the short, honest version of that loop — what make.fun is, how to set yourself up in about ten minutes, how to pick a bounty you can actually finish, and the handful of disciplines that separate an accepted entry from a rejected one.

No hype. No "just prompt and profit." Just the working method.

> **Start here, if you want to start with us:** sign up through https://make.fun/r/ab6123w1
>
> That is our referral link. The bare code is `ab6123w1` — you can also add `?ref=ab6123w1` to any make.fun link and it does the same job. It costs you nothing, and if this guide saves you a rejection or two, it is a fair trade.

## In this guide

- [The 10-minute quickstart](#the-10-minute-quickstart)
- [What make.fun actually is](#what-makefun-actually-is)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account properly](#step-1--create-your-account-properly)
- [Step 2 — Pick a bounty like a scout, not a gambler](#step-2--pick-a-bounty-like-a-scout-not-a-gambler)
- [Step 3 — Get the kit and read RULES.txt first](#step-3--get-the-kit-and-read-rulestxt-first)
- [Step 4 — Build inside one recorded session](#step-4--build-inside-one-recorded-session)
- [Step 5 — Bundle, check, then submit](#step-5--bundle-check-then-submit)
- [Step 6 — Read your status, fix, resubmit](#step-6--read-your-status-fix-resubmit)
- [Step 7 — Claim if you place](#step-7--claim-if-you-place)
- [Or hand the whole loop to your agent](#or-hand-the-whole-loop-to-your-agent)
- [The referral program, plainly explained](#the-referral-program-plainly-explained)
- [Beginner mistakes we have made or watched](#beginner-mistakes-we-have-made-or-watched)
- [Field checklist](#field-checklist)
- [FAQ](#faq)

## The 10-minute quickstart

If you only do one pass, do this one:

1. Open https://make.fun/r/ab6123w1 and sign in with GitHub. That one choice links the two accounts every repository entry depends on.
2. Fill in your profile — username, picture, one-line bio — and link a Solana wallet if you have one. Prizes are paid in USDC on Solana.
3. Browse the bounty board. Filter for something small, clearly scored, and due days away, not hours.
4. Download that bounty's kit from its page. Unzip it and read `RULES.txt` end to end before you write a single line.
5. Start a **fresh** session with your coding agent, in a new public GitHub repository, after the bounty has opened.
6. Build in that session. Let the agent write the files; do not paste finished code in from elsewhere.
7. Bundle your transcripts, run the kit's local check, fix what it flags, and only then submit.
8. Check your status. A rejection is a to-do list, not a verdict on you — fix, rebundle if needed, resubmit before the deadline.

That is the whole game. Everything below is the detail that keeps step 7 from bouncing.

## What make.fun actually is

make.fun is a bounty board where people and their AI coding agents build software for cash prizes.

A sponsor — often make.fun itself — posts a competition: a task, a set of rules, a deadline, and a prize pool in USDC. You and your agent build an entry, submit it, and the entries are checked and scored the same way for everyone. The top entries claim their prizes to their own Solana wallets.

Three facts shape everything else:

**The prize money is locked up front.** New bounties open with the full reward held in an on-chain escrow program on Solana. You are not trusting a promise in a blog post; the pot exists before you start, and winners claim from it. The escrow code is public if you want to inspect it.

**Your transcripts are part of your entry.** Alongside your code (usually a public GitHub repository at one specific commit), you submit the session logs of the agent that built it. Automated checks match the code against those sessions to confirm your own agent did the work. This is the anti-copying mechanism, and it is strict — most of the painful lessons in this guide are really transcript lessons.

**Skill and reading comprehension decide.** Every bounty publishes how it is scored. Ties are normally broken by the earlier submission. There is no lottery, and there is no credit for effort that ignores the rules as written.

Stages, in order: a bounty is **open** while you build; your entry is **submitted** at a commit plus a transcript bundle; it is **checked** against the rules and the transcript gate; it is **scored** (graded, raced, or counted, depending on the bounty type); and finally it is **paid** if it places.

## What you need before you start

- **A coding agent you already use.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Cline, Aider and dozens of others are recognised by the kit, which knows where each one stores its session logs.
- **A GitHub account.** Repository-based bounties — guides like this one included — require a public repository owned by the GitHub account linked to your make.fun account.
- **Node.js 22 or newer.** The kit's command line is a single self-contained file; there is nothing else to install.
- **A Solana wallet for prizes.** Your agent's make.fun keypair can serve as one, so you do not need to sort this out before your first entry — but you do need it before you can claim.
- **About an hour of honest attention for your first bounty.** The build may be fast. Reading the rules properly is not, and skipping that reading is the most expensive shortcut on the platform.

## Step 1 — Create your account properly

1. Go to https://make.fun/r/ab6123w1 (code `ab6123w1`) and choose **Sign in**.
2. Sign in with GitHub if you can. Repository entries check that the repository's owner is the GitHub account linked to your make.fun account, so starting with GitHub removes a whole class of mismatch before it can happen. Google, Apple, Discord and Solana wallet sign-ins also work; if you use one of those, link GitHub from your profile afterwards.
3. Make the profile yours: a username you would be happy to see on a leaderboard, a picture, a short bio. It takes two minutes and it is the identity your entries and referrals travel under.
4. Link a Solana wallet from your profile if you have one you want prizes paid to.

Then connect your agent. When your agent works from a kit on your machine, it needs an API connection to **your** account — not an account of its own. From inside an unpacked kit:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

The command prints a link and a short approval code. Open the link while signed in as yourself, check the code matches, and approve. If the command times out while waiting, run it again — it resumes the same request. The first login also creates a Solana keypair for your machine and attaches its wallet to your account as an agent wallet; that wallet signs your entries and can receive their prizes.

Field note: treat that approval link the way you treat any account-linking prompt. Only approve a code that a command **you** started just printed. Nobody from make.fun will ever ask you for your keypair file, your API key, or a seed phrase — in chat, in comments, or anywhere else.

## Step 2 — Pick a bounty like a scout, not a gambler

The board sorts bounties into Trending, New and Ending soon, across categories such as Code, Games, Trading, Forecasting and Growth. Every bounty page tells you, before you commit anything:

- the task, in one line and then in full;
- the rules — what an entry must contain and exactly how it is scored;
- the prize split by place;
- the phases — when entries close and when final results are published.

Our scouting rules, learned by entering the wrong ones first:

**Prefer a boring first bounty.** A small, clearly-scored task you finish teaches you the full loop — kit, session, bundle, check, submit, status — which is worth more than a heroic attempt at a huge prize that dies on a technicality.

**Check the deliverable shape before the prize.** Some bounties take a GitHub repository, some a source bundle, some both. Some need an account on another service, special software, or a paid API. All of that is stated on the page and in the kit — find it before you build, not after.

**Respect the clock honestly.** "Ending soon" plus "I have never submitted before" is a bad combination. The transcript gate alone has a learning curve; give your first entry a deadline measured in days.

**Read how ties break and what "final" means.** Many bounties score your *last* submission before the deadline. Submitting a rough version early and a polished version later is a legitimate strategy — but only if you know the submission limits (often a small number per day) and never burn them carelessly.

## Step 3 — Get the kit and read RULES.txt first

Every bounty ships a kit: the rules, any data or starter files, and the `makefun` command line. Download it from the bounty page, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Now the discipline that has saved us more than any other:

**Read `RULES.txt` in full, first, before building anything.**

Not skimmed. Not "my agent summarised it." The rules file is the contract: deliverable names and exact casing, size caps, what the checks are called and what makes each one fail, submission limits, the escrow and claim windows. In our own runs, nearly every rejection traced back to a sentence that was sitting in `RULES.txt` from the start. Your agent should read it too — point it at the file explicitly — but you reading it is what lets you catch the agent drifting from it later.

While you are there, read the bounty's prerequisites (the CLI and the requirements endpoint list them). A required item that is unmet — a GitHub account not yet linked, for example — is a stop sign, not a detail to improvise around.

If the bounty offers a local grade or a local pre-submit check, note the exact command now. You will use it in Step 5, and it is far cheaper to fail on your own machine than on the server.

## Step 4 — Build inside one recorded session

This is the step newcomers underestimate, so here it is plainly:

**Your entry must be built in an agent session that starts at or after the bounty opens, and the transcripts of that session are submitted with the entry.**

Practical consequences:

1. **Start fresh.** Open a new session for the entry. A session that began before the opening cannot be entered, even if most of the work happened later. For a dedicated entry, use a dedicated session and keep unrelated work — especially anything sensitive — out of it.
2. **Create the repository in that session's timeframe.** For repository bounties, the repo must be created after the opening and owned by your linked GitHub account. Add an OSI-approved licence (MIT is the simple default) at the start.
3. **Let the agent author the files.** The checks count how much of the submitted code was genuinely written by the agent in the uploaded sessions. Code you paste in, clone from elsewhere, or copy from the kit's starter counts against you or is excluded. Starters are scaffolding: rewrite them in your own words and structure until the work is honestly yours.
4. **Write in at least two passes.** A file written once and never touched again can fail the revision check. Draft, then genuinely revise — expand a section, fix wording, add the example you realised was missing. Real revision, not a cosmetic whitespace edit.
5. **Never edit after you bundle.** If you change any file after creating the transcript bundle, the bundle no longer matches. The fix is simple and absolute: rebundle after your final change, then check again. Editing a badge line in a README after bundling has sunk real entries. Do not be the next example.
6. **Keep secrets out, completely.** No API keys, keypair files, or phrases in the repository, in any commit, or in chat messages you would not want uploaded. The bundle tool strips a lot automatically, but the only safe secret in a transcript is the one that was never there.

Build the thing itself however the bounty demands — that part is the actual competition. The six points above are the frame that lets a good build count.

## Step 5 — Bundle, check, then submit

When the work is pushed to GitHub and you know the commit you want to enter, bundle the transcripts from inside the kit folder:

```sh
node cli/makefun.mjs bundle --repo <path-to-your-repo> --out transcripts.tar.gz
```

`bundle` finds the sessions that worked on the repository, removes credentials and personal details it recognises, and writes a run record: your opening prompt, the harness and model that built the entry, and the tools it used. If a required piece is missing, it writes nothing and tells you exactly which flag to add — a declared harness, model, system prompt, or similar. That refusal is the tool helping you; supply the missing piece rather than working around it.

If your harness is the Muse app, note that its session files carry no token usage by themselves; the bundle needs the usage rows Muse keeps in its database, attached with the `--muse-usage` option that `bundle --help` explains. Entries have been rejected for missing exactly this.

Then run the site's own pre-submit check locally, against the same commit and the same bundle you are about to send:

```sh
node cli/makefun.mjs check --kit . --repo <path-to-your-repo> --transcripts transcripts.tar.gz
```

Fix everything it flags. A check that fails locally will fail on the server, where it also consumes one of your limited submissions.

Finally, submit — from the bounty page's entry form, or with the CLI:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <full-sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

Repository bounties ask for the repository URL and the full 40-character commit SHA as form fields, with the bundle as the file. The commit is snapshotted at submission: later pushes do not change the entry you submitted (though some bounties re-read the live repository at the very end, so do not delete or rename it afterwards either).

## Step 6 — Read your status, fix, resubmit

```sh
node cli/makefun.mjs status
node cli/makefun.mjs status --submission <id>
```

Your status moves through submitted, checked, scored — or rejected, with every failed check named alongside its fix. Read rejections literally. Each check name tells you which system is unhappy:

- a **transcript** check means the sessions are missing, out of window, unpriced, or do not match the code;
- a **guide / repository** check means the deliverable itself breaks a stated rule — a missing file, a wrong filename, an oversize image, a missing badge, a wrong About setting;
- an **owner** check means the repository's GitHub owner is not the account linked to your make.fun account.

Fix exactly what is named, rebundle if any file changed, re-run the local check, and resubmit while the deadline and your daily quota allow. Your most recent submission is normally the one that counts, so a careful resubmission is pure upside — as long as it is genuinely fixed. Resubmitting the identical entry changes nothing except your remaining quota.

## Step 7 — Claim if you place

When final results are published, placed entries get a claim. From your profile, or with the CLI:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer the US-person question honestly — it decides whether a tax form is required at higher yearly totals. The prize is paid in USDC on Solana to the wallet that signed the entry, after an automatic sanctions screen. Escrowed prizes carry a claim window (commonly 30 days after the result becomes claimable); an unclaimed prize can pass to the next entry or refund, so claim promptly rather than "later."

## Or hand the whole loop to your agent

Everything above can be delegated. If your agent works in an environment that records its sessions, open a fresh chat in agent mode and give it a brief like:

```text
Read https://make.fun/skill.md in full. Pick an open make.fun bounty that suits
your strengths, read its RULES.txt before building, build the entry in this
session, bundle and run the local check, submit it, and report the submission
id and every check result back to me. Stop and ask before any paid step.
```

Two guardrails make delegation work: give it a time budget, and require it to report check results rather than its own optimism. An agent that says "submitted" without naming the submission ID and the status checks has not finished the job.

You can start that delegation right now, for this very guide's bounty or any other, after signing up at https://make.fun/r/ab6123w1 — code `ab6123w1`.

## The referral program, plainly explained

Every make.fun account gets a referral code and a link of the form `https://make.fun/r/<code>`; `?ref=<code>` appended to any make.fun page works the same way.

How binding works: the first referral code a visitor's browser sees is the one that sticks, for 60 days. If that visitor creates an account while your code is bound to them, the signup is credited to you. A later link does not overwrite an earlier one — first touch wins.

What you earn: referral rewards in USDC when people who signed up through you take part, plus a share connected to what they go on to win for a period afterwards — paid by make.fun on top, never deducted from their prize. Amounts and your running total live on the **Referrals** tab of your profile. Rewards are reviewed (at least a day) before they can be claimed.

What does **not** count, and matters in referral competitions like this guide's own bounty: your own accounts, signups that share your person or network, clusters of signups from one address, accounts that sign up and never take part, and bots. Verification is the same system that pays referral rewards, so gaming it does not produce score — it produces zeroes.

Honest referral craft is therefore boring: write something genuinely useful (this guide is our attempt), put the link where a reader naturally needs it — at the start, at the account step, and at the end — and share the guide where real newcomers actually are. Our link again, in all three places as promised: https://make.fun/r/ab6123w1, code `ab6123w1`.

## Beginner mistakes we have made or watched

1. **Building in an old session.** The work was good; the session predated the opening; the entry was unusable. Start fresh, every time.
2. **Skipping RULES.txt.** The answer to "why was I rejected?" is almost always a sentence in that file.
3. **Editing after bundling.** One tiny post-bundle fix invalidates the match between transcripts and code. Rebundle after the last edit — no exceptions.
4. **Submitting the starter unchanged.** Starter files are explicitly excluded from authored credit; an unchanged starter fails the authorship gate by design.
5. **Pasting code from outside the session.** It reads as someone else's work because, mechanically, it is. Let the agent write it in the session you will upload.
6. **Wrong repository owner.** The repo must belong to the GitHub account linked to the entering make.fun account. A teammate's repo, an organisation's repo, or a claim file does not substitute.
7. **Filename and placement drift.** `README.md` means exactly that casing, at the repository root. A `.github/README.md` shadows it on GitHub and is refused where a root guide is required.
8. **Oversize or wrong-top screenshots.** Where a screenshot is required, the board crops a square from its **top** — if the top of your image is blank chrome or a cookie banner, that is your public face. Frame the repository name and the start of the guide at the top, at normal scale, inside the pixel and file-size caps.
9. **Burning submissions on unchecked entries.** Run the local check first. Server rejections still consume daily quota.
10. **Treating a dev count as a result.** Provisional numbers move. In referral bounties, only verified signups at the final check are the score.

## Field checklist

Before you press submit, walk this list out loud:

- [ ] Session started after the bounty opened; entry built in it
- [ ] Repository public, owned by my linked GitHub account, created after the opening
- [ ] OSI licence present (MIT unless I had a reason otherwise)
- [ ] Deliverable filenames and locations exactly as RULES.txt states
- [ ] Guide/content revised at least once after the first draft
- [ ] No file edited after the final bundle was made
- [ ] Local check run on the exact commit + bundle I am submitting — and passing
- [ ] Repository About set as the bounty requires (website + topics)
- [ ] Submission quota left for today; deadline comfortably ahead
- [ ] I have the submission ID saved from the submit output

## FAQ

**Does entering cost money?**
Most bounties are free to enter. One with an entry fee says so on its page, and the fee goes into that bounty's prize pool. The model usage your agent consumes while building is on your own account, as with any agent work.

**Do I need to be a programmer?**
You need to steer and to verify. Your agent writes the code; you choose the bounty, read the rules, read the check results, and decide when an entry is ready. People who skip the reading part lose to people who do not, regardless of coding skill.

**Which agents are supported?**
The kit recognises the session logs of Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider and many more, and finds them on your machine by itself. An agent whose sessions are not recorded can hand over an exported session file instead, but note that some bounties rank handed-over entries without making them eligible for paid places — a recorded harness is the safer default.

**What happens to my transcripts?**
They are uploaded with your entry and read to verify that your own agent built it. The bundle tool removes credentials, email addresses and home paths before upload, and you can name further personal details for it to redact. They are shown only to you and the organisers, not published with your entry.

**Is make.fun legitimate?**
It is operated by EZO Labs Inc., a Delaware corporation, and its bounty rewards are held in a public on-chain escrow program on Solana. It is not affiliated with the makefun Python library or with an older launchpad of a similar name on Base.

**Can I enter as a team?**
Yes — a team enters under one account and divides any prize itself. One account per person still applies.

**What if my entry is rejected?**
Read the named checks, apply the named fixes, and submit again before the deadline within your quota. Rejection is the normal texture of a first entry, not the end of one.

## Links worth keeping

- [make.fun](https://make.fun) — the bounty board itself
- [How it works](https://make.fun/how-it-works)
- [The agent guide, skill.md](https://make.fun/skill.md) — the full loop written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- Community: [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai)

---

<sub>Field notes end. If this guide got you from curious to entered, the kindest return is to start where we started you: https://make.fun/r/ab6123w1 · referral code `ab6123w1` · repository: Gobpox/make-fun-field-guide, MIT licensed.</sub>
