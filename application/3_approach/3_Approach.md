# 3. Approach

## Motivation

Antimicrobial resistance (AMR) is a major global threat to modern medicine, directly responsible for an estimated 1.27 million deaths and contributing to 4.95 million deaths worldwide in 2019. The economic burden is similarly severe, with projected losses of up to US \$3.4 trillion in global GDP and over US \$1 trillion in additional healthcare costs by 2050. This crisis is driven not only by the spread of resistant strains between individuals and hospitals, but also by continuous evolution within individual patients, where bacteria acquire resistance genes, develop tolerance to antibiotics, and adapt to evade the immune system.

Despite this, we still lack the technology to make robust predictions. At a global level, we cannot reliably predict the emergence of new resistance, epidemic and pandemic strains, or which resistance mechanisms will spread.  
At a clinical and individual patient level, we cannot predict which patients will benefit from a given antibiotic and which will not, and still rely on culture and sensitivity testing to guide antibiotic prescribing – technology that has barely changed since the early twentieth century and has poor predictive power for many invasive and chronic infections.

## Aims

This fellowship aims to contribute to:

1. **Understanding the emergence and pathoadaptation in a global pathogen resistant to new antibiotics**
2. **Developing and refining predictive models from genomes to predict antibiotic resistance and invasive disease**
3. **Predicting the clinical outcome of antibiotic treatment and resistance emergence in individual patients**

The overarching aim is to build and test a practical, genomics-informed prediction framework at the global and clinical level that can move beyond binary "sensitive / resistant" reporting and support individualised antibiotic decisions.

## Background and Work Leading Up to this Fellowship

> This is a literature review of the background and work leading up to this fellowship.

Emerging global bacterial pathogens, such as \textit{Pseudomonas aeruginosa} and \textit{Mycobacterium abscessus}, evolve to specialise in human infection and transmission, driving both chronic and invasive disease. This process, termed pathoadaptation, encompasses both vertical and horizontal mechanisms of genetic change. Vertical pathoadaptation occurs through convergent mutation of the core and accessory genomes, often involving the rewiring of global transcription to enable immune evasion and allow bacteria to survive and persist inside macrophages (Weimann et al., Science 2024; Bryant et al., Science 2021). Pathoadaptation also operates horizontally via horizontal gene transfer (HGT), which can drive saltatory leaps in bacterial fitness and pathogenic capacities — as seen in \textit{M. abscessus} (Bryant et al., Science 2016) — or sudden evasion of the immune system, such as through capsule locus acquisition in \textit{Klebsiella} (Holt et al., [ref]). These transfers occur via multiple mechanisms including bacteriophages and plasmids (Science review 2019, [HGT mechanisms ref]). Furthermore, plasmids themselves have undergone profound evolutionary domestication in the post-antibiotic era: a minority of ancestral backbones have evolved into large, self-transmissible, multi-replicon vectors that now drive the global dissemination of multidrug resistance (Cazares et al., Science 2025). 

Enteriobacteriacae include E. coli, K. pneumoniae and A. baumannii are important ESCAPPM organisms and are also a major cause of mortality worldwide, with rapidly escalating rates of AMR (ref). \textit{Klebsiella pneumoniae} is a particularly interesting and important pathogen to study because it is a global AMR pathogen and a major cause of mortality worldwide, with rapidly escalating rates of AMR. It is also a major cause of invasive disease, particularly in the respiratory tract. It is characterised by frequent HGT, capsule recombination, and acquisition of large plasmids carrying AMR and virulence determinants. Global success of lineages such as sequence lineage 258 likely reflects a complex interplay of these processes, which are poorly understood and not adequately represented in current models (ref: ).

