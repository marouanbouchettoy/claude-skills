# 🧠 Claude Skills

> A collection of custom skills that supercharge Claude AI — making it smarter, more specialized, and more powerful for real-world tasks.

---

## What Are Claude Skills?

**Skills** are structured instruction files (`.skill` or `SKILL.md`) that you provide to Claude via its system prompt or context. They teach Claude *how* to behave for a specific task — what tools to use, what quality bar to hit, and what pitfalls to avoid.

Think of them as reusable "expert modes" you can plug into any Claude session.

---

## 📦 Skills in This Repo

| Skill | Description |
|---|---|
| `frontend-design.skill` | Build production-grade UIs with high design quality — no generic AI aesthetics |
| `humanizer.skill` | Rewrite AI-generated text to sound naturally human |
| `file-organizer.skill` | Intelligently organize, rename, and sort files |
| `redis-development.skill` | Best practices for Redis schema design and development |
| `sql-to-accdb.skill` | Convert SQL scripts to Microsoft Access (.accdb) format |

---

## 🚀 How to Add Skills to Claude

---

### ⭐ Method 1 — Upload from Device (Easiest & Fastest)

No coding required. Works directly in [claude.ai](https://claude.ai).

**Step 1 — Download this repo as a ZIP**

Click the green **`<> Code`** button on this GitHub page → **Download ZIP**

Or use this direct link:
```
https://github.com/marouanbouchettoy/claude-skills/archive/refs/heads/main.zip
```

**Step 2 — Extract the ZIP** on your device. You'll get a folder with all the `.skill` files.

**Step 3 — Open Claude.ai and go to the Skills tab**

1. Go to [claude.ai](https://claude.ai)
2. In the left sidebar, click **Skills**
3. Click **"Add new skill"** (or the **+** button)
4. Choose **"Upload from device"**
5. Select the `.skill` file(s) you want from the extracted folder
6. Done! ✅ Claude now has access to that skill in your session.

> 💡 **Tip:** You can upload multiple skills one by one to stack them together.

---

### Method 2 — Paste into the System Prompt (Claude API)

1. Copy the contents of any `.skill` file from this repo.
2. Paste it at the top of your **system prompt** when calling the Claude API.
3. Claude will follow the skill's instructions automatically.

```python
import anthropic

with open("frontend-design.skill", "r") as f:
    skill = f.read()

client = anthropic.Anthropic()
message = client.messages.create(
    model="claude-sonnet-4-20250514",
    max_tokens=1024,
    system=skill,  # 👈 skill goes here
    messages=[
        {"role": "user", "content": "Build me a dashboard with a sidebar and stats cards."}
    ]
)
print(message.content)
```

---

### Method 3 — Use in Claude.ai Projects

1. Go to [claude.ai](https://claude.ai) and open or create a **Project**.
2. Click **"Set instructions"** (the project system prompt area).
3. Paste the skill content there.
4. Every conversation in that project will now use the skill automatically.

---

### Method 4 — Add as a File in Claude Code

If you're using [Claude Code](https://claude.ai/code) (the CLI tool):

1. Place your `.skill` file inside your project directory.
2. Reference it in your `CLAUDE.md` file or pass it as context:

```bash
# Example: tell Claude Code to read the skill
cat frontend-design.skill | claude "Now build me a landing page component"
```

Or add it to your project's `CLAUDE.md`:

```markdown
## Skills

@frontend-design.skill
```

---

## ✍️ How to Create Your Own Skill

A skill file is a plain text or Markdown file with:

1. **A frontmatter header** (optional but recommended) — name, description, license.
2. **Context** — what this skill is for, and when Claude should use it.
3. **Instructions** — the specific rules, patterns, tools, or quality standards Claude should follow.
4. **Examples** (optional) — sample inputs/outputs to anchor Claude's behavior.

### Minimal Skill Template

```markdown
---
name: my-skill-name
description: One sentence describing what this skill does and when to use it.
---

## Purpose

Explain what task this skill handles and what makes a great output.

## Instructions

1. Always do X before Y.
2. Use Z library/approach for this task.
3. Avoid the common mistake of...

## Quality Bar

The output should be... [describe the standard]

## Example

Input: ...
Output: ...
```

Save the file as `my-skill-name.skill` and add it to this repo via a pull request!

---

## 🤝 Contributing

Have a skill that makes Claude dramatically better at something? Contributions are welcome!

1. Fork this repo.
2. Add your `.skill` file to the root (or a subfolder if it includes multiple files).
3. Open a Pull Request with a short description of what your skill does.

Please make sure your skill:
- Has a clear, specific purpose
- Is tested with Claude Sonnet or Opus
- Doesn't include harmful, misleading, or unethical instructions

---

## 📜 License

MIT — use these skills freely in your own projects.

---

> **Remember:** Use AI responsibly. These skills are tools — use them to build, create, automate, and explore. Make Claude your superpower. ⚡