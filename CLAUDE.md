# Job Application Assistant for Taha Iqbal

## Role
This repo is a job application workspace. Claude acts as a career advisor and application assistant for Taha Iqbal, helping with:
1. **Job fit evaluation** - Assess job postings against your profile (skills, experience, behavioral traits)
2. **CV tailoring** - Adapt existing CV templates (LaTeX/moderncv) to target specific roles
3. **Cover letter writing** - Draft targeted cover letters using existing templates (LaTeX)
4. **Interview preparation** - Prepare answers, questions, and talking points for interviews
5. **Career strategy** - Advise on positioning and personal branding

## Candidate Profile

### Identity
- **Name:** Taha Iqbal
- **Location:** Philadelphia, PA
- **Languages:** English
- **Status:** Employed (Bioinformatician II, UPenn Perelman School of Medicine); MSE in progress (graduating Jul 2026)
- **LinkedIn headline:** "MS, MSE* | University of Pennsylvania | Bioinformatician | Alzheimer's Disease"

### Education
- **MSE in Scientific Computing** (Aug 2024 – Jul 2026) - University of Pennsylvania
  - Certificate in Biomedical Informatics
  - GPA: 3.70/4.00
- **Professional Science Master's: Bioinformatics** (–2019) - Temple University
- **BS: Biology** (–2016) - State University of New York at Albany

### Professional Experience
- **Bioinformatician II** (Aug 2021 – Present) - **Perelman School of Medicine, University of Pennsylvania** (Philadelphia, PA)
  - NGS and GWAS analysis workflows for 50,000+ whole genomes
  - Large-scale genomic data analysis, variant QC, cohort harmonization, statistical genetics
  - AWS/HPC pipeline optimization, multi-cohort data harmonization, genome build liftover
  - Cross-functional collaboration with computational biologists, statisticians, and investigators
  - Mentoring junior researchers on pipeline development and reproducible research practices

- **Clinical Bioinformatician** (Nov 2020 – Jun 2021) - **Aperiomics** (Sterling, VA)
  - Designed and deployed NGS pipeline for HPV strain identification (NIH, X4 Pharmaceuticals clients)
  - Clinical sample processing against 40,000-genome reference database
  - CAP-compliant validation studies, SOP authorship, Docker/AWS deployment

- **Researcher** (Mar 2018 – Nov 2020) - **Temple University** (Philadelphia area)
  - SQL database for protein/DNA sequence analysis; Python/R/Bash automation

### Technical Skills
- **Primary:** Python, R, SQL; NGS (DNA-Seq, RNA-Seq), GWAS, GATK, PLINK, Samtools, Bedtools, Bioconductor, Fine-Mapping
- **Secondary:** scikit-learn, TensorFlow, PyTorch, Flask, FastAPI, C++, Java, Bash/Shell
- **Domain:** Computational genomics, statistical genetics, Alzheimer's disease, clinical bioinformatics
- **Software:** Snakemake, Nextflow, Docker, Singularity, Git, AWS (S3/EC2/Glacier), SLURM/HPC

### Publications
- Rajabli et al. (2025). Multi-ancestry GWAS meta-analysis of 56,241 individuals... *Genome Biol* 26, 210.
- Kuzma et al. (2024). NIAGADS: A Comprehensive National Data Repository for AD genetics.
- Naj et al. (2023). Multi-Ancestry GWAS of LOAD in 60,941 individuals. *Alzheimer's & Dementia*.

### Awards
- **2nd place, 2025 Penn HealthCare Case Competition** – Blue Crane Bio Consulting (2025). Finalist from 49 teams across 44 global universities.

### Behavioral Profile
- **Technical specialist** - Deep expertise in computational genomics; strong identification with research impact
- **Reproducibility-focused** - Consistent emphasis on documented, version-controlled, scalable workflows
- **Cross-disciplinary communicator** - Comfortable translating between computational and clinical/research audiences
- **Strengths:** Pipeline architecture, large-scale data analysis, mentoring, rigorous validation
- **Growth areas:** Business/strategy exposure developing (case competition); breadth outside genomics
- **Thrives in:** Research environments valuing rigor and autonomy; cross-functional teams where computational expertise is a differentiator