Our ability to decode these processes at scale is accelerating rapidly, driven by the convergence of massive genomic resources with powerful computational tools. Global repositories including AllTheBacteria (Hunt et al., bioRxiv 2024), BakRep ([ref]), and NCBI/EBI now make hundreds of thousands of short read and whole genome assemblies openly accessible, providing the population-scale datasets necessary for statistically powered inference. These are complemented by a new generation of analytical methods: whole-genome pangenome graph tools representing gene presence and adjacency as networks of orthologous nodes (Panaroo; Tonkin-Hill et al., Genome Biology 2020), Bayesian phylodynamic frameworks reconstructing the timing and geography of pathogen emergence (BEAST; used in Weimann et al., Science 2024), Bayesian mixed-model GWAS identifying resistance and virulence determinants across tens of thousands of genomes (PySeer; Lees et al., Bioinformatics 2018), and hidden Markov and latent-state models detecting mobile elements and insertion sequences genome-wide (ISEScan; [ref]). Together, these tools — and the global datasets that power them — make true population-scale comparative genomics viable for the first time, opening systematic interrogation of how bacteria evolve, adapt to human hosts, and acquire resistance.

Translating these datasets into phenotypic predictions has advanced through curated resistance gene catalogues (CARD, AMRFinderPlus; refs: Jia et al., Nucleic Acids Res 2017; Feldgarden et al., Sci Rep 2021), bacterial GWAS using Bayesian mixed models and k-mer random walks across population graphs (PySeer; ref: Lees et al., Bioinformatics 2018), and pan-genome tools that estimate accessory genome openness and quantify HGT acquisition rates (Panaroo, Panstripe; refs: Tonkin-Hill et al., Genome Biology 2020; Genome Research 2023). Most recently, Bacformer — a whole-genome transformer pretrained on 1.3 million bacterial genomes that models genomes as sequences of contextualised protein embeddings — predicts antibiotic resistance with AUROC >0.97 and identifies causal genetic determinants without prior annotation, representing an unparalleled advance in genome-to-phenotype inference (ref: Wiatrak, Abelson et al., in submission).
 
At the clinical level, genomic approaches work well in acute, single-pathogen environments like urinary tract infection, where integrating pathogen genomics with patient treatment history can reduce resistance emergence by up to 74\% (Stracy et al., Science 2022). However, these predictive models routinely perform poorly in chronic and invasive respiratory infections such as cystic fibrosis (CF) and non-CF bronchiectasis. For example, standard antimicrobial susceptibility testing (AST) — currently our only clinical tool for guiding antibiotic therapy — frequently fails to predict patient outcomes. In CF patients experiencing Pseudomonas aeruginosa exacerbations, antibiotic treatment yields a successful clinical response in roughly 60\% of cases when the bacteria are deemed susceptible in vitro; bizarrely, treatment succeeds at approximately the same rate even when the isolate is highly resistant (Somayaji et al., J Cyst Fibros 2019; Aaron et al., JAMA 2005). Furthermore, longitudinal sputum antibiogram resistance profiles and microbial community structures remain remarkably stable over time within individual patients, remaining entirely decoupled from the success or failure of specific clinical treatment episodes (Fodor et al., PLoS One 2012; Zhao et al., Microbiome 2012).

