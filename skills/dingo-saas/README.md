# Run Dingo SaaS evaluations in natural language

The Dingo SaaS skill lets you manage datasets and metrics, run experiments, and analyze
reports through natural language. Just describe your evaluation goal — the agent finds the
resources, calls the Dingo SaaS API, and completes the steps in the right order.

## Before you start

All you need is a valid Dingo SaaS API key. Sign in to [Dingo SaaS](https://dingo.openxlab.org.cn),
go to `Dashboard → Settings` (`/dashboard/settings`), and create an API key. The full key is
shown only once at creation, so save it somewhere safe.

There are two ways to provide the key — pick one:

- **Environment variable (recommended, zero-config):** set `export DINGO_SAAS_API_KEY=<your-key>`
  in your shell. The agent reads it directly, with nothing written to disk.
- **Let the agent save it:** just tell the agent to connect. It asks you for the key and saves
  it to `~/.config/dingo-saas/config.json` (mode 600).

It connects to production `https://dingo.openxlab.org.cn` by default, so no URL is needed.

## Connect to Dingo SaaS

If `DINGO_SAAS_API_KEY` is set, just start using the skill — no connection step is required.
Otherwise, the first time you use it, say:

```text
Use $dingo-saas to connect to my Dingo SaaS.
```

The agent asks for your API key and saves the connection locally. Then verify it with a
read-only request:

```text
Check the connection and list my datasets, metric groups, and 5 most recent reports.
Don't modify anything.
```

Once connected, the agent returns resource names and IDs, but never shows the full API key
in its replies.

## Run your first full quality check

You can describe the entire goal in a single message:

```text
Upload assets/mineru_pdf.jsonl from the skill directory and create a "MinerU PDF extraction
results" dataset. From the existing metrics, list the ones suitable for checking PDF
extraction content quality and explain each one's criteria, then let me choose one.
After I pick, create and run the quality-check experiment. When it finishes, send me the report.
```

The agent works through it in order:

1. Upload the JSONL file and create the dataset.
2. Filter the existing metrics for suitable ones.
3. Create and start the experiment after you pick a metric.
4. Poll the status and send you the report once it completes.

When done, you get a result like:

| Item | Example |
| --- | --- |
| Dataset | MinerU PDF extraction results |
| Quality-check metric | PDF content completeness check |
| Experiment status | `success` |
| Report | MinerU PDF extraction quality test_20260914_093000 |
| Deliverable | Full quality-check report |

## More things you can do

```text
Preview the "MinerU PDF extraction results" dataset, tell me its fields, and show the first
3 records.
```

```text
If there's no suitable metric, draft a custom "PDF content extraction quality" metric.
Show me the criteria first — don't save it.
```

```text
Schedule the "MinerU PDF extraction quality test" experiment to run every weekday at 09:30,
timezone Asia/Shanghai.
```

```text
Find the most recent MinerU extraction quality report and send it to me.
```

There's more you can do with datasets, metrics, experiments, and reports through the skill.
See [SKILL.md](SKILL.md) for the full list of actions and execution constraints.
