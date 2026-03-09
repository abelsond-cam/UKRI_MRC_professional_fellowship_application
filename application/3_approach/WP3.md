Here is a coherent draft of the full WP3 section, with the revised Background plus WP3a–c laid out in grant style so you can edit further.

***

## WP3: Clinical Antibiotic Prediction in Chronic Lung Infection

### Objective

To determine whether strain‑resolved bacterial genomics, integrated with longitudinal clinical metadata, can explain and begin to predict IV antibiotic treatment outcomes in chronic respiratory infection—moving beyond the fundamental limitations of standard culture and AST, and characterising the microbial mechanisms underlying treatment failure.

***

### Background

Predicting antibiotic success and resistance emergence is central to treatment decisions, yet current antimicrobial susceptibility testing has little clinical predictive value in most real infections (ref). Standard AST measures antibiotic activity in simplified planktonic monocultures, whereas most clinically important infections occur in polymicrobial, spatially structured environments where neighbouring organisms can protect one another from antibiotic killing and in vitro susceptibility becomes decoupled from in vivo treatment efficacy (ref).

Recent work has shown that strain (and species) switching is a central mechanism of resistance emergence and treatment failure: Stracy et al. (Science 2022) demonstrated that within-patient strain and species replacement underlies a substantial proportion of resistance acquisition, even in relatively planktonic urinary tract infections. Crucially, however, their approach relied on culture-derived AST as the primary endpoint for detecting switching events. In the polymicrobial, spatially structured infections, where AST is least reliable, we need methods that reconstruct mixed-lineage infection structure at high resolution and assess the clinical significance of strain dynamics independently of AST. For example, in chronic lung infection, microbial communities tend to be stable at the species level and AST from a single colony pick is often fixed over periods of time without relevance to the flux of effective and ineffective antibiotic treatments (ref).

To address this, we have built the SputaGen cohort — a fully recruited, prospective study of 653 intravenous antibiotic courses in severe exacerbations of lung disease requiring IV antibiotics and producing purulent sputum, with standardised clinical endpoints that I designed and have led as Principal Investigator. We focus on lung infection because it is a major cause of morbidity and mortality and it is an excellent example of a polyclonal, polymicrobial infection in structured environments. The cohort is in place, we have confirmed adequate power (see Statistical Design), and the analytical pipeline is ready. In WP3a, we first quantify the real-world predictive value of AST and define rigorous clinical outcome measures; in WP3b, we apply strain-resolved genomics to determine whether strain switching explains treatment failure; and in WP3c, we integrate genomic and clinical features into preliminary predictive models.

***

### WP3a. Bio‑clinical informatics of the SputaGen cohort

This will be the first large-scale, prospective study to directly test the clinical predictive value of sputum AST in chronic lung infection. I will curate and analyse the full SputaGen dataset (653 IV antibiotic courses, 1,273 sputum samples) to quantify treatment success and failure rates and define robust outcome measures. Using pre-specified clinical endpoints (global response score, symptom change, lung function, and time to next IV course), I will (i) derive a composite responder/non-responder classification using both quantitative and qualitative response criteria, (ii) estimate overall and species-specific failure rates, and (iii) identify baseline clinical predictors of outcome stratified by pathogen. This work is a significant standalone contribution: it will provide definitive, prospective evidence on whether current AST practice predicts clinical outcome in this setting — where we expect it to have very little predictive value. Equally, the outcome definitions and failure/success cut-points established here are essential for all downstream genomic analyses: without rigorous clinical classification of which patients failed and which succeeded, it is not possible to test whether strain switching or other genomic features explain the difference (WP3b–c). [bmjopen.bmj](https://bmjopen.bmj.com/content/8/3/e014613)

***

### WP3b. *Pseudomonas aeruginosa* strain switching during IV treatment

Chronic *P. aeruginosa* infection is present in ~40–45% of SputaGen IV episodes, consistent with adult bronchiectasis and CF cohorts, yielding ~270–290 courses with baseline *P. aeruginosa*. 
Using the strictly defined failures from WP3a, I will select all available failures and an equal number of matched successful courses (e.g. by age, disease, baseline lung function), yielding a balanced set of ~50 failures and ~50 successes for detailed genomic analysis. [pmc.ncbi.nlm.nih](https://pmc.ncbi.nlm.nih.gov/articles/PMC7993380/).  Preliminary SputaGen analyses indicate that ~19% of all courses have been judged by clinical staff to have failed as they have changed IV antibiotics in absence of any side effects.  This corresponds to approximately ~50 failures among *P. aeruginosa*‑positive episodes confirming the study is adequately powered (see statistics). 

Strain resolution will be performed on culture-enriched samples rather than by direct sputum metagenomics, because host DNA heavily dilutes bacterial signal in respiratory samples and culture-based approaches consistently recover greater diversity and higher-quality assemblies for lineage reconstruction. For each selected course, the Bryant lab’s established strain‑resolution pipeline will be applied to pre‑ and post‑course sputum cultures to identify *P. aeruginosa* lineages and their approximate relative abundances from mixed cultures. Dominant strain switching will be defined as a change in the leading *P. aeruginosa* lineage between pre- and post-course samples, or the emergence of a new lineage that was undetectable at baseline. This analysis is adequately powered to detect a clinically meaningful association between strain switching and treatment failure (see Statistical Design). This will deliver the first quantitative estimate of *P. aeruginosa* strain switching rates in chronic lung infection and its clinical impact.


### WP3c. Foundations for genomic outcome prediction

Within the fellowship, I will integrate the outputs of WP3a–b into preliminary models that combine clinical predictors (disease type, exacerbation history, prior antibiotics) with species composition and *P. aeruginosa* strain switching to explain treatment outcomes. Using logistic and time‑to‑event models, I will quantify the incremental predictive value of genomic features—such as the presence of specific epidemic clones or dominant strain switching—over and above AST and baseline clinical variables. This will identify which genomic and ecological features are most informative for outcome, and will define the feature set for future machine‑learning models that integrate whole‑genome embeddings and community metrics. The resulting strain‑resolved genomes, annotated mobile genetic elements (from WP1), and longitudinal outcomes from SputaGen will position us to build and validate full genomic outcome prediction models in a subsequent programme, operating independently of the current AST paradigm rather than being constrained by it. 