# claude-skill-pe-esg-analysis

An open-source **Claude skill set** that produces institutional-grade **ESG analyses of private equity targets** — from a one-line verdict to a full, styled Word report. It is designed for deal screening and investment-committee work, and can be installed in any organisation.

**Version:** Beta 0.31 · **Licence:** Apache License 2.0 · Free to use, no attribution required.

This repository is a public, dated technical disclosure of the skill set (see *Prior art* below).

## What it does

Given the sources you provide for a deal (a document-store link, an information memorandum / CIM, an internal investment note, a company name, or a website), the skill produces an ESG analysis at one of three depths:

- **Ultra-short** — a one or two sentence verdict, keeping only the potentially problematic points (or stating that ESG issues are limited).
- **Short** — a one-pager under 2000 characters (Products / ESG risks / Governance) plus a complementary synthesis.
- **Long** — a full structured report (Impacts of products/services, main environmental and social risks, governance), with financial-impact ratings, a synthesis table and a complementary synthesis, exported as a styled Word document.

## How it works

- **Source collection.** The skill gathers from whatever the user supplies; it does not assume a fixed folder layout. The information memorandum is the factual base; internal notes carry the governance reading and committee stage.
- **Two mandatory check-ins.** It pauses to confirm the company name/website when ambiguous, and to confirm that no information memorandum exists when none is provided or found.
- **Research.** Company website ESG pages, controversy research on the company and its named executives, employee and client reviews, and sector-incident research where relevant.
- **SASB sector checklist.** A bundled reference lists the 77 SASB industries with their disclosure topics (general issue category and dimension). The skill reads only the target's sector block, as a safety net to ensure no material issue is missed.
- **Impact-theme taxonomy.** A fixed list of impact themes is used to name the positive impact of the products/services; the section is named "Impacts of products", "Impacts of services" or "Impacts of products and services" depending on what the company sells.
- **Self-contained Word export.** A dependency-free Python script (`render_esg_long.py`) builds the `.docx` from scratch — synthesis table, colour-coded title blocks with pillar pastilles (E / S / G) and Exposure / Maturity cells — with no external template and no logo.
- **Token modes.** A *light* mode (recommended for free or small plans) reads the memorandum via a sub-agent extract, pulls only the target's SASB sector block, and caps web research; *full* mode is the thorough default.
- **Optional modules (long format).** Competitor ESG benchmark, exclusion-list screening, and a SASB-based double-materiality matrix, each rendered as a table.

## Repository contents

- `PE-ESG-Analysis-Skills-Installation-Guide.pdf` — the complete installation guide. It contains the full text of the four skills, the Word-export script source, and two reference appendices (impact themes and the SASB sector list). Everything needed to reproduce the system is in this PDF.
- `LICENSE` — Apache License 2.0.
- `README.md` — this file.

## Installation

Follow the installation guide (PDF). In short: create four skills from the templates in the guide —

- `pe-esg-analysis` (main)
- `pe-esg-analysis-ultra-short`
- `pe-esg-analysis-short`
- `pe-esg-analysis-long`

— add the two reference files and the export script into the main skill folder, then install the skills in your Claude environment. Optionally prefix the skill names with your firm name. Skill names and descriptions must contain no angle brackets, and each description must be at most 1024 characters.

The skill set works with Claude in environments that support skills (e.g. Claude desktop Cowork mode, or Claude Code). It also relies on the "SASB Standards" materiality data (SASB Standards Navigator, IFRS Foundation — public data).

## Prior art

This repository is published as a public, timestamped technical disclosure. The commit history provides the publication date, and the PDF contains the reproducible technical content of the skill set. It is intended to serve as prior art establishing that this work was publicly available as of its publication date.

## Licence

Licensed under the Apache License, Version 2.0. You may use, modify, distribute and use it commercially, including in proprietary products, provided you keep the licence and copyright notice. The licence includes an explicit patent grant and a patent-retaliation clause. See `LICENSE`.
