# Customer Solutions Claude skills

Snapshot of the Customer Solutions skills for impact.com, taken 2026-11-19.

Internal use only. These skills reference internal Slack channels, Jira queues, and Operator details. Do not share outside impact.com.

## What is here

The .claude/skills folder holds one folder per skill, each with a SKILL.md and, where present, a references folder. Some items are still open decisions and are flagged inside the skill files.

## Option 1: Claude Code (recommended)

Claude Code loads project skills from the .claude/skills folder, so this is the simplest route.

1. Install Claude Code if you don't have it, and make sure you can sign in with your impact.com account.
2. Clone the repository: git clone https://github.com/tabor-impact-stack/TBrepo.git
3. Open the TBrepo folder in Claude Code, or run claude from inside it.
4. Ask Claude to list its skills. The Customer Solutions skills should appear.

To pull updates later, run git pull inside the TBrepo folder.

## Option 2: Claude app (copy each skill)

The Claude app doesn't load skills from GitHub, so each person adds them to their own account.

1. Open the .claude/skills folder in this repository on GitHub.
2. For each skill, open its SKILL.md, copy the full text, and add it as a skill in your Claude account. Use the same name as the folder.
3. Copy the references folder for a skill too, if it has one, and check that the skill still works.

If you can't find where to add skills in your account, ask your Claude admin or Tabor.

## Updating

These are copies. When a skill changes in the source account, Tabor will refresh this folder and commit the update. Pull the latest version before you rely on a skill.