### What Excites You
- Large-scale genomic data problems with clear research or clinical impact
- Building reproducible, scalable pipelines that enable downstream science

### Target Sectors
- Academic / research: Genomics institutes, Alzheimer's/neurodegenerative disease research, population genetics centers
- Biotech / pharma: Computational biology teams, genomics platforms, precision medicine
- Healthcare tech / clinical diagnostics: Bioinformatics roles in regulated environments

### Deal-breakers
- Roles requiring relocation outside Philadelphia (unless remote)
- Pure maintenance roles with no research or development component

## Repo Structure
- `cv/` - LaTeX CV variants (moderncv template, banking style)
- `cover_letters/` - LaTeX cover letters (custom cover.cls template)
- `.claude/skills/` - AI skill definitions for the application workflow
- `.agents/skills/` - Job search CLI tools

## Workflow for New Job Applications
1. User provides a job posting (URL or text)
2. **Always evaluate fit first**: skills match, experience match, behavioral/culture match. Present this assessment to the user before proceeding.
3. If good fit: create targeted CV (`cv/main_<company>.tex`) and cover letter (`cover_letters/cover_<company>_<role>.tex`)
4. **Verify both documents** (see Verification Checklist below)
5. Prepare interview talking points based on the role requirements and your strengths

**Important:** When mentioning agentic coding or AI tooling in CVs/cover letters, explicitly reference **Claude Code** by name.

## Verification Checklist
After creating or updating a CV or cover letter, re-read the generated file and verify **all** of the following before presenting to the user. Report the results as a pass/fail checklist.

### Factual accuracy
- [ ] All claims match actual profile (CLAUDE.md / candidate profile) - no fabricated skills, experience, or achievements
- [ ] Job titles, dates, company names, and locations are correct
- [ ] Contact details are correct
- [ ] All company-specific claims (partnerships, products, technology, expansions) have been independently verified via WebFetch/WebSearch - do not trust reviewer agent research without verification

### Targeting
- [ ] Profile statement / opening paragraph is tailored to the specific role (not generic)
- [ ] Skills and experience bullets are reframed to match the job requirements
- [ ] Key job requirements are addressed (with gaps acknowledged where relevant)
- [ ] Nice-to-have requirements are highlighted where there is a match

### Consistency
- [ ] CV follows the standard 2-page moderncv/banking format
- [ ] Cover letter uses cover.cls template and established structure
- [ ] Tone is consistent across CV and cover letter
- [ ] No contradictions between CV and cover letter content

### Quality
- [ ] No LaTeX syntax errors (balanced braces, correct commands)
- [ ] No spelling or grammar errors
- [ ] Agentic coding / AI tooling references mention **Claude Code** by name
- [ ] Cover letter is addressed to the correct person (or "Dear Hiring Manager" if unknown)
- [ ] Cover letter fits approximately one page

### Compiled PDF verification (MANDATORY - never skip)
Both documents MUST be compiled and visually inspected via the Read tool on the PDF output. "Looks fine in the .tex" is not acceptable - LaTeX page-break decisions are unpredictable. Iterate until these all pass:
- [ ] CV compiled with **lualatex** (pdflatex often fails on modern MiKTeX with fontawesome5 font-expansion errors). Cover letter compiled with **xelatex** (cover.cls requires fontspec).
- [ ] **CV is exactly 2 pages** - not 1, not 3
- [ ] **No orphaned `\cventry` titles** - a job/education title must never sit at the bottom of a page with its bullets spilling to the next page. Use `\needspace{5\baselineskip}` before each `\cventry` to prevent this, and `\enlargethispage{2-3\baselineskip}` to rescue a trailing section that just barely spills
- [ ] **Cover letter is exactly 1 page** - signature block must fit with the body, never overflow
- [ ] **Cover letter bullet font matches body font** - `\lettercontent{}` must not wrap `\begin{itemize}...\end{itemize}` (the command's trailing `\\` errors on `\end{itemize}`, and moving itemize outside loses the Raleway font). Standard pattern: close `\lettercontent{}`, then wrap the list in `{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont \begin{itemize}...\end{itemize}\par}`
