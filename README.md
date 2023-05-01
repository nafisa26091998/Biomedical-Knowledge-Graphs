# Biomedical-Knowledge-Graphs
"Combination of OCR, named entity linking, relation extraction and external enrichment databases to construct a biomedical knowledge graphs."

A python project that allows you to parse a research paper in PDF format, extract entities and relationships, link the entities with present target knowledge bases (ontologies) and create a knowledge graph for the same.

By the end of this project, we will be able to construct a graph with the following schema.
![image](https://user-images.githubusercontent.com/130223304/235447785-fe4a6910-6a83-4005-8746-d8768c5c8674.png)

The project will store our graph in Neo4j, a graph database that uses the labeled property graph model. There may be one or multiple writers for each article. We will utilize NLP to extract both medical entities and their connections after breaking the article's content into sentences. The fact that we will record relations between items as intermediate nodes rather than relationships may seem a little counterintuitive. The main driving force for this choice is that we need a record of the original text from which the relationship was retrieved. You cannot have a relationship pointing to another relationship in the labeled property graph model. Because of this, we redesign the relationship between medical ideas as an intermediary node. This will also allow a domain expert or subject matter expert (SME) to evaluate if a relation was correctly extracted or not.

Named entity recognition techniques are used to detect relevant entities or concepts in the text. For example, in the biomedical domain, we want to identify various genes, drugs, diseases, and other concepts in the text.
![image](https://user-images.githubusercontent.com/130223304/235448848-8cd37f74-d0a6-4e2d-9a90-909bfea69dc2.png)

In this example, the NLP model identified genes, diseases, drugs, species, mutations, and pathways in the text. As mentioned, this process is called named entity recognition. An upgrade to the named entity recognition is the so-called named entity linking. The named entity linking technique detects relevant concepts in the text and tries to map them to the target knowledge base. In the biomedical domain, some of the target knowledge bases are:

- MESH
- CHEBI
- OMIM
- ENSEMBL

The main benefit of linking medical entities to a target knowledge base is that it facilitates entity disambiguation for us. For instance, domain experts would tell you that ascorbic acid and vitamin C are the same thing, thus we don't want to represent them in the graph as different entities. The second justification is that by assigning ideas to a target knowledge base, we may improve our graph model by retrieving data from the target knowledge base about the mapped concepts. If we were to utilize the ascorbic acid example once more, we could quickly retrieve more data from the CHEBI database if we knew its CHEBI id.
![image](https://user-images.githubusercontent.com/130223304/235449032-a48d4ccd-b24e-43a8-bf9e-7acd16a63a75.png)

# Disclaimer
This project is intended for research purposes and must not substitute a healthcare professional's medical directory or search engine.
# Usage
This project is have been developed in .ipynb format for amendments and ready to use. It requires python version >=3.8.

