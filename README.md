# Topic 02: Deep mutational scanning data analysis to reveal sequence function relationships

### *Project overview and guidelines*

-   [Introduction](#introduction)
-   [Objective](#objective)
-   [Description of datasets](#description-of-datasets)
-   [Literature review](#literature-review)
-   [How to structure your project](#how-to-structure-your-project)
    -   [Project proposal](#project-proposal)
    -   [Project](#project)

Supervisor
----------

_Prof. Dominik Niopek_  ([dominik.niopek@uni-heidelberg.de](mailto:dominik.niopek@uni-heidelberg.de))  
_Jan Mathony_  ([jan.mathony@tu-darmstadt.de](mailto:jan.mathony@tu-darmstadt.de)) 

Tutor: _Benedict Wolf_ ([b.wolf@stud.uni-heidelberg.de](mailto:b.wolf@stud.uni-heidelberg.de))    


Introduction
------------
Deep mutational scanning (DMS) is a powerful experimental technique to analyse the effects of mutations on protein function. The technique builds on large protein variant libraries, where each variant carries a different single or multiple mutations. High-throughput screening of such libraries for functional variants enables the mapping between mutations and their effects on protein activity.
By comparing the abundance of each variant in the library before and after the screening or selection process, deep mutational scanning enables researchers to infer the effects of each mutation on the molecule's function and to construct detailed maps of how sequence variation affects molecular activity. This approach has been applied to a wide range of biological systems, including enzymes, receptors, transcription factors, and viruses, and has provided valuable insights into how molecular evolution proceeds and how proteins and nucleic acids achieve their specific functions.
In this practical, we want to explore DMS data from various proteins and try to identify general patterns that exist throughout the dataset. Based on this information we will try to develop models that can help us to identify mutation tolerant sites.
Finally, we will compare the results to mutation patterns derived from evolutionary related proteins and will interpret them.

Objectives and work plan
------------------------

You will analyze a dataset that encompasses DMS results corresponding different proteins from a variety of different publications. The overall goal is to identify general trends in mutation patterns. The following questions provide a rough guideline and first ideas of the features that can be analyzed:
- Is there a specific mutation tolerance for certain amino acids that can be identified?
- Can you relate the data to secondary structure elements or functional sites?
- Do the observed trends correlate between proteins?
- How do these compare to evolutionary conservation.
- Can you identify a subset of features that can help with the prediction of mutation tolerance?

To exemplify the observations and effects in detail, each group can focus on one of the following proteins:  
1) E. coli beta-lactamase
2) TP53
3) GFP
4) BRCA1

Description of datasets
-----------------------

**DMS Datatables**  
DMS substitution datasets of 87 proteins in a CSV format.
- mutant (str): describes the set of substitutions to apply on the reference sequence to obtain the mutated sequence (eg., A1P:D2N implies the amino acid 'A' at position 1 should be replaced by 'P', and 'D' at position 2 should be replaced by 'N'). Present in the the ProteinGym substitution assays only (not indels).
- mutated_sequence (str): represents the full amino acid sequence for the mutated protein.
- DMS_score (float): corresponds to the experimental measurement in the DMS assay. Across all assays, the higher the DMS_score value, the higher the fitness of the mutated protein
- DMS_score_bin (int): indicates whether the DMS_score is above the fitness cutoff (1 is fit, 0 is not fit)

**DMS metadata**  
- The UniProt_ID of the corresponding protein, along with taxon and MSA depth category
- The target sequence (target_seq) used in the assay
- Details on how the DMS_score was created from the raw files and how it was binarized

**Download**  

:warning: ADD LINKS :warning:


Literature
----------

Two reviews that decribe DMS and directed evolution methods, providing a good background with respect to the underlying experimental techniques and concepts:
- Fowler, D., Fields, S. Deep mutational scanning: a new style of protein science. Nat Methods 11, 801–807 (2014). https://doi.org/10.1038/nmeth.3027
- Packer, M., Liu, D. Methods for the directed evolution of proteins. Nat Rev Genet 16, 379–394 (2015). https://doi.org/10.1038/nrg3927

Publications, referring to some of the provided data, especially the key proteins:
- Findlay, G.M., Daza, R.M., Martin, B. et al. Accurate classification of BRCA1 variants with saturation genome editing. Nature 562, 217–222 (2018). https://doi.org/10.1038/s41586-018-0461-z
- Stiffler, M.A., Hekstra D.R., Ranganathan R., Evolvability as a Function of Purifying Selection in TEM-1 β-Lactamase,
Cell, 160, 5, 882-892 (2015) https://doi.org/10.1016/j.cell.2015.01.035.
- Giacomelli, A.O., Yang, X., Lintner, R.E. et al. Mutational processes shape the landscape of TP53 mutations in human cancer. Nat Genet 50, 1381–1387 (2018). https://doi.org/10.1038/s41588-018-0204-y
- Sarkisyan, K., Bolotin, D., Meer, M. et al. Local fitness landscape of the green fluorescent protein. Nature 533, 397–401 (2016). https://doi.org/10.1038/nature17995

A very recent paper, that focuses mainly on the analysis and interpretation of mutation patterns from DMS experiments:
- Leander M., Liu Z., Cui Q., Raman S. (2022) Deep mutational scanning and machine learning reveal structural and molecular rules governing allosteric hotspots in homologous proteins eLife 11:e79932 https://doi.org/10.7554/eLife.79932



How to structure your project
-----------------------------

### Project proposal

You first task will be to define a **project proposal**, which should
include

-   summary of literature on this dataset
-   questions you want to address
-   approximate timetable

You will present this project proposal together with a literature review
on the subject 3 week after the beginning of the semester (10 minute
presentation + 5 minutes discussion).

### Project

You project should contain the following elements:
- **descriptive statistics** about the datasets
- **graphical representations**
- **dimension reduction** analysis (PCA, clustering or k-means)
- **statistical tests** (t-test, proportion tests etc)
- **linear regression** analysis, either uni- or multivariate _(this point is optional!)_

#### Data cleanup

You will be analyzing multiple data sets together. It is
essential that you explore each dataset and clean it. Cleaning can refer
to many things:

-   Removing/Imputing missing values
-   Removing low variance columns/rows
-   Removing batch effects
-   Removing outlier samples (only if it is due to technical issues !!)
-   Making sure that data is in the correct format, for example, numbers
    should be encoded as numeric and not as characters. Categorical
    variables should be factors etc.
-   Re-ordering rows/columns in meaningful and useful ways

#### Data exploration

Now that you have cleaned data, explore your data to understand its
structure. Perform basic exploratory data analysis.

-   Look at the distribution of the overall data, specific samples or
    features.
-   Als consider the experimental differences behind the datasets
-   Identify additional useful metadata that can be fetched from public databases
-   Visualize the data distribution
-   Visualize the inter-dependencies (e.g. correlations) among specific samples/features of
    interest
-   Check some of your hypothesis like - is something high/low between
    two conditions etc

#### Data reduction

You have a high dimension matrix, that is, you have way more features
 than observations.

-   Try out methods to reduce the dimensionality of this data.
-   Cluster your samples to identify similar and dis-similar groups
-   Check how well the groups separate based on the features of your
    interest

#### Data modelling

Use linear regression to evaluate the relation between variables and predicting one using others.
