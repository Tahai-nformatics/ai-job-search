# Search Queries for Job Scraper

## Search Sites

Primary (US job market):
- **linkedin.com/jobs** - LinkedIn job listings (filter: Philadelphia / Remote / United States)
- **indeed.com** - broad US job board
- **glassdoor.com/Jobs** - with company culture context
- **jobs.lever.co / greenhouse.io** - biotech/pharma/startup ATS listings
- **USAJobs.gov** - NIH, NCI, NHGRI, FDA roles (federal genomics/bioinformatics)

Secondary (academic/research):
- **jobs.nih.gov** - NIH intramural and extramural positions
- **higheredjobs.com** - university research positions
- **naturejobs.com / science.org/careers** - research scientist roles
- Direct Google searches: `site:upenn.edu/careers bioinformatics`, `site:chop.edu careers bioinformatics`

## Query Categories

Queries are grouped by priority. Combine with location terms where supported.

### Priority 1: Core Bioinformatics / Computational Genomics

These match Taha's strongest and most desired career direction.

```
site:linkedin.com/jobs "bioinformatician" Philadelphia
site:linkedin.com/jobs "senior bioinformatician" "remote"
site:linkedin.com/jobs "computational biologist" Philadelphia
site:indeed.com "bioinformatician" "NGS" Philadelphia
site:indeed.com "GWAS" "bioinformatician" United States
site:linkedin.com/jobs "genomics data scientist" Philadelphia
site:linkedin.com/jobs "staff bioinformatician"
```

### Priority 2: Statistical Genetics / Population Genomics

These match Taha's deep domain expertise.

```
site:linkedin.com/jobs "statistical genetics" bioinformatician
site:linkedin.com/jobs "GWAS" "computational biologist"
site:linkedin.com/jobs "population genomics" scientist Philadelphia
site:indeed.com "statistical geneticist" United States
site:linkedin.com/jobs "Alzheimer" "bioinformatics" scientist
site:linkedin.com/jobs "neurodegenerative" "genomics" scientist
```

### Priority 3: Adjacent Roles (Pivot Opportunities)

Roles Taha could pivot into with his background:

```
site:linkedin.com/jobs "genomics data scientist" biotech
site:linkedin.com/jobs "bioinformatics engineer" Philadelphia
site:linkedin.com/jobs "research scientist" "genomics" "Python" Philadelphia
site:linkedin.com/jobs "computational scientist" "NGS" pharma
site:linkedin.com/jobs "clinical bioinformatician" Philadelphia
site:indeed.com "bioinformatics" "pipeline" "AWS" Philadelphia
```

**Also consider** (proactive suggestions based on Taha's profile):
- **"Technical Consultant - Genomics"** or **"Scientific Solutions Engineer"** at genomics platform companies (Illumina, 10x Genomics, PacBio, Element Biosciences) — combines deep technical expertise with client-facing impact
- **"Principal Scientist - Computational Biology"** at biotech/pharma (Regeneron, GSK, Pfizer, Novartis all have Philadelphia-area presence or strong remote programs)
- **"Bioinformatics Scientist - Rare Disease"** — skills transfer directly from AD genomics
- **"Research Software Engineer - Genomics"** — for candidates who want to focus on infrastructure/tooling over analysis

### Priority 4: Broader Technical / Healthcare Data

Wider net for adjacent technical roles.

```
site:linkedin.com/jobs "data scientist" "genomics" Philadelphia
site:linkedin.com/jobs "machine learning" "bioinformatics" Philadelphia
site:linkedin.com/jobs "Python" "AWS" "genomics" remote
site:indeed.com "bioinformatics" "Snakemake" OR "Nextflow" United States
site:linkedin.com/jobs "computational biology" "drug discovery" Philadelphia
```

## Location Filter

Philadelphia metro area is home base. When evaluating results:

- **Ideal:** Philadelphia city, University City, Center City; New York City; Boston/Cambridge MA; California (Bay Area, San Diego, LA); remote-first roles (US)
- **Acceptable:** Philadelphia suburbs (Main Line, South Jersey, Wilmington DE area); hybrid with 1-3 days/week in office
- **Borderline:** Washington DC area
- **Too far:** Relocation required outside the above — flag for discussion, do not auto-discard if role is exceptional

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- `/scrape biotech` → Priority 3 queries + custom biotech-specific searches
- `/scrape remote` → add `"remote" OR "fully remote"` to all Priority 1-2 queries
- `/scrape NIH` → use USAJobs.gov + jobs.nih.gov queries specifically
