# Title: “Influence network” hidden in Quotebank

## Data Story:
[“Influence network” hidden in Quotebank](https://popkova-a.github.io/ADA-data-story-2021/)

## Abstract:
Influence has long been studied in the fields of sociology, communication, and political science. Traditional communication theory states that a minority, called influentials, excels in persuading others. Generally, more quotations of a person indicate more impact of this speaker or at least his/her higher exposure to the public. 

In this project, our intention is to reveal the unobvious relationships between the most authoritative speakers by creating a directed graph with weighted edges based on how much other people talk about a particular person according to Quotebank, a corpus of quotations attributed to the speakers who uttered them, extracted from news articles of 2015-2020. The graph represents an “influence network” of Quotebank speakers. The world is small (recall “six degrees of separation”), especially for famous public figures, so we are also interested in how two seemingly unrelated people in different fields could be connected to each other.

## Research Questions:
* **Who are the most authoritative people that other speakers talk about?** 
    - Introducing the new measure of “influence” defined as the number of mentions of the person by other speakers, we are interested in the fact who occupies the highest positions in the ranking based on this impact rate. 
* **Does the number of speaker’s quotes in the dataset correlate with his/her influence?**
    - Since the quotation rate of a person can be also considered as a measure of his/her exposure to the public (the more news sources quote the speaker, the more impact he/she has), we are going to analyze which people satisfy both of the criteria.
* **What potential/hidden communities do the speakers form? And how do they link together?**
    - In general, we tend to classify people by their occupations, genders, races, etc. But are there potential communities that aren’t that obvious? We are looking forward to discovering hidden communities with a clustering algorithm, and trying to investigate how these latent communities form.
* **How does the “influence network” evolve over 2015-2020?**
    - After the construction of the “influence network”, we would like to study further its evolution in these 6 years and answer questions: Whose influence increases over time and whose decreases? Who joined and who left the ‘most influential people’ community? etc.

## Proposed additional datasets (if any): 
Metadata about the speakers in the Quotebank dataset gathered in the `speaker_attributes.parquet` file. We use it for detection of the same people called different ways in the Quotebank dataset (`aliases` feature) and for analysis of politicians' proportion among the most influential speakers (`occupation` feature).   
 
## Methods:
In order to determine the most influential people in the network, we use the Katz centrality measure for directed graphs.

Further, we apply a community detection algorithm named Girvan-Newman to decompose the most influential speakers’ neighborhoods into different heavily interlinked groups, which results in hierarchical clustering. Since the Girvan-Newman method encounters some problems when applied to some directed graphs with a special structure, then our approach is to treat a directed graph as undirected when using this method for community detection. We will use modularity to evaluate the quality of a community clustering.

In order to track the evolution and structure of communities over time, we use Jaccard similarity, which is a statistic used for gauging the similarity and diversity of sets.

Other characteristics of the graph that we get are the connectivity of the directed graph and its in-degree distribution. As the “influence network” representation, we draw a graph using the NetworkX Python library, also we show the relationships between the most authoritative persons by plotting a heatmap.

## Proposed Timeline and Organization Within the Team:
| Time | Work | Team Members |
| ---- | ---- | ---- |
| 26/11 | Initially, we will work with the `speaker_attributes.parquet` file and use the ‘aliases’ attribute to combine different nodes corresponding to the same person in one node and get a one-to-one correspondence between a name and a person. | Irina |
| 27/11-29/11 | We are going to build graphs for different years from 2015 to 2020 and compare them. | Irina & Yuxiao  |
| 30/11-03/12 | Then, our plan is to implement community clustering with the Girvan-Newman method and compare the evolution of communities in different years applying Jaccard similarity. We will use modularity to evaluate the quality of a community clustering. | Anastasia & Yuhan |
| 04/12-06/12 | Our next step is to find the most influential people for each year applying a threshold to the Katz centrality of the nodes. We are going to represent the relationships between the most authoritative speakers by means of a heatmap plot. | Yuxiao |
| 07/12-09/12 | Using the ‘occupation’ attribute of the .parquet file, we plan to find the proportion of politicians among the most influential speakers. Depending on the results, we will also check Qids corresponding to other occupations or align the ‘occupation’ attribute manually if there are only a few exceptions in the speakers’ set. | Yuhan |
| 10/12-17/12 | The final step is to upload the read.me file and prepare the final data story by means of Jekyll. | All |

## Contributions:
| Team Member | Responsibilities |
| ---- | ---- |
| Anastasia | <ul><li>Preliminary data analysis;</li><li>Community analysis;</li><li>Creating the plots for the data story.</li></ul> |
| Irina | <ul><li>Building the graph;</li><li>Plot description;</li><li>Data story composition.</li></ul> |
| Yuhan | <ul><li>Politician proportion analysis;</li><li>Creating the plots for the data story;</li><li>Data story composition.</li></ul> |
| Yuxiao |  <ul><li>Building the graph;</li><li>Construction of the heatmap and degree plots;</li><li>Data story composition.</li></ul> |

## References:
1. Timoté Vaucher, Andreas Spitz, Michele Catasta, and Robert West. 2021. Quotebank: A Corpus of Quotations from a Decade of News. In The Four- teenth ACM International Conference on Web Search and Data Mining (WSDM ’21), March 8–12, 2021, Virtual Event, Israel. ACM, New York, NY, USA, 9 pages. https://doi.org/10.1145/3437963.3441760
2. M. E. J. Newman, M. Girvan Finding and evaluating community structure in networks // Physical review E, 2004. Vol. 69.
3. Gao, Z. & Liu, X. (2017). Personalized Community Detection in Scholarly Network. In iConference 2017 Proceedings, Vol. 2 (pp. 107-112). http://hdl.handle.net/2142/98863
4. https://networkx.org/documentation/stable/_modules/networkx/algorithms/centrality/katz.html
5. https://graphscope.io/docs/v0.1.1/reference/networkx/builtin.html
6. https://en.wikipedia.org
