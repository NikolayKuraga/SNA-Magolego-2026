**Building Knowledge Graphs from Raw Text Sources**

## **Description**

This project focuses on building a small knowledge graph from raw text sources such as Wikipedia articles, books, news articles, lecture notes, or other document collections. The goal is to transform unstructured text into a graph where nodes represent meaningful entities and concepts, and edges represent relationships between them.

For example, from the sentence “Albert Einstein developed the theory of relativity,” the system can extract:

Albert Einstein \-\> developed \-\> theory of relativity

The project does not aim to build a perfect universal knowledge graph. Instead, it aims to implement a practical pipeline that can process a limited text collection and produce a useful graph for exploration and analysis.

## **Motivation**

Raw text contains many facts, but they are difficult to analyze automatically. A book or a Wikipedia category may contain hundreds of entities, events, places, dates, and concepts, but these connections are hidden inside natural language.

A knowledge graph makes these relationships explicit. It allows us to see which entities are central, which concepts are connected, and how information is structured across a document collection.

This can be useful for:

* summarizing a large text corpus;	  
* exploring connections between entities;  
* finding 	central concepts;  
* building a simple question-answering or search system;  
* comparing different documents by their entities and relations.

## **Goals**

The project has the following goals:

1. Select a	small raw text corpus.  
2. Extract named entities from the text.  
3. Extract 	simple relations between entities.  
4. Build a 	graph from extracted facts.  
5. Analyze and visualize the resulting graph.  
6. Evaluate the quality of extracted entities and relations.

## **Dataset**

The dataset can be chosen from one of the following sources:

* Wikipedia articles on one topic;  
* a public-domain book;  
* news articles;  
* scientific abstracts;  
* course materials;  
* any collection of plain text documents.

A realistic dataset size is:

* 20-100 Wikipedia articles, or  
* 1 short book, or  
* 100–500 short text documents.

Possible topic examples:

* history of space exploration;  
* machine learning concepts;  
* World War II events;  
* biographies of scientists;  
* mythology characters;  
* geography and countries.

The topic should be narrow enough to make the graph interpretable.

## **Methodology**

### **1\. Text Collection**

The first step is to collect raw text documents. Each document will be stored with basic metadata: title, source, and document ID.

### **2\. Text Preprocessing**

The text will be cleaned and split into sentences. Basic preprocessing includes:

* removing irrelevant symbols;  
* sentence segmentation;  
* tokenization;  
* optional lemmatization;  
* filtering very short or noisy sentences.

### **3\. Entity Extraction**

Named entities will be extracted from the text. These may include:

* people;  
* organizations;  
* locations;  
* dates;  
* events;  
* concepts.

Tools such as spaCy, Stanza, Natasha, or transformer-based NER models can be used.

### **4\. Relation Extraction**

The project will use simple relation extraction methods. Possible approaches:

* rule-based patterns;  
* dependency parsing;  
* co-occurrence inside the same sentence;  
* LLM-based extraction, if available.

For a short implementation, the main approach can be simple: if two entities appear in the same sentence, create a candidate relation between them. if the sentence contains a clear verb between the entities, use that verb as the relation label.

Example:

Sentence: “Marie Curie discovered polonium in 1898.”

Extracted relation:

Marie Curie \-\> discovered \-\> polonium

### **5\. Graph Construction**

The extracted entities become graph nodes. Extracted relations become graph edges.

Node types:

* Person;  
* Organization;  
* Location;  
* Event;  
* Concept;  
* Document.

Edge types:

* MENTIONS;  
* RELATED\_TO;	  
* DISCOVERED;  
* LOCATED\_IN;  
* PART\_OF;  
* INFLUENCED;	  
* custom 	extracted verb-based relations.

The graph can be built using NetworkX. Gephi or PyVis can be used for visualization.

## **Evaluation**

The project will use a simple manual evaluation.

A random sample of extracted entities and relations will be checked manually.

Metrics:

* entity extraction precision;  
* relation extraction precision;  
* number of nodes and edges;  
* percentage of documents connected to the graph;  
* number of isolated nodes;  
* interpretability of the largest connected component.

The project will also analyze central nodes using:

* degree centrality;  
* PageRank;  
* connected components;  
* community detection.

## **Expected Results**

The expected result is a working prototype that transforms raw text into a knowledge graph.

The project should produce:

1. A collected text corpus.  
2. A pipeline for entity and relation extraction.  
3. A graph of entities and relations.  
4. Basic graph statistics.  
5. A visualization of the resulting knowledge graph.  
6. A short 	evaluation of extraction quality.

The expected conclusion is that even simple extraction methods can produce a useful graph for exploring a text collection. The graph will not be perfectly accurate, but it should reveal central entities, important concepts, and meaningful connections hidden inside raw text.

## **References**

1. Hogan, A. et al. Knowledge Graphs. ACM Computing Surveys, 2021\.  
2. Ji, S. et 	al. A Survey on Knowledge Graphs: Representation, Acquisition, and 	Applications. IEEE TNNLS, 2022\.  
3. Grover, A., Leskovec, J. node2vec: Scalable Feature Learning for Networks. KDD, 2016\.  
4. Blondel, V. et al. Fast unfolding of communities in large networks. Journal of Statistical Mechanics, 2008\.