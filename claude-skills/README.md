# Claude Skills

Installable skills for focused LinkedIn jobs. Each folder contains one `SKILL.md` entry point with the workflow, quality checks, and output contract Claude follows.

## Install a skill in Claude Code

Choose one skill folder, then copy the complete folder to one of these locations:

- Personal use across all projects: `~/.claude/skills/<skill-name>/`
- One project only: `.claude/skills/<skill-name>/`

Example:

```bash
mkdir -p ~/.claude/skills
cp -R claude-skills/linkedin-about-section-writer ~/.claude/skills/
```

Start Claude Code after copying the folder. Claude can activate the skill automatically when your request matches its description, or you can invoke it directly:

```text
/linkedin-about-section-writer
```

Claude Code watches existing skill directories for changes. If this is the first skill directory created during an active session, restart Claude Code so it can discover the directory.

Official documentation: [Extend Claude with skills](https://code.claude.com/docs/en/skills)

## Use a skill from this repository without installing it

Give Claude access to the repository, point it to the selected `SKILL.md`, and ask it to follow that skill for the task. Installing the folder is better for repeated use because Claude can discover it automatically.

## Available skills

| Skill | Best for | Starter prompt |
|---|---|---|
| [LinkedIn About Section Writer](linkedin-about-section-writer/SKILL.md) | Writing one conversion-focused About section | `Write my LinkedIn About section from these positioning notes and keep my voice.` |
| [LinkedIn Case Study Builder](linkedin-case-study-builder/SKILL.md) | Turning verified outcomes into proof assets | `Build a LinkedIn case study from these client notes. Mark anything that needs confirmation.` |
| [LinkedIn Comment to DM Bridge](linkedin-comment-to-dm-bridge/SKILL.md) | Deciding if a public interaction should move to DMs | `Review this post and comment exchange. Should I reply publicly, DM, or stop?` |
| [LinkedIn Company Page Optimizer](linkedin-company-page-optimizer/SKILL.md) | Auditing and rewriting a Company Page | `Audit this LinkedIn Company Page and give me the three highest-impact fixes.` |
| [LinkedIn Connection Request Writer](linkedin-connection-request-writer/SKILL.md) | Writing relevant 200 or 300 character notes | `Write a connection request for this prospect and tell me if no note is better.` |
| [LinkedIn Content Engine](linkedin-content-engine/SKILL.md) | Turning a new idea into a founder-led post | `Turn this idea into a LinkedIn post for my ICP in my voice.` |
| [LinkedIn Content Repurposing Engine](linkedin-content-repurposing-engine/SKILL.md) | Extracting distinct assets from an existing source | `Repurpose this transcript into a source-traceable LinkedIn content package.` |
| [LinkedIn DM Writer](linkedin-dm-writer/SKILL.md) | Writing warm DMs and follow-ups after contact | `Write the next DM in this conversation without pitching too early.` |
| [LinkedIn Featured Section Builder](linkedin-featured-section-builder/SKILL.md) | Turning proof and resources into a focused Featured sequence | `Audit these assets and build my first three LinkedIn Featured items.` |
| [LinkedIn ICP Finder](linkedin-icp-finder/SKILL.md) | Defining an ICP and practical search filters | `Turn this offer and customer evidence into a focused LinkedIn ICP.` |
| [LinkedIn Lead Scorer](linkedin-lead-scorer/SKILL.md) | Ranking prospects against a defined ICP | `Score these prospects against my ICP and explain every disqualifier.` |
| [LinkedIn Positioning Coach](linkedin-positioning-coach/SKILL.md) | Clarifying and pressure-testing positioning | `Build and pressure-test my positioning from these customer notes.` |
| [LinkedIn Profile Optimizer](linkedin-profile-optimizer/SKILL.md) | Auditing the complete personal profile | `Audit my LinkedIn profile and rewrite the weakest sections first.` |

## Choose the right skill

- Use the **Profile Optimizer** for the full personal profile and the **About Section Writer** for a deeper About-section draft.
- Use the **Content Engine** when starting from an idea and the **Content Repurposing Engine** when starting from an existing source.
- Use the **Featured Section Builder** to choose and order proof assets, and the **Case Study Builder** when the proof asset still needs to be created.
- Use the **Connection Request Writer** before connection, the **Comment to DM Bridge** for a public-to-private transition, and the **DM Writer** after a real private conversation begins.
- Use the **ICP Finder** to define fit and the **Lead Scorer** to evaluate actual prospects against that fit.

## Get better outputs

1. Provide source material instead of asking Claude to guess.
2. Include your ICP, objective, and natural voice when relevant.
3. Label confidential details before sharing them.
4. Verify claims, customer names, quotes, and metrics before publishing.
5. Treat the first result as a working draft and give specific feedback.

## Safety and accuracy

These skills are designed to mark missing evidence instead of inventing it. You remain responsible for checking claims, permissions, platform limits, and final copy before using an output publicly.