There are multiple mechanisms of bacterial evasion that explain why standard in vitro testing fails to capture in vivo reality. First, chronic respiratory infections are inherently polymicrobial and polyclonal; antibiotic efficacy against target pathogens is often markedly diminished when they reside within these complex, mixed communities, where interactions between species can cross-protect otherwise susceptible bacteria (O'Brien, Figueroa & Welch, ISME J 2022). Second, the host lung environment and long-term pathoadaptation drive profound changes in bacterial behaviour (Weimann et al., Science 2024; Bryant et al., Science 2021). Adaptive mutations can promote physiological senescence and extreme antibiotic tolerance — such as through the formation of persister cells — enabling bacteria to survive prolonged antibiotic exposure via metabolic dormancy, independent of classical genetic resistance mechanisms (Boeck et al., Nat Microbiol 2022; Mulcahy et al., J Bacteriol 2010). Together, these multifaceted evasion strategies highlight why conventional AST and simple resistance genotyping fall short, underscoring the urgent need for advanced diagnostic and therapeutic approaches in chronic lung infection. 

A further limitation is the AST itself. For example, AST values can vary dramatically depending on the culture media used: in one study of ... cultured in ... and in ... the AST value was ... vs ... So that currently reported in-vitro tests reporting a bacteria as resistant (for example in Pseudomonas aeruginosa culture media) may actually be susceptible in clinical practice when used in lung infection.  Developing tests for each bacterial environment (sputum, urine, wound, and the various diseases that of them (for example CF vs non-CF bronchiectasis) is difficult.  Using bacterial genomes to directly predict clinical success of treatments offers and exciting new possible avenue which, with enough data of the genome, site of infection and clinical background information, may be tractable (Kishony, reference in urine). 


## Research Strategy

> Sections must be completely orthogonal and self-contained. They should not hang one over the top of the other. 

### WP1: Understand the Emergence and Pathoadaptation of *Klebsiella pneumoniae*, a Global AMR Pathogen

**Objective:**  
To reconstruct the evolutionary history, vertical mutational trajectories, and horizontal gene transfer (HGT) networks that drive the global emergence, pathoadaptation, and antimicrobial resistance (AMR) of *K. pneumoniae*.

**Feasibility and Initial Findings:**  
I have already established a foundation for this work package by downloading and curating a massive global dataset of over 80,000 *K. pneumoniae* genomes. To mitigate the primary risk of missing or poor-quality clinical metadata, I have systematically collated thousands of clinical labels, increasing metadata completeness from approximately 50% to over 80% across most key categories (detailed further in the Statistical Analysis section). Furthermore, my initial exploratory analyses using Kleborate have confirmed a broad global distribution and revealed a vast array of HGT events. These include the routine exchange of exceptionally large genomic sections and frequent capsular locus swapping, underscoring the highly dynamic nature of the *K. pneumoniae* accessory genome and confirming the viability of this dataset for high-resolution evolutionary modelling.

**Research Strategy:**  
Decoding the pathogenic evolution of *K. pneumoniae* requires a multifaceted approach encompassing vertical transmission, core genome phylogenetics, pathoadaptation, and horizontal gene transmission. I will execute this complex analysis as part of, and with mentoring from, our world-leading bioinformatics team (Weimann, Dinan, Figueroa, Ruis, Bruchmann, and Wiatrak). This collaborative environment greatly reduces the risk surrounding the overall bioinformatic output and allows me to focus my leadership on the critical role of mobile elements and plasmids. The overarching group effort will include:

**Core Genome Phylogeny and Evolutionary Dating:**  
We will generate high-resolution core genome phylogenies and employ Bayesian temporal reconstruction (using tools such as BEAST and BactDating) to date the emergence, expansion, and global spread of key epidemic lineages.

- **Scalable Pangenome Analysis:**  
  - Managing over 80,000 genomes presents significant technical challenges due to the data volume.  
  - We have developed a custom pipeline for efficient, scalable variant calling.  
  - Collaboratively extending Panaroo, with the Lee lab and Gerry Tonkin-Hill, to construct accurate pangenome graphs at unprecedented scale.

- **Vertical Pathoadaptation Mapping:**  
  - Identify pathoadaptive genes and regulatory mutational hotspots.  
  - Apply Poisson-based mutational burden tests and PySeer.  
  - Reveal convergent evolutionary steps taken by *K. pneumoniae* to adapt to the human host.


**Specific Focus: Leadership in HGT and Plasmid Analysis**

While the wider team maps core genome evolution, my specific focus will be leading the systematic characterisation of horizontal pathoadaptation. My approach will include:

- **Characterising Mobile Genetic Elements (MGEs):**  
  I will use advanced bioinformatic pipelines (ISEScan, MGEfinder, and custom scripts) to comprehensively identify insertion sequences, transposons, and other MGEs across the dataset.

- **Mapping MGEs to the Pangenome Graph:**  
  Because the accessory genome in *Klebsiella* is so dynamic, mapping MGEs onto the pangenome graph will be a key challenge. We will use the Panaroo and GGCaller pipelines to map MGEs to the pangenome graph and identify reference genomes by clustering the pangenome.

- **Analysing Plasmid Diversity and Domestication:**  
  I will characterise the structural variation, diversity, and evolution of plasmids within the *Klebsiella* population, tracing how specific plasmid backbones have fused and acquired AMR and virulence cassettes over time.

- **Integrating HGT with Phenotype:**  
  I will map these horizontal structural variations against our highly complete clinical metadata to determine their precise association with AMR, virulence phenotypes, and invasive disease. By distinguishing these abrupt horizontal mechanisms from the vertical transcriptional and regulatory hotspots we previously identified in *M. abscessus* and *P. aeruginosa*, I will isolate the specific evolutionary advantages conferred by MGEs.


### WP2. Predict Behaviour of *Klebsiella pneumoniae* and *Pseudomonas aeruginosa* from Whole Genome Sequence

**Objective:** To develop and validate next-generation machine learning models that predict clinically critical phenotypes — antimicrobial resistance and invasive disease propensity — directly from whole genome sequence (WGS), and to investigate how mobile genetic elements and plasmids are represented within genome-level embedding spaces.

**Overview and Preliminary Data:**
A central ambition of this WP is to determine whether phenotypic AST testing can be replaced or substantively reduced in large-scale bioinformatic research workflows where WGS is already being performed. To establish feasibility, I have already trained XGBoost models on one-hot encoded AMR gene presence/absence profiles generated by AMRFinderPlus across both *Klebsiella* (n=1,200 genomes) and *Pseudomonas aeruginosa* (n=450 genomes). These preliminary screens achieved AUROC 0.80–0.99 across antibiotics in both species (Figure [placeholder]), demonstrating that even modest training sets with simple gene catalogue features support high-accuracy resistance prediction. Separately, I have generated initial fine-tuned Bacformer embeddings for resistance prediction, achieving AUROC >0.97 in preliminary analyses (Figure [placeholder]). These early results, generated in collaboration with our machine learning team (Wiatrak, Weimann), substantially derisk the central aims of this WP and provide a strong platform for scaling to the full dataset.

***

**a) AMR Prediction and Generalisation**

I have collated a high-powered EBI dataset comprising >7,000 isolates with phenotypic AST results across 23 antibiotics, with over 2,500 measurements per antibiotic, providing exceptional power for both model training and cross-validation. Using this resource, I will pursue four complementary modelling strategies.

First, I will fine-tune Bacformer for AMR prediction by training a linear head with layer normalisation directly on whole-genome embeddings, following the approach established in Wiatrak, Abelson et al. (in submission). This leverages Bacformer's capacity to embed proteins in their full genomic context, capturing epistatic and regulatory interactions invisible to gene catalogue approaches. Second, I will train XGBoost models on known AMR gene presence/absence profiles from AMRFinderPlus as a rigorous interpretable baseline, enabling direct quantitative comparison of annotation-dependent versus annotation-free approaches.

Third — and most innovatively — I will develop a hybrid model architecture that integrates AMR gene annotation directly into Bacformer's embedding space. In this approach, each protein embedding will be augmented with AMRFinderPlus annotations for the relevant antibiotic, such that the resulting genome representation becomes a mixture of learnt sequence context and known resistance features. This hybrid strategy is designed to test whether prior biological knowledge can meaningfully enrich deep learning representations and improve generalisation to novel or understudied resistance determinants. I will compare the performance of this hybrid approach against a standard linear head trained on unmodified Bacformer embeddings. Finally, given the strong preliminary XGBoost performance in *Klebsiella*, I will extend all models to *Pseudomonas aeruginosa* and conduct systematic cross-species and cross-antibiotic comparisons to assess the generalisability of each approach.

***

**b) Invasive Disease Prediction**

