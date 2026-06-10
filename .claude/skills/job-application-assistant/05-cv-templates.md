# CV Templates and Tailoring Guide

## Template: LaTeX moderncv (Banking Style)

All CVs use the moderncv LaTeX package with the "banking" style and "blue" color scheme.

**Output file:** `cv/main_<company>.tex`
**Compile with:** **lualatex** on MiKTeX/TeX Live. pdflatex often fails on modern MiKTeX installs with `fontawesome5` font-expansion errors; lualatex handles the same sources cleanly.
**Master reference:** `cv/main_example.tex` (comprehensive CV with all competencies, experience, and achievements - use as source when building targeted CVs)

### Compile command

```bash
cd cv && lualatex -interaction=nonstopmode main_<company>.tex
```

Expected output: `Output written on main_<company>.pdf (2 pages, ...)`. Any page count other than 2 is a failure that must be fixed before presenting to the user.

## Document Structure

```latex
\documentclass[11pt,a4paper,sans]{moderncv}
\moderncvstyle{banking}
\moderncvcolor{blue}

% Force both first and last name AND section headings to render in moderncv
% blue (color1). Default banking on lualatex+MiKTeX leaves these black, which
% looks inconsistent with the rest of the blue accent scheme.
\renewcommand*{\firstnamestyle}[1]{{\fontsize{34}{36}\bfseries\upshape\color{color1}#1}}
\renewcommand*{\lastnamestyle}[1]{{\fontsize{34}{36}\bfseries\upshape\color{color1}#1}}
\renewcommand*{\sectionstyle}[1]{{\sectionfont\color{color1}#1}}

\usepackage[utf8]{inputenc}
\usepackage{hyperref}
\hypersetup{
    colorlinks=true,
    linkcolor=blue,
    filecolor=magenta,
    urlcolor=blue,
    pdftitle={Taha Iqbal - CV},
    pdfpagemode=FullScreen,
}
\usepackage[scale=0.77]{geometry}
\usepackage{import}

% Personal data
\name{Taha}{Iqbal}
\address{Philadelphia, PA}{}{}
\phone[mobile]{(267) 506-6888}
\email{Taha.iqbal1993@gmail.com}
\extrainfo{\href{https://linkedin.com/in/taha-iqbal-001}{LinkedIn}, \href{https://github.com/Tahai-nformatics}{GitHub}}

\begin{document}
\makecvtitle

% 1. Profile statement (1-3 sentences, tailored per role)
% 2. Skills section
% 3. Professional Experience section
% 4. Education section
% 5. Selected Publications
% 6. Honors and Awards
% 7. References

\end{document}
```

### Color overrides

