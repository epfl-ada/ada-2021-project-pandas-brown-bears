# Title: “Influence network” hidden in Quotebank
## Abstract:
Influence has long been studied in the fields of sociology, communication, and political science. Traditional communication theory states that a minority, called influentials, excels in persuading others. Generally, more quotations of a person indicate more impact of this speaker or at least his/her higher exposure to the public. 

In this project, our intention is to reveal the unobvious relationships between the most authoritative speakers by creating a directed graph with weighted edges based on how much other people talk about a particular person according to Quotebank, a corpus of quotations attributed to the speakers who uttered them, extracted from news articles of 2015-2020. The graph will represent an “influence network” of Quotebank speakers. The world is small (recall “six degrees of separation”), especially for famous public figures, so we are also interested in how two seemingly unrelated people in different fields could be connected to each other.
## Research Questions:
* What are the most authoritative people that other speakers talk about? 
* What proportion of the most influential speakers are politicians? 
* Does the number of speaker quotes in the dataset correlate with his/her influence? 
* What hidden communities do the speakers form? How do they link together? 
* How does the dynamic “influence network” evolve over 2015-2020 years?
## Proposed additional datasets (if any): 
Metadata about the speakers in the Quotebank dataset gathered in the `speaker_attributes.parquet` file. We will use it for detection of the same people called different ways in the Quotebank dataset (`aliases` feature) and for analysis of politicians' proportion among the most influential speakers (`occupation` feature).   
## Methods:
In order to determine the most influential people in the network, we will use `Katz centrality` measure for directed graphs. 

Further, we will apply a community detection algorithm named `Girvan-Newman` to decompose the most influential speakers’ neighborhood into different heavily interlinked groups, which results in a hierarchical clustering. Since the Girvan-Newman method encounters some problems when applied to some directed graphs with special structure, then our approach is to treat a directed graph as undirected when using this method for community detection. We will use `modularity` to evaluate the quality of a community clustering. 

In order to track the evolution and structure of communities over the time, we will use `Jaccard similarity`. 

Other characteristics of the graph that we plan to get are connectivity of the directed graph and its in-degree distribution. As the “influence network” representation, we draw a graph using the `NetworkX Python library`, also we plan to show the relationships between the most authoritative persons by plotting a heatmap.
## Proposed Timeline:
| Time | Work | Team Member |
| ---- | ---- | ---- |
| 1 Day | Our first step is to explore deeper and proceed with further data wrangling based on previous preprocessing results. | xxx |
| 1 Day | Initially we will work with the `speaker_attributes.parquet file` and use the ‘aliases’ attribute to combine different nodes corresponding to the same person in one and get a one-to-one correspondence between a name and a person. | xxx |
| 3 Days | We are going to build graphs for different years from 2015 to 2020 and compare them. | xxx |
| 4 Days | Then, our plan is to implement community clustering with the Girvan-Newman method and compare the evolution of communities in different years applying Jaccard similarity. We will use modularity to evaluate the quality of a community clustering. | xxx |
| 2 Days | Our next step is to find the most influential people for each year applying a threshold to the in-degrees of the nodes. We are going to represent the relationships between the most authoritative speakers by means of a heatmap plot. | xxx |
| 3 Days | Using the ‘occupation’ attribute of the .parquet file, we plan to find the proportion of politicians among the most influential speakers. Depending on the results, we will also check Qids corresponding to other occupations or align the ‘occupation’ attribute manually if there are only a few exceptions in the speakers’ set. | xxx |
| 7 Days | The final step is to upload the read.me file and prepare the final data story by means of Jekyll. | All |
## Organization Within the Team:

## Questions for TAs (optional):
 Add here any questions you have for us related to the proposed project.