Beyond resistance, a major unmet need is the ability to predict bacterial propensity for invasive disease — the likelihood that a strain isolated from a commensal context will cause bacteraemia rather than colonisation. Using isolation source as a proxy, I have assembled a dataset stratified by blood versus stool isolation for *Klebsiella*, providing a well-powered binary classification task. My initial Bacformer predictions for this split yield an AUROC of 0.65, which, while above chance, indicates considerable room for improvement and suggests that invasive propensity is a more complex, multi-factorial phenotype than resistance.

To improve performance, I will explore three strategies. First, I will run bacterial GWAS using PySeer (ref: Lees et al., *Bioinformatics* 2018) to identify accessory genome variants — including capsule loci and plasmid-borne virulence genes identified in WP1 — that associate with invasive isolation source, and incorporate these as additional features. Second, I will train XGBoost models directly on Bacformer embeddings as a non-linear alternative to the linear head, enabling the model to exploit higher-order interactions within the embedding space. Third, leveraging the breadth of our metadata-enriched dataset (completed from 50\% to 80\% completeness as described in the Statistical Analysis section), I will extend the analysis beyond blood versus stool to include respiratory, urine, wound, and abscess sources, all of which are sufficiently powered in our dataset for multi-class modelling. This multi-isolation-source comparison will provide a richer, clinically translatable map of the genomic determinants of tissue tropism and invasive capacity across *Klebsiella*.

