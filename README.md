## Building a machine-learning taxon classifier to inform genomic classification in malaria mosquitoes (Google Summer of Code project)

Identifying _Anopheles_ mosquitoes species with precision is critical for malaria control. The _Anopheles gambiae sensu lato_ (_An. gambiae s.l._) complex, the primary malaria vector in sub-Saharan Africa, consists of multiple species, including _An. arabiensis_, _An. coluzzii_, and _An. gambiae s.s._. Each of these species has unique ecological roles and varying susceptibility to vector control strategies, leading to heterogeneity in their contribution to malaria transmission.

Taxonomic identification of _Anopheles_ mosquitoes is challenging as they are morphologically identical, and genomic data is key to correctly classify individuals. Misclassification can lead to suboptimal interventions and flawed epidemiological insights, underscoring the need for robust, scalable and accessible classification frameworks.

This project aims to optimise, enhance, and package a cloud-native genomic taxon classifier for _Anopheles_ mosquitoes. The starting point will be to optimise an existing random-forest classifier to improve accuracy and computational efficiency while validating the predictions against expertly curated taxonomic datasets. 

As the current implementation is trained on high-resolution genomic data from the Vector Observatory, which integrates whole-genome sequence data for over 25,000 mosquitoes, a key aspect of the project will be to package the classifier in an accessible manner, ensuring any research group can use this tool.

---

### GSoC application:
To support the GSoC application process, we have included additional resources in this repository to support futher exploration of the classification problem described above. 

### Data sources
Our group has built the [Malaria Genome Vector Observatory](https://www.malariagen.net/vobs), which integrates whole-genome sequence data for over 25,000 _Anopheles_ mosquitoes. If you would like to look at some of these data in more depth, we have included a subset that we will be working on during the initial phase of this project. 

>  Under the `data/features.tsv` path, you can find a file with data from genotypes from 2784 mosquitoes -- each row in this file corresponds to an individual file. On each of these files, we want to take genotypes (`GT`) data as input. Our team uses the [Zarr format](https://zarr.readthedocs.io/en/stable/) to optimise access to genomic data. We suggest having a read through the official documentation, if you are not familiar with this format, and to take a look at [this blogpost](https://alimanfoo.github.io/2018/04/09/selecting-variants.html) by [@alimanfoo](https://github.com/alimanfoo), for a walkthrough through an example of accessing whole-genome sequence data and extracting genotype (`GT`) information.

> Under the `data/labels.tsv` path, you can find a file with taxon labels, one per corresponding mosquito. To generate taxon classification labels within the Vector Observatory, our team uses a methodology which combines information from an initial assignment from a random-forest classifier together with expert manual curation for these taxa. Classes vary greatly in size and a few samples, labeled "unassigned", do not belong to any class.

### What do we want to optimise/enhance?
The most important thing is to balance the accuracy and precison of the taxon classification. A close second is to ensure any code is well optimised and computationally efficient and/or works on a small subset of the data, the main impediment to a lot of approaches is how long training takes, given the size of the genome of each mosquito. 


### How to contribute?
Our main challenge can be summarised as: **How to come up with a taxon assignment for one individual mosquito which is robust & efficient?**

We are particularly interested on hearing about interdisciplinary ways to think or tackle this task. This is a difficult problem which will benefit from discussion and different perspectives. You could tackle this from a computational angle which focuses on optimisation, scalability and a balanced data set, a genomic angle which focuses on how to best sentment the genome to tackle this; or somewhere in the middle. With a lot of possible input features available, we encourage you to come up with the approach you think is best, and you would be the most interested on working with.

* If you have any additional resources or ideas that you have identified that would be of benefit for this project, or for the malaria community, we encourage you to open an issue or a pull request to include them on this repository.

* If you decide to put together together a full GSoC proposal, please share them via email to your initial point of contact via the GSoC mailing address.


### Further reading:

#### On genomics & malaria:
- Malaria Genome Vector Observatory: https://www.malariagen.net/vobs
- Article on the distribution of African mosquitoes belonging to the Anopheles gambiae complex: https://www.cell.com/partod/fulltext/S0169-4758(99)01563-X

#### On API development:
- Our team has built and maintains an open-source cloud-native Python API: https://github.com/malariagen/malariagen-data-python, which supports analysis of genomic data from mosquitoes, we are always on the look for contributors and ideas for improvements.
