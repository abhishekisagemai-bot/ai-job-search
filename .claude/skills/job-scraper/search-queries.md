# Search Queries for Job Scraper

## Installed portal CLIs (primary for `/scrape`)

`/scrape` runs every enabled portal skill under `.agents/skills/*/SKILL.md`. For this India search, `linkedin-search` and `freehire-search` are enabled and the four Danish portals are disabled (`enabled: false`).

Use these CLI settings:
- **linkedin-search:** `--location "Bengaluru, Karnataka, India"` (repeat for `"Pune, Maharashtra, India"`, `"Hyderabad, Telangana, India"`, `"Noida, Uttar Pradesh, India"`, `"Gurugram, Haryana, India"`) and once with `--location "Remote"` plus "India" in the query. Use `--jobage 7`.
- **freehire-search:** `--country IN --jobage 14`, and `--category backend|fullstack|ml_ai`.

If a CLI cannot connect (for example in a sandbox whose network allowlist blocks it), fall back to WebSearch with the queries below and say so in the output.

**Language scope:** English only until languages are declared in CLAUDE.md.

## Query Categories (organized by function)

### Priority 1: Backend / Java

```
"java developer" OR "backend developer" OR "software engineer" Bengaluru 0-2 years
"spring boot" developer Bengaluru
"java" "kafka" engineer Bengaluru
site:linkedin.com/jobs "backend engineer" India
```

### Priority 2: Full stack

```
"full stack developer" Bengaluru 1-2 years
"full stack" angular OR node OR django Bengaluru
```

### Priority 3: AI / Gen AI engineer

```
"AI engineer" OR "Gen AI engineer" OR "generative AI" developer Bengaluru
"LLM" OR "RAG" engineer India junior
```

### Priority 4: Early career

```
"software engineer" "early career" OR "new grad" OR "entry level" India
"SDE 1" OR "SDE-1" OR "associate software engineer" Bengaluru
"software engineer intern" Bengaluru
```

Company career pages (via WebSearch `site:`) for named targets such as Google, Cisco, Rubrik, Navi, Angel One and HackerRank.

## Location Filter

Acceptable: Bengaluru (preferred), Pune, Hyderabad, Noida, Gurugram, and remote roles open to India. Exclude roles requiring relocation outside India or a work-authorization Abhishek lacks.

## Experience Filter

Target postings asking for roughly 0-2 years. Flag, don't auto-exclude, postings asking for 3 years. Exclude postings asking for 5+ years (for example SDE-2/Senior) unless the user asks to include them.

## Language Filter

Apply `04-job-evaluation.md`'s Language Gate using the Languages table in CLAUDE.md.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
