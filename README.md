# MigoXLab Skills

Agent skills and Claude Code plugins published by [MigoXLab](https://github.com/MigoXLab).

Each skill teaches a coding agent (Claude Code / Cursor / Cline / Windsurf / ...) how to
operate a MigoXLab product through natural language.

## Available skills

| Skill | Description |
| --- | --- |
| [`dingo-saas`](skills/dingo-saas) | Operate [Dingo](https://dingo.openxlab.org.cn/) SaaS through conversation — datasets, metrics, experiments, and reports. |

## Install

**Any agent (skills.sh):**

```bash
npx skills add MigoXLab/skills --skill dingo-saas
```

**Claude Code (plugin marketplace):**

```bash
claude plugin marketplace add MigoXLab/skills
claude plugin install dingo-saas@migoxlab-skills
```

After installing, configure the connection once — see each skill's own README.
