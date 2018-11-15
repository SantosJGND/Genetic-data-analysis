# Stats Lab

*Exploring and classifying genetic data.*

In recent years the size and quality of biological data sets have increased at a tremendous rate. It is fair to say that we 
have not yet reached the plateau of that development, so that students and researchers alike will be facing even larger data 
sets in the near future.

As the amount of information increases, so must the methods we use to explore, analyse and even present that data. 
The field of population genetics is undergoing a profound paradigm shift, as researchers move from exploiting the sparse, 
hard-won data sets of old to finding ways to understand and encompass the swaths of data their laboratories turn in. 

In recent years i have had the privilege of working on one of the largest genetic data sets to date (2018). In summary, this 
project involved the description of genetic structure across thousands of possible sites. I would like to leave 
here some of the more useful insight and tools that resulted. This repository consists in a series of Jupyter notebooks, 
each exploring some method or applications i found particularly useful.

Notebooks are organised in order of increasing complexity and, in most cases, of chronological development. This development was driven in 
greater part by the need to study the relation between statistcis that describe structure in data. Metrics to describe structure vary
across fields of research. Here, the focus is on the description of genetic data. 

Use NBviewer directly to explore the [notebook library](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/tree/master/). 
[NBviewer](https://nbviewer.jupyter.org/) supports the 2D images produced in the scripts (copy-paste the url of a notebook onto the tab provided).


## I. Binary samples. Population distribution and identification.

- Notebooks: 1 - 5

Structure in data is either used to study real-world processes influencing the distribution of observed variables or as a basis for
prediction. From a mathematical point of view these two goals are indistinguishable. In either case the focus of scientific research is
on the description of the laws that govern the generation of new data. This description comes in the form of the combined distributions
of all variables available to describe the subject of study. 

In the study of the variation of binary data, the simplest assumption is that of a binomial probability of observation at the smallest 
unit of measurment available. In the case of genetic data, this unit is the single nucleotide polymorphism (SNP).

Througout the notebooks provided, individuals are simulated as samples of *L* binary markers (0, 1, .., i), coded 0 and 1, of frequency *pi* 
within a given population *K*. Populations were simulated as multivariate Bernoulli variables *Sk*, where each variable *Ski* represents the 
binomial probability of an event. We further assumed independent markers and modelled the distributions of allele frequencies *Sk* from the 
Beta distribution, as an approximation of the stationary allele frequencies described in Williamson *et al.* (2004, see Jiang and Cockerham 1990; Sawyer and Hartl 1992). ). Allele frequency vectors 
of size *L* were sampled from the Beta distribution for various combinations of mean and variance of this distribution (see [Notebook 1](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/1.%20Generating_haplotypes.ipynb)).

To the extent that individuals are defined as combinations observations of the same weight, principal component analysis (PCA) presents an intuitive
summarisation of population samples. In this context, given a sufficient number of samples, a basic description of a population entity is 
the probability density function of its samples in PCA feature space. In Notebooks [2.](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/2.%20Local_classification.ipynb),
 [3.](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/3.%20Mislabelling.ipynb), [4.](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/4.%20X-material.ipynb),
  and [5.](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/5.%20Visualizing%20KDE.ipynb), the use of kernel
density estimates ([KDE](https://scikit-learn.org/stable/modules/density.html)) for 
the characterisation and assignment of individual samples is explored. 


## II. Population structure.

Notebooks: 6 - 11

The study of the relation of different descriptors and population structure requires the analysis of samples from as many different populations
as possible ([Fig. 1](https://github.com/SantosJGND/Stats_Lab/blob/master/Complementary_data/Ideo_order_Fst_example.png)).
This section deals with organising simulations so as to easily control for population number, sample size and correlation. 

- [Notebook 6](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/6.%20A%20link%20to%20FSTs.ipynb)
describes the use of PCA to organise allele frequency vectors by genetic proximity, as measured in *Fst* 
([Fig. 2](https://github.com/SantosJGND/Stats_Lab/blob/master/Complementary_data/Ideo_comparison.png)).

- [Notebook 7](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/8.%20Controlling%20for%20size.ipynb) 
Describes the relation between the proximity of source populations and euclidian distances of sample projections in PCA space.
The impact of sample size is studied.

- [Notebook 8](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/7.%20Machine%20Learning%20for%20Genomics.ipynb)
describes the use of PCA to infer genetic distances measured in *Fst*.

- Notebooks [9](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/9.%20Conditional_variation.ipynb) 
and [9b](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/9b.%20Conditional_Var%2C%20but%20using%20Pops.ipynb) 
describe the use of KDE to extract a measure of distribution overlap. 

- Notebook [10](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/10.%20Indexing_MS.ipynb) 
and [11](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/11.%20Visualising%20Overlaps.ipynb) 
explore the behaviour of Mean Shift classification under different patterns of structure.


## III. Admixture.

Notebooks 12 - 13

This section extends on the analyses in Notebooks 2 through 5. The use of the KDE of known populations for the characterisation 
of samples in scenarios containing outliers and cases of mislabelling is explored. However, this time we will build on the infrastructure
developed in Section II to compare classification output across structure and admixture scenarios.

- [Notebook 12a](https://nbviewer.jupyter.org/github/SantosJGND/Genetic-data-analysis/blob/master/12a.%20Admixture%20simulations.ipynb) 
introduces individual IDs and admixture proportions to combine admixture and genetic structure ([Fig. 3](https://github.com/SantosJGND/Stats_Lab/blob/master/Complementary_data/3way_example.png)).

- [Notebook 12b](https://nbviewer.jupyter.org/github/SantosJGND/Stats_Lab/blob/master/12b.%20Inference_Admixed.ipynb) 
KDE-based assignment of admixed scenarios.

- [Notebook 13](https://nbviewer.jupyter.org/github/SantosJGND/Stats_Lab/blob/master/13.%20Outliers_genetic_structure.ipynb) 
focuses on the identification of samples from non-reference sources under different structure parameters ([Fig. 4](https://github.com/SantosJGND/Stats_Lab/blob/master/Complementary_data/Supplemental_Figure_S11.png)).

- [/LAI_interface](https://github.com/SantosJGND/Stats_Lab/tree/master/LAI_interface): analysis of simulated samples using Local Ancestry Inference software 
([Fig. 5](https://github.com/SantosJGND/Stats_Lab/tree/master/LAI_interface/Supplemental_Figure_S6.png)).

- [Digits](https://github.com/SantosJGND/Digits): an aside on controlling for admixture proportions for many individuals as a function of 
proxy genomic position ([Fig. 6](https://github.com/SantosJGND/Digits/blob/master/Ideo_step__OutlierTh0.0001_Z1.png)).


## References

- Jiang CJ and Cockerham CC. 1987. Use of the multinomial Dirichlet model for analysis of subdivided genetic populations. Genetics **115**: 363-366.

- Sawyer SA and Hartl DL. 1992. Population genetics of polymorphism and divergence. Genetics **132**: 1161-1176.

- Williamson S, Fledel-Alon A and Bustamante CD. 2004. Population genetics of polymorphism and divergence for diploid selection models with arbitrary dominance. Genetics **168**: 463-475.
