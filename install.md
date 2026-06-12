# Install — PM Savior Skills

Manual setup. No scripts. Copy the skills you want into Claude Code's skills directory.

## Prerequisites

- [Claude Code](https://claude.ai/code) installed and authenticated
- macOS or Linux (Windows: adjust paths below to `%USERPROFILE%\.claude\skills\`)

---

## Step 1 — Locate your Claude skills directory

```
~/.claude/skills/
```

If it doesn't exist yet, create it:

```bash
mkdir -p ~/.claude/skills
```

---

## Step 2 — Copy skills

Copy each skill folder you want from `skills/` into `~/.claude/skills/`.

**Copy all skills at once:**

```bash
for skill in ~/pm-savior/skills/*/; do
  skill_name=$(basename "$skill")
  if [ -d ~/.claude/skills/"$skill_name" ]; then
    echo "SKIP $skill_name — already exists (delete it first to reinstall)"
  else
    cp -r "$skill" ~/.claude/skills/
    echo "INSTALLED $skill_name"
  fi
done
```

**Or copy a single skill:**

```bash
cp -r ~/pm-savior/skills/pm-plan ~/.claude/skills/
```

**To overwrite an existing skill (reinstall/upgrade):**

```bash
rm -rf ~/.claude/skills/pm-plan
cp -r ~/pm-savior/skills/pm-plan ~/.claude/skills/
```

---

## Step 3 — Verify

Open Claude Code in any directory and type `/` — you should see `pm-plan`, `pm-brainstorm`, etc. in the skill list.

---

## Updating

Pull the latest version and re-copy changed skills:

```bash
cd ~/pm-savior && git pull
# Then re-copy any skills you want to update (see "overwrite" step above)
```

---

## Uninstall

Delete any installed skill from `~/.claude/skills/`:

```bash
rm -rf ~/.claude/skills/pm-brainstorm
# repeat for each skill
```