The three `\renewcommand*` lines in the preamble are required on lualatex+MiKTeX. Without them the firstname, lastname, and section headings render in black even though `\moderncvcolor{blue}` is set, which looks inconsistent with the rest of the blue accent scheme (links, bullet markers, contact icons). The override forces all three to use `color1` (moderncv's accent colour, which becomes blue under `\moderncvcolor{blue}`). Both names render bold; if you prefer the firstname in regular weight, change the firstnamestyle override from `\bfseries` to `\mdseries`. Don't drop the override - on most modern installs the defaults render visibly wrong.

### Spacing inside itemize lists (important)

**Do not place `\vspace{...}` between `\item` entries in an `itemize` list.** Even though the source looks symmetric, this pattern occasionally produces a noticeably oversized gap before a single item: the inter-item `\vspace` creates a paragraph break that interacts unpredictably with the list's internal `\itemsep`, so LaTeX renders one of the gaps wider than the rest. Remove the inter-item `\vspace` and let `itemize` use its native uniform spacing.

```latex
% WRONG - intermittently produces an oversized gap before one bullet
\begin{itemize}
\item \textbf{Foo}: ...
\vspace{1pt}
\item \textbf{Bar}: ...
\vspace{1pt}
\item \textbf{Baz}: ...
\end{itemize}

% RIGHT - uniform spacing using the list's native itemsep
\begin{itemize}
\item \textbf{Foo}: ...
\item \textbf{Bar}: ...
\item \textbf{Baz}: ...
\end{itemize}
```

Two related patterns are fine and should be kept:
- `\vspace{1pt}` immediately after `\section{...}` (between section heading and first item) - this is between the heading and the list, not between list items.
- `\vspace{3pt}` between top-level `\cventry` blocks in Professional Experience or Education - this gives breathing room between roles and renders consistently.

## Profile Statement Templates

### For Bioinformatics / Computational Genomics roles:
> Bioinformatician with 4+ years of experience developing reproducible NGS and GWAS pipelines for population-scale genomic datasets at the University of Pennsylvania. Combines deep expertise in variant analysis, cohort harmonization, and statistical genetics with strong Python, R, and cloud infrastructure skills (AWS, HPC). Experienced working across multidisciplinary teams on publication-ready Alzheimer's disease genomics research, with a track record of building scalable workflows that process terabytes of sequencing data.

### For Computational Biology / Statistical Genetics roles:
> Computational biologist specializing in large-scale statistical genetics and population genomics, with hands-on experience across the full GWAS workflow — from variant QC and cohort harmonization to fine-mapping and downstream ML applications. Brings 4+ years of production-grade pipeline development (Snakemake, Nextflow, Docker) on AWS and HPC, co-authorship on multi-ancestry Alzheimer's disease studies, and an MSE in Scientific Computing (UPenn, 2026).

### For ML / Data Science in Healthcare / Biotech roles:
> Data scientist and bioinformatician with deep experience applying machine learning and statistical methods to genomic and clinical datasets in a research setting. Proficient in Python (scikit-learn, TensorFlow, PyTorch), R, and SQL, with a strong foundation in reproducible pipeline engineering and cloud-scale data processing (AWS, HPC). Background spans Alzheimer's disease genomics, clinical metagenomics (CAP-regulated), and RESTful API development, with an MSE in Scientific Computing in progress at UPenn.

### For Clinical Bioinformatics / Diagnostics roles:
> Clinical bioinformatician with experience building and validating NGS pipelines in a CAP-regulated diagnostics environment (Aperiomics) and in large-scale academic genomics (UPenn Perelman School of Medicine). Designed pathogen detection workflows processing clinical samples across 40,000 reference genomes; later scaled to 50,000+ whole genomes in population-level GWAS studies. Brings rigorous SOP authorship, Docker/cloud deployment, and cross-functional communication with clinicians and investigators.

## Section-by-Section Tailoring

### Profile Statement / Elevator Pitch (Best Practice)
This is the most important section to customize. It appears right after `\makecvtitle`.

Write 5-7 lines that function as an "elevator pitch": a concise, compelling introduction explaining why you're qualified for *this specific role*. Focus on what the employer gains from hiring you.

### Core Competencies / Skills Section (Best Practice)
Reorder and emphasize based on the role. Use bold category labels.

List **5-7 key competencies** in bullet format, tailored to the specific job. For each competency, briefly explain how it adds value to the position.

### Education
- Always include highest degrees
- MSE at UPenn (in progress, 2026) is a strong signal — always include
- For industry roles, keep education brief (dates and titles only)

### Professional Experience
- Rewrite bullet points to emphasize aspects most relevant to the target role
- Use 4-6 bullets for most recent role, 3-4 for previous, 2-3 for older
- **Emphasize measurable results** where possible: "50,000+ whole genomes", "40,000 reference genomes", "terabyte-scale"

### Handling the Temple Researcher Role
This role (2018–2020) is optional on the CV — include it when:
- The posting values database engineering or early-career research breadth
- Space allows (it's a 3rd role and may push to 3 pages — cut bullets aggressively)
- Omit it when the CV is already full and the role adds little signal for the target posting

### Publications
- Include all 3 current publications for academic and research roles
- For industry roles, include 1-2 most relevant; keep format brief
- Lead with Rajabli 2025 (most recent, highest-impact)

### Honors and Awards
- 2025 Penn HealthCare Case Competition (2nd place) — include for consulting, biotech strategy, or any role where business acumen is valued

### References
- List upon request only (single line) unless specifically asked

## Compile-and-Inspect Loop (MANDATORY)

After writing the CV and before presenting to the user, always compile and visually inspect the PDF. Iterate until the layout is clean. Workflow:

1. Run `lualatex -interaction=nonstopmode main_<company>.tex`
2. Check the output page count: must be exactly 2
3. Read the PDF via the Read tool and visually inspect both pages
4. Check for **orphaned entries**: a `\cventry` title line must never sit alone at the bottom of page 1 with its bullets on page 2

### Fixing common page-break problems

**Problem: entry title on page 1, bullets orphaned to page 2**
Add `\needspace{5\baselineskip}` immediately before the problematic `\cventry`:
```latex
\needspace{5\baselineskip}
\item{\cventry{YEAR--YEAR}{Role Title}{Organization}{Location}{}{...}}
```
Include `\usepackage{needspace}` in the preamble.

**Problem: one trailing section spills to page 3 (e.g., References alone on page 3)**
Add `\enlargethispage{2-3\baselineskip}` before a late section (e.g., before `\section{Honors and Awards}`) to stretch page 2 by a few lines. This is the standard LaTeX rescue for near-miss overflows.

**Problem: 3 pages with significant content on page 3**
Cut content — do not compress geometry or `\vspace`. See "Relevance-weighted cutting" below for the rule.

**Problem: content finishes early on page 2 (feels thin)**
Restore the highest-relevance item that was previously cut — a CV that ends mid-page 2 looks incomplete.

## Page Budget - Hard 2-Page Limit

The CV **must** fit on exactly 2 pages when compiled. Use these content limits as a guide:

| Section | Max budget |
|---------|-----------|
| Profile statement | 3-4 lines |
| Skills | 5 items, each 1-2 lines |
| Most recent role | 4-5 bullets |
| Previous role | 2-3 bullets |
| Older roles | 2 bullets (1 line each) |
| Education | 2-3 entries |
| Publications | 2-3 entries |
| Awards | 1-2 entries, single line each |
| References | "Available upon request." (single line) |

**If in doubt, cut rather than squeeze.** Reducing `\vspace` or geometry scale to force-fit content makes the CV look cramped.

## Relevance-weighted cutting (the right way to shrink a CV)

**Cut by signal, not by section.** Static priority lists ("remove oldest education first, then shorten the earliest role...") are wrong when a relevant "lower-priority" item is competing with an irrelevant "higher-priority" item. An older-role bullet that speaks directly to the posting is worth more than a recent-role bullet that does not.

For every candidate line, score three things:

1. **Relevance to THIS posting** — does the line hit a named tool, keyword, or stated responsibility in the job ad?
2. **Uniqueness** — is it the only place this claim appears, or is it duplicated elsewhere in the CV?
3. **Narrative load** — does the cover letter depend on it? If cutting the line would force you to rewrite a cover-letter paragraph, it is load-bearing.

Cut the lowest-total-score line first, regardless of which section it sits in.

### Practical order of cuts (easiest → last resort)

1. **Redundancy.** If an achievement appears in both Core Competencies AND a role bullet, the Core Competencies version is usually the cleaner cut (the experience bullet is more concrete evidence).
2. **Profile-statement fluff.** A sentence that just restates what Publications or Skills will show.
3. **Low-relevance experience bullets.** A bullet about work that does not touch posting keywords, wherever it sits.
4. **Low-relevance supporting content.** Temple Researcher role bullets; certifications that don't match the posting's stack.
5. **Low-relevance publications.** Keep 1-2 publications that best match the posting.
6. **Last-resort structural cuts.** Oldest education entry, tightening an older role to 2 bullets.

## Recommended Section Order

**For bioinformatics / computational genomics / statistical genetics roles:**
1. Profile statement / elevator pitch
2. Core competencies / Skills
3. Professional Experience (reverse chronological)
4. Education (reverse chronological)
5. Publications
6. Honors and Awards
7. References

**For ML / data science / healthcare tech roles:**
1. Profile statement / elevator pitch
2. Core competencies / Skills
3. Professional Experience (reverse chronological)
4. Education (reverse chronological)
5. Publications (abbreviated)
6. Honors and Awards
7. References

**For clinical / diagnostics / regulatory roles:**
1. Profile statement / elevator pitch
2. Core competencies / Skills
3. Education (reverse chronological) — credentials are a key qualifier
4. Professional Experience (reverse chronological)
5. Publications
6. References
