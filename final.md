# Machine Learning Applications in Genomics
##### Rayan Massoud
##### Xin Yi (Linda) Lei
##### Aarthi Venkat

I. [Introduction](#1)   
II. [Supervised vs. Unsupervised Learning](#2)  
III. [Model Selection and Optimization](#3)   
IV. [Supervised Learning Applications](#4)  
  a. [Hidden Markov Models](#41)  
  b. [Linear Regression](#42)  
V. [Unsupervised Learning Applications](#5)  
  a. [Hierarchical Clustering](#51)  
  b. [K-means Clustering](#52)  
VI. [Sources](#6)  

## I. Introduction<a name="1"></a>

Machine learning is an interdisciplinary subfield of computer science and mathematics involving algorithm and method development for predictive modeling. In the post-genomic era, interpreting large genomic datasets with high complexity, dimensionality, and noise has proven a daunting task, and machine learning has allowed bioinformaticians to computational and mathematical approaches to understand the data. Many early applications of machine learning in genomics involved annotation of genomic sequence elements based on DNA pattern recognition. ML approaches have since extended to other types of data, such as RNA-Seq differential gene expression, ChIP-Seq and chromatin annotation. ML can also help elucidate the underlying mechanisms, such as regulatory network and pathway inference.

## II. Supervised Learning vs. Unsupervised Learning <a name="2"></a>

Machine learning is often discussed as two separate methods of statistical inference- supervised and unsupervised learning. In this section, we will explore both these topics and introduce the type of data needed. 

#### a. Supervised Learning
Supervised learning involves training a model with already labelled data in order to make predictions about unlabelled examples [1]. As the model learns the general properties of the data and identifies which features are most relevant, it uses those learned properties to identify new information in the unlabelled data. 

As such, there are three elements to supervised learning:

- Training input: a collection of data points, each with an associated label
- Post-training input: a collection of data points
- Post-training output: predicted label for the unlabelled data points

#### b. Unsupervised Learning
Unsupervised learning, on the other hand, is trying to find structure in a data set without any labels [1]. Note that for this type of learning, there is no training input, so structure often involves clustering and dimensionality reduction to ease interpretation of large and complex genomic datasets.

- Input: a collection of data points
- Output: predicted label for the unlabelled data points

## III. Model Selection and Optimization  <a name="3"></a>  
![](/final_figures/tvt.png)  

Model selection and optimization involves splitting the data into training, validation, and testing in order to ensure the model is both specific and predictive, but generalizable.  

The model is initially fit on a <b>training</b> dataset, that is a set of examples used to fit the parameters. Then, the fitted model is tested on the <b>validation</b> dataset, which offers an unbiased evaluation of the model and finetunes the hyperparameters and to make sure there is no overfitting. Finally, the <b>test</b> dataset is a dataset used to provide an unbiased evaluation of a final model fit on the training dataset.  

## IV. Supervised Learning Applications<a name="4"></a> 
Examples of supervised learning in genetics and genomics range from DNA pattern recognition to text-mining. In this section, we will discuss two prominent examples of supervised learning, and demonstrate some applications and their influence to the field.

#### a. Hidden Markov Models  
One of the most prominent examples of supervised learning is the Hidden Markov Model, hereinafter referred to as the HMM. HMMs are a type of Bayesian network that use transition and emission probabilities to interpret the state probability of a dataset. HMMs have been used in bioinformatic modeling from chromatin state discovery [2] to gene finding [1]. Here, we present a simple gene-finding HMM used to capture the properties of a protein-coding gene.  
![](/final_figures/gene_finding.jpg)  

This model requires as input a training set of labeled DNA sequences. Labels for such a model may include the start and end coordinates of a gene, splice sites, and UTR. The model uses this training data to learn general properties of genes, including the DNA pattern near donor and acceptor splice sites, the expected length distributions for each element, and patterns within elements, such as typical codons in an exon vs. an intron. The trained model can then use these learned properties to identify novel genes that resemble the genes in the training set.  

Note certain limitations to this type of model, namely that it is incapable of identifying overlapping genes or multiple isoforms of the same gene. Similar limitations exist for other applications of HMMs, such as in topologically associating domain (TAD) discovery and directionality index creation in Hi-C data, wherein a simple HMM as above cannot find a hierarchy of TADs. For biological questions like this, more complex models are useful.  

#### b. Linear Regression  
Another commonplace example of supervised learning in genomics is linear regression, which can be used in population genomics and medical genetics to perform single SNP association testing through optimizing the sum of the squared differences in a dataset. Notice how this dataset can be modeled in three ways - additive, dominant, and recessive. Each model attempts to estimate the proportion of phenotypic variation, in this case, cholestorol, explained by the SNP, and uses the coefficient of determination, or R^2 value, to assign confidence to that estimation. 
![](/final_figures/regression.JPG)  
One approach to choosing a statistical model is to choose the simplest model that has the right parameters and right assumptions based on our biological data, and work toward building rigor and complexity. Thus, it is important to understand what the assumptions of each model are, and how it relates to the problem we are trying to solve. In the additive model, for example, by putting a line to the dataset, we are exploring the phenomenon that the number of minor alleles, or major alleles, is correlated with phenotypic variation, and as such the two homozogytes are equally different to the heterozygote. Such phenomenon is important when performing association studies, such as for purposes related to drug target discovery.  

# Reference
[1] Libbrecht M.W., Noble W. S. Machine Learning Applications in Genetics and Genomics. Nature Reviews Genetics. 16, (2015) 321-332.  
[2] Ernst, Jason and Manolis Kellis. “ChromHMM: automating chromatin-state discovery and characterization” Nature methods vol. 9,3 215-6. 28 Feb. 2012, doi:10.1038/nmeth.1906  