A further limiting factor in the current Bacformer architecture is that, as a contextualised protein language model, it relies entirely on gene callers to define the input sequence and does not currently embed non-coding RNA, regulatory elements, or intergenic regions. These features are likely to carry important information about virulence and host adaptation, and their absence may partly explain the modest initial performance in invasive disease prediction. Two complementary approaches will address this. First, a next-generation hybrid model combining a protein language model with a DNA language model (PLM+DNALM) is currently in training and will be available for use in June 2026; I will fine-tune this architecture on the invasive disease prediction task to directly test whether the inclusion of non-coding genomic context resolves the performance deficit. Second, I will use the comprehensive pangenome and mobile element characterisation from WP1 — integrating Panaroo graph structures, GGCaller gene calls, and ISEScan insertion sequence annotations — to systematically investigate whether limitations in gene calling caused by transposable elements and mobile genetic elements result in fragmented or missing protein representations in Bacformer, and whether these gaps are disproportionately enriched in virulence-associated genomic regions. This analysis will provide direct mechanistic insight into the current model's limitations and a principled basis for its improvement.

***

**c) Plasmid Representation in Bacformer Embedding Space**

Bacformer encodes bacterial genomes as ordered sequences of contextualised protein embeddings, capturing both gene content and genomic neighbourhood. However, plasmids present a fundamental architectural challenge: as mobile elements residing outside the chromosome and capable of transferring between distantly related bacteria, it is unclear whether Bacformer's current training adequately captures their cross-species generalisability or their specific contribution to pathoadaptation and resistance dissemination.

I will address this directly by embedding *Klebsiella* genomes stratified by their plasmid content — as characterised in WP1 — and examining whether bacteria carrying the same plasmid cluster together in Bacformer's embedding space, irrespective of their chromosomal background. If bacteria sharing a plasmid fail to share similar embeddings, this would indicate that the model is not capturing plasmid-borne function as a generalisable cross-lineage signal. Such a finding would constitute a significant model limitation but simultaneously a major improvement opportunity: it would motivate architectural modifications to Bacformer, such as plasmid-specific positional encoding or separate plasmid versus chromosome training streams, that could substantially improve its capacity to predict AMR and invasive disease through learning plasmid-mediated gene transfer across species. These findings will be developed in close collaboration with Wiatrak and the machine learning team, with any architectural insights fed back to ongoing Bacformer development (ref: Wiatrak, Abelson et al., in submission).

***

