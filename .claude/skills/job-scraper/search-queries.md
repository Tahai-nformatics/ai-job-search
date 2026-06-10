# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Search Sites

Primary (US job market):
- **linkedin.com/jobs** - strongest overall source for consulting + bioinformatics
- **indeed.com** - broad US job aggregation
- **glassdoor.com** - consulting + biotech + analytics
- **builtin.com** - tech/startup roles
- **biospace.com** - biotech/pharma jobs
- **wellfound.com** - startup opportunities
- **dice.com** - technical/data engineering roles
- **usajobs.gov** - government/public health positions

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for target companies
- Company career portals (Deloitte, Accenture, IQVIA, ZS, etc.)

## Query Categories

Queries are grouped by priority. Each query should be combined with your location terms (e.g. "Copenhagen", "Sjælland", "Hovedstaden") where the site supports it.

### Priority 1: Bioinformatics / Computational Biology

These match your strongest and most desired career direction.

```
site:linkedin.com/jobs "Bioinformatics Scientist" "United States"
site:linkedin.com/jobs "Computational Biologist" "United States"
site:linkedin.com/jobs "Bioinformatician" "United States"
site:linkedin.com/jobs "Bioinformatics Analyst" "United States"
site:indeed.com "Bioinformatics Scientist" "remote"
site:biospace.com "Computational Biology" "United States"
site:glassdoor.com "Bioinformatics Engineer" "United States"
```

### Priority 2: Data Science

These match your domain expertise.

```
site:linkedin.com/jobs "Healthcare Data Scientist" "United States"
site:indeed.com "Genomics Data Scientist" "remote"
site:builtin.com "Bioinformatics" "remote"
site:dice.com "Python" "Bioinformatics" "remote"
```

### Priority 3: Genomics / NGS / Cancer

Adjacent roles you could pivot into.

```
site:linkedin.com/jobs "NGS" "Bioinformatics" "United States"
site:linkedin.com/jobs "Cancer Genomics" "Computational Biologist"
site:biospace.com "Cancer Genomics" "Bioinformatics"
site:indeed.com "Variant Calling" "Bioinformatics"
```

### Priority 4: Consulting / Strategy / Technical Consulting

Wider net for general technical roles.

```
### Priority 4: Consulting / Strategy / Technical Consulting

Broader consulting and analytics-focused roles across strategy, healthcare, technology, and operations consulting firms.

```bash
# Management / Strategy Consulting
site:linkedin.com/jobs "Consultant" healthcare analytics
site:linkedin.com/jobs "Senior Consultant" data analytics
site:linkedin.com/jobs "Strategy Consultant" healthcare
site:linkedin.com/jobs "Business Transformation Consultant"

# Technical / Data Consulting
site:linkedin.com/jobs "Data Science Consultant"
site:linkedin.com/jobs "Analytics Consultant"
site:linkedin.com/jobs "AI Consultant"
site:linkedin.com/jobs "Cloud Consultant" AWS
site:linkedin.com/jobs "Bioinformatics Consultant"

# Life Sciences / Pharma Consulting
site:linkedin.com/jobs "Life Sciences Consultant"
site:linkedin.com/jobs "Healthcare Consultant"
site:linkedin.com/jobs "Clinical Data Consultant"
site:linkedin.com/jobs "Digital Health Consultant"
site:linkedin.com/jobs "Pharma Consulting"

# Supply Chain / Retail Consulting
site:linkedin.com/jobs "Supply Chain Consultant"
site:linkedin.com/jobs "Retail Consultant"
site:linkedin.com/jobs "Planning Consultant"
site:linkedin.com/jobs "Business Analyst" supply chain
site:linkedin.com/jobs "IBP Consultant"

# Firms
site:linkedin.com/jobs Deloitte consultant healthcare
site:linkedin.com/jobs Accenture data consultant
site:linkedin.com/jobs KPMG healthcare consultant
site:linkedin.com/jobs EY technology consultant
site:linkedin.com/jobs PwC analytics consultant
site:linkedin.com/jobs North Highland consultant
site:linkedin.com/jobs Slalom consultant data
site:linkedin.com/jobs ZS Associates consultant
site:linkedin.com/jobs IQVIA consultant

# Remote + US
site:linkedin.com/jobs consultant remote healthcare analytics
site:indeed.com "Data Consultant" remote
site:builtin.com consultant healthcare data
site:glassdoor.com "Analytics Consultant" remote
```

```

## Location Filter

When evaluating results, verify the job location is within reasonable commute distance from your home. Define acceptable areas:
- Philadelphia and surrounding areas
- California
- New York
- Boston
- Remote US

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
