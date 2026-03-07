DISCUSSION OF WP3 and issues with it.  Planning to improve. 

Current:
------
Previous version of WP3:

Reworked Draft: WP3 Background & Research Plan
WP3: Clinical Antibiotic Prediction in Chronic Lung Infection
Objective: To determine whether whole genome sequence data, integrated with longitudinal clinical metadata, can predict antibiotic treatment efficacy in chronic respiratory infection — moving beyond the fundamental limitations of standard culture and AST — and to characterise the microbial and genomic mechanisms underlying treatment failure.
Background
Standard AST is a poor predictor of clinical outcome. Even in ideal free-floating, monomicrobial infections, it remains unreliable. Most clinical infections are polymicrobial and non-planktonic—settings where AST has almost no predictive value (Doern & Brecher, 2011).
Two mechanisms drive this failure. First, polymicrobial communities confer antibiotic protection to co-habiting pathogens (O'Brien et al., 2022). Second, MIC varies profoundly with growth environment (Haaber et al., 2012). Chronic lung infections exemplify this: their polyclonal (Bos et al., 2023), structurally complex nature decouples in vivo efficacy from in vitro susceptibility (Somayaji et al., 2019), leaving antibiograms static despite fluctuating outcomes (Fodor et al., 2012).
This demands culture‑independent prediction. Outcome models must take as input the true strain and species composition of the infecting community, including strain switching and polyclonality (Stracey et al, 2022), but they must be independent of both culture and AST. Genomics offers this: resolving community structure directly from clinical samples, integrating it with patient metadata, and training ML models that bypass AST entirely.
The SputaGen Cohort
The Floto Laboratory and Cambridge Centre for Lung Infection have established a prospective cohort specifically designed to address this challenge. The SputaGen study — which I designed and lead as Principal Investigator — has collected 642 intravenous antibiotic courses from patients with chronic lung infection, with standardised sputum samples collected before, during, and after each course, yielding a biobank of 1,273 longitudinally linked samples.
Research Plan
a) AST versus Outcomes. I will systematically correlate historical AST results with clinical outcomes across four domains: global clinical change score, validated symptom questionnaire, Chronic Airway Assessment Test (CAAT) score, and time to next treatment course. Subgroup analyses will stratify by pathogen, antibiotic class, and disease. This will produce the first robust prospective analysis of AST predictive value in chronic lung infection.  We need to say that we will collate these.  But I think this is virtually assumed.  How useful is it?  We know it doesn’t work.  But it will be direct evidence that it doesn’t work.
b) Strain Dynamics. Informed by Kishony and colleagues' demonstration that strain switching underlies resistance emergence and treatment failure, I will implement an integrated pipeline to capture both community-level diversity and high-resolution clonal dynamics. First, we will use 16S rRNA metagenomic sequencing to characterise overall community composition and species abundance. Second, to overcome the limitations of standard bulk metagenomics—which conflates multiple co-infecting sublineages—we will employ targeted approaches to isolate and sequence individual P. aeruginosa lineages from complex samples. By resolving the precise assemblies of major clones per patient per timepoint, we can conduct accurate SNP distance-based strain switching analysis without the confounding effects of intra-sample polyclonality. We will leverage state-of-the-art strain resolution techniques (incorporating tools developed by the Bryant lab alongside novel bioinformatic deconvolutions) to ensure distinct lineages are accurately tracked. MGE and plasmid characterisation tools from WP1 will then be applied to interpret genomic changes in this high-resolution clinical context.(I
 
We can also analyse strain switching in our samples as a single outcome.
 
c) Genomic Outcome Prediction. I will develop machine learning models integrating genomic features of the main bacterial lineages (by annotated genes and / or by whole genome embeddings).   I will combine this with bacterial community structure (starting with species abundance and alpha diversity), clinical metadata (antibiotic history, BSI severity, underlying disease, comorbidities). By driving the predictive model with precise strain-level assemblies rather than unrepresentative colony picks or blended MAGs, we aim to predict treatment efficacy directly—bypassing AST entirely.



----------------------------


The last paragraph on line 13 includes "This demands culture independent prediction". We can't say this! It would be ideal, but metagenomics of whole sputum (without culture) in notoriously impossible (I need a reference for this) because of the low abundance of bacterial genomic material and the high amount of bronchial contamination.

So, while we need methods independent of AST, we will in the first instance need to use culture. We should state that our plan (because of the limitations of culture and AST) is structured step wise testing:

(and parts of this will need to go into our text)

We need to methods to analyse genomic diversity in sputum samples. Many studies have been done of 16S RNA speciation of sputum samples in bronchiectasis and CF and show chronic polymicrobial infections with signatures of the individual much more stable than others even over courses of antibiotics. Thus 16S gives us little information to predict dynamics. But this belies the complexity of the polyclonal infection. For instance within pseudomonas infection there may be many strains and clones in a single infection. We need to be able to model or assess this clonality in polymicrobial infections. To tackle this we will stepwise:

1/. Use 16S RNA PCR amplication to assess the species structure of sputum samples (reference)
2/. In the first instance we will then focus on pseudomonas aeruginosa infection which is present in > 50% of our samples and is the dominant pathogen when present (ref). We will use Pseudomonas aeruginosa specific culture media on a select test set of 30 sputum from previous studies (ACE-CF). We will then conduct a split experiment to best characterise the Pseudomonas aeruginosa cultured:
a). We will separately culture multiple colonies and identify different clones on the culture plate using specially designed pseudomonas lineage PCR guides (Bryant lab, any reference would help!). We will then conduct WGS on these independent colonies separately, likely to establish ~ 60 metagenomic samples from the 30 sputum cultures.
b). For comparison and validation, we will take a plate sweep of the initial culture which will mix the polyclonal sample and run mGEMs (reference) to test if it can be reliably be used in Pseudomonas aeruginosa infection, as it has been done in E. coli.
c). We will not perform AST on these samples as this will be estimated using techniques from WP2.

3/. Having established the most prescient sequencing approach (either plate sweeps or individual colony picks and guide from strain specific PCR) to the polyclonal infections we will then expand our sequencing to test strain switching during treatment with antibiotics (ref. Kishony). We will need to be able to measure the strains independently and assess their abundance (can we do this??). We will do this on xxx samples (we need to estimate power here for detection of strain switching using the paper of Kishony as reference which is in your context window for the space).

4/. Then we move onto the last section of the WP which is Genomic Outcome Prediction.

I am considering dropping WP3. a) as it is terribly boring and sure to not have a result from the previous literature. However, it is practical, simple and achievable, derisking the WP to produce some output.

I'm just not sure we can claim what we had for WP3.c):

"I will develop machine learning models integrating genomic features of the main bacterial lineages (by annotated genes and / or by whole genome embeddings).   I will combine this with bacterial community structure (starting with species abundance and alpha diversity), clinical metadata (antibiotic history, BSI severity, underlying disease, comorbidities). By driving the predictive model with precise strain-level assemblies rather than unrepresentative colony picks or blended MAGs, we aim to predict treatment efficacy directly—bypassing AST entirely."

Given our description of the uncertainty above.

Of course this is a grant pitch. We don't have to do everything. It just needs to sound convincing, achievable and well planned.

Can you please review this and the previous draft WP3 (below) and first discuss the overall plan and how we can position this and also give key references for the problems of metagenomic cultures I am discussing as this is key.