**Expected Outcomes:**
1. Validated, scalable AMR prediction models for *Klebsiella* and *Pseudomonas aeruginosa* at AUROC >0.95 across all major antibiotics, with direct evidence on whether phenotypic AST can be reliably replaced by WGS in research workflows.
2. Quantified performance comparison of gene catalogue, deep learning, and hybrid modelling strategies, providing methodological guidance for the field.
3. A multi-label genomic predictor of *Klebsiella* tissue tropism and invasive disease across clinically relevant isolation sources, with mechanistic insight into the contribution of non-coding genomic regions and mobile element-driven gene calling failures to current model limitations.
4. A mechanistic characterisation of plasmid representation in Bacformer, with a clear framework for architectural improvements to foundation models trained on bacterial genomes.


WP3. Clinical Antimicrobial Resistance and Resilience in Chronic Lung Infection
Objective: To determine whether whole genome sequence (WGS) data, integrated with longitudinal clinical metadata, can predict antibiotic treatment efficacy in chronic respiratory infection — moving beyond the fundamental limitations of standard culture and AST — and to characterise the microbial, genomic, and ecological mechanisms that underlie treatment failure.

The Problem with Standard AST in Chronic Lung Infection

A landmark review in the Journal of Clinical Microbiology demonstrated that whilst a susceptible classification carries a positive predictive value of >90%, the ability of a resistant classification to reliably predict treatment failure is less than 35% — leading to the conclusion that what clinicians need are true resistance tests, which current methods do not provide (Doern & Brecher, J Clin Microbiol 2011).

A central motivation for this WP is that standard culture and AST, whilst guiding antibiotic prescribing in chronic lung infection, performs remarkably poorly as a predictor of clinical outcome in this context. Results in chronic suppurative infections are even worse than this.  For example, in chronic lung infection, with P. aeruginosa, treatment of pulmonary exacerbations succeeds at approximately the same rate (~60%) regardless of whether the isolate is classified as susceptible or resistant in vitro (Somayaji et al., J Cyst Fibros 2019; Aaron et al., JAMA 2005). Second, longitudinal sputum antibiograms are remarkably stable within individuals over time, remaining decoupled from the variable success or failure of specific treatment episodes (Fodor et al., PLoS One 2012; Zhao et al., Microbiome 2012, Walters & Ratjen, J Pediatric Infect Dis Soc 2022 — "The Sense and Nonsense of Antimicrobial Susceptibility Testing in Cystic Fibrosis",Flume & Muhlebach, Clin Infect Dis 2019 — "Reconciling Antimicrobial Susceptibility Testing and Clinical Response in Antimicrobial Treatment of Chronic Cystic Fibrosis Lung Infections").

A further and underappreciated limitation is the unreliability of the AST measurement itself. Standard in vitro susceptibility testing is performed under aerobic, planktonic, single-species conditions using nutrient-rich broth media that bear little resemblance to the microaerobic, nutrient-limited, polymicrobial sputum environment of the chronically infected lung. This matters profoundly: MIC values for P. aeruginosa tested in artificial sputum medium under microaerophilic conditions can be over 128-fold higher than those obtained under standard aerobic planktonic conditions for the same isolate and antibiotic (Haaber et al., J Antimicrob Chemother 2012). Furthermore, azithromycin MICs in physiologically relevant eukaryotic cell culture media (RPMI 1640) are significantly lower than those in standard prokaryotic broth, suggesting that bacteria routinely classified as resistant under standard conditions may behave as susceptible in the lung environment (Ravn et al., APMIS 2024). Intra-sample polyclonality compounds this further: isolates from the same sputum sample exhibit highly diverse MIC profiles, with categorical disagreement rates that call into question whether any single colony pick is representative of the infecting population (Bos et al., Microbiol Spectr 2023). Developing infection site-specific and disease-specific AST systems for each clinical context — sputum, urine, wound, CF versus non-CF bronchiectasis — is practically infeasible at scale. Using bacterial genomes to predict clinical treatment outcomes directly, integrating pathogen genomics with patient clinical data, represents an exciting and tractable alternative avenue, as demonstrated in urinary tract infection (Stracy et al., Science 2022).

## The SputaGen Cohort

The Floto Laboratory, in collaboration with the Cambridge Centre for Lung Infection (CCLI), has established a prospective clinical cohort specifically designed to address this challenge. The SputaGen study — which I designed and am Principal Investigator — has collected 642 intravenous antibiotic courses (encompassing 1,341 individual antibiotics) from patients with chronic lung infection, with standardised sputum samples collected before, during, and after each treatment course, resulting in a biobank of 1,273 longitudinally linked samples. This dense, longitudinal dataset, paired with detailed clinical metadata, provides an exceptional and largely unique resource for applying genomics to antibiotic outcome prediction.

### a) Evaluating Treatment Efficacy Using Culture and AST

As an initial step, I will systematically assess how historical culture and antimicrobial susceptibility testing (AST) results—those available to clinicians at the point of treatment decision—relate to actual patient outcomes in the cohort. The primary analysis will focus on *Pseudomonas aeruginosa*, with further assessments encompassing additional non-mycobacterial respiratory pathogens. Treatment efficacy will be quantified across the following four outcome domains:

- Global clinical change score
- Change in validated symptom questionnaire results
- Change in Chronic Airway Assessment Test (CAAT) score
- Time to next treatment course (categorized as <3 months, <12 months, or >12 months)

Each of these outcomes will be statistically correlated with contemporaneous AST data. Subgroup analyses will be pre-planned to stratify results by underlying disease (e.g., cystic fibrosis, non-CF bronchiectasis, other etiologies), antibiotic class, and pathogen species. This approach will produce the first robust, prospective analysis of how traditional sputum AST correlates with clinical measures of treatment effectiveness in chronic lung infection, offering clear, actionable evidence for or against the ongoing use of current AST practices in the clinical setting.

### b) Strain Identification and Dynamics as Predictors of Outcome

A key hypothesis, informed by Kishony and colleagues' demonstration that strain and species switching can underlie resistance emergence and treatment failure (measured via SNP distances), is that polyclonality and strain dynamics — largely invisible to standard culture — are major drivers of outcome in chronic lung infection.

In collaboration with microbiologists at the Floto and Bryant (Wellcome Sanger Institute) laboratories, I will implement the following integrated pipeline:

1) 16S rRNA metagenomic sequencing of whole sputum samples to characterise microbial diversity, species abundance, and community stability across timepoints

2) Culture-based approaches on P. aeruginosa-specific selective plates, with systematic isolation of individual colonies and PCR-guided lineage typing using Bryant lab strain-specific RNA guide protocols to identify co-infecting lineages

3) Whole genome sequencing of multiple distinct lineages per patient per timepoint, alongside parallel metagenomic WGS sweeps of unseparated sputum to capture polyclonal and culture-resistant diversity

4) Strain switching analysis via SNP distance-based lineage tracking across timepoints, directly mirroring the Kishony group's framework

Note that polymicrobial and polyclonal community structure can be partially lost during standard culture and downstream WGS; the parallel metagenomic approach is specifically designed to mitigate this limitation and preserve ecologically meaningful community-level information. I will then examine whether strain switching, lineage replacement, or acquisition of novel accessory elements predicts treatment failure and resistance emergence — applying the plasmid and MGE characterisation tools developed in WP1 and WP2 to interpret genomic changes in the clinical context.

### c) Advanced Genomic Prediction of Clinical Outcomes

Having established the baseline relationship between AST and outcomes, and characterised the extent of strain dynamics in the cohort, I will develop machine learning models that integrate multiple data streams to directly predict treatment efficacy from genomic and clinical data — bypassing AST as an intermediate proxy:

