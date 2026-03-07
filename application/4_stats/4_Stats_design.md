# Reproducibility and Statistical Approach

This section details the statistical design and reproducibility considerations for major analyses, including explicit power calculations and approaches to address dataset bias.

---

## 1. Global *Klebsiella* Analyses

- Estimate pangenome size and structure within each clonal group.
- Identify clusters using Panaroo, both overall and stratified by clonal group.
- Use high-quality reference genomes to anchor and define Panaroo clusters.
- Assess statistical power for analyses of insertion sequences and plasmid content.

*Dating of lineages:*  
Apply Bayesian phylogenetic approaches (e.g., BEAST or BactDating) to estimate lineage ages. This temporal context is critical for evaluating pangenome openness, as within-lineage diversity and new gene acquisition may depend on evolutionary time rather than lineage identity alone.

---

## 2. Bacformer and Pyseer Analyses

### i) Antibiotic Susceptibility Testing (AST)

- Power analysis: Predictive modeling of antibiotic resistance using 2,500 genomes with matched AST results.
- Ensure a minimum of 450 resistant cases in the training set for robust classification.
- For reference, an *A. baumannii* dataset with 1,800 genomes (60% training split, 50% resistance prevalence—i.e., 540 resistant cases) demonstrated appropriate power for resistance prediction (e.g., gentamicin resistance).

### ii) Invasive Disease Prediction Using Isolation Source

- Assemble a set of 10,000 samples (approx. 5,000 each for blood and stool as isolation sources), matched by country with a maximum stratification of 2:1 for either source per country.
- Provide exact sample numbers and describe the global distribution.
- Use country-based stratification to minimize oversampling from dominant clonal lineages.
- Further stratify by antimicrobial resistance (AMR) study type and 'Surveillance' study type (definitions and rationale provided).
- Additional sources for possible analyses include:
  - Urinary tract (~13,000 global results)
  - Lower respiratory tract (~6,500 results)
  - Wound and abscess (~3,500 results)
  - Other body fluids (e.g., ascitic tap, pleural or surgical drain fluid, CSF; to specify sample size)

- Visual summaries: Include figures depicting the distribution of isolation sources and other relevant metadata.

---

## 3. SputaGen WP3b: Strain Switching in *P. aeruginosa* During IV Treatment

Chronic *P. aeruginosa* infection is present in approximately 40–45% of SputaGen IV courses (consistent with rates in adult bronchiectasis and CF cohorts), corresponding to roughly 270–290 IV episodes with baseline *P. aeruginosa* detection.

Preliminary SputaGen data indicate about 19% of these episodes meet a strict definition of treatment failure (defined as worsening or no improvement in clinical response metrics, or IV escalation within 30 days), yielding around 50 failures. All available failures and an equal number of matched successes (matched by age, underlying disease, baseline lung function, etc.) will be selected, resulting in a balanced set of ~50 failures and ~50 successes for in-depth genomic study.

For each selected case, the Bryant lab’s strain-resolution pipeline will be applied to pre- and post-treatment sputum cultures, enabling high-resolution identification of *P. aeruginosa* lineages and their relative abundances.

**Definition of strain switching:**  
A switch is defined as either (1) a change in the dominant *P. aeruginosa* lineage between pre- and post-course samples, or (2) the emergence of a previously undetectable lineage after treatment.

**Power calculation:**  
Drawing on Stracy et al. (2022), who found that treatment-induced resistance emergence confers odds ratios of approximately 2–4 (stratified by patient history), this analysis targets detection of a similar effect size. If dominant strain switching is present in ~15% of successful courses and ~40% of failures, a sample size of 50 failures and 50 successes (100 total) provides >80% power (α=0.05) to detect an association (estimated OR ≈ 3) between strain switching and treatment failure. 

This study will provide the first quantitative estimate of *P. aeruginosa* strain switching rates and their clinical impact in chronic lung infection (see Stracy et al., 2022 for reference).