- Genomic features such as AMRFinderPlus gene profiles, plasmid and MGE content and representations of genomes explored in W.P 2 (For example, One Hot encoded or Bacformer embeddings) 

- Clinical metadata including culture history, prior WGS, BSI severity score, underlying disease, antibiotic history, and comorbidities

- Strain community structure (species, abundance and alpha diversity) derived from 16S and metagenomic profiling

I will first apply the XGBoost and Bacformer models developed and validated in WP2 to predict AST results from genome sequence as a baseline. I will then extend these to predict clinical outcome directly, in parallel with the approach demonstrated by Stracy et al. in urinary tract infection. RNA guide-based accessory gene tracking across multiple colonies will be used to label genomic sublineages, enabling fine-grained resolution of the within-patient genomic landscape and its relationship to clinical response.

### Expected Outcomes:

The first well-powered, prospective quantification of the relationship between sputum AST and clinical outcome in chronic lung infection, providing a definitive evidence base for or against current testing practice.

A comprehensive characterisation of strain dynamics, polyclonality, and community switching as predictors of treatment failure and resistance emergence in P. aeruginosa respiratory infection.

Machine learning models integrating pathogen genomics, community structure, and clinical metadata to predict antibiotic treatment outcomes in chronic lung infection, providing a proof-of-concept framework for genomics-guided antibiotic stewardship in this setting.

It is a first step towards direct genomic predictions of clinical outcomes bypassing or combining information from other clinical tests.  We expect this work to encounter multiple road blocks and have purposely designed an initial pathway that is achievable and focusses on single testable hypotheses (such as strain switching).  In due course other features such as Bacterial Killing and persister cells (Boeck, Liu) might add to these models.  

But the aim here is an initial well formulated pipeline to understand, test and retest bioinformatic predictions of clinical outcomes and iteratively develop transformatic models for clinical practice. 


## Outcomes for the Field and Career

- Generate models of *Klebsiella* pathogen evasion and evolution at both the global population level and in clinical settings, using advanced bioinformatics and machine learning approaches.
- Establish personal leadership in the field of *Klebsiella* pathogen evasion and evolution, building expertise in advanced bioinformatics and machine learning, and demonstrating the ability to transfer and design studies across machine learning and into clinical microbiology.
- Enhance the reputation of the Floto Lab and the University of Cambridge as leaders in these fields, supporting a pipeline for translating discoveries into intellectual property and commercial opportunities.

## Timeline

- See main text and GANTT chart

## Floto Lab Environment

- Weimann (publications)
- Wendy Figueroa (publications)
- Dynan (publications)
- Chris Ruiz
- Sebastian Bruchmann (Klebsiella publications)

## Collaborators (Partners)

- Josie Bryant
- John Lees
- Adrian Cazalles (doesn't have own lab; met and will iterate with him)
- Ewan Harrison (mentoring)

## Data Dependencies

- Data sources: EBI / NCBI, Bakrep
- Clinical data: SputaGen study

## Services and Equipment Required

- CPU time
- GPU time
- Cultures
- Assembly resources
- PhD student (UK fees)

## Risks

- Addressed above

## References

- To be completed

## Figures

- Global distribution of the Klebsiella set
- Clonal and sublineage variance of Klebsiella genomes
- Curated isolation source and host species
- Pathoadaption of PsA (from Weimann et al)
- Dating phylogenies in PsA 
- Global spread of M. abscessus (from Bryant et al)
- Identifying genes with GWAS from Pyseer and Hotspot analysis
- Bacformer architecture and predictions — AUROC and AUPRC, plus identifying genes using explainability (Captum)
- Exploring the embedding space of Bacformer
- Clustering of the pangenome with Panaroo
- Trajectories of pangenome in *S. aureus*
- Identifying operons with Panstripe and GGCaler
- Sputum microbial communities in bronchiectasis — Variability between individuals, but consistent signatures over time within individuals
- (additional: Sputum microbial communities in bronchiectasis — ...)
- GANTT chart

## GANTT Chart

---
