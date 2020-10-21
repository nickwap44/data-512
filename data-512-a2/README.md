# DATA 512 - Assignment 2: Bias in Data
Nicholas Wapstra

## Goal
The goal of this assignment was to identify potential sources of bias in the Wikipedia Talk corpus of human-annotated data in an exploratory data analysis, and some of the implications of this bias on the behavior of machine learning models trained on then data.

The Wikipedia Talk corpus consists of three datasets. Each dataset contains thousands of online discussion posts made by Wikipedia editors who were discussing how to write and edit Wikipedia articles. Crowdworkers labelled these posts for three kinds of hostile speech: “toxicity”, “aggression”, and “personal attacks”. Many posts in each dataset were labelled by multiple crowdworkers for each type of hostile speech, to improve accuracy.

I will be exploring two research questions: 1) How consistent are labelling behaviors among workers with different demographic profiles?; and 2) Are some kinds of hostile speech harder for people to agree on than others?

## Data Sources
Data was collected from the Perspective API repository and the Detox wiki page.

1. The Perspective API ([GitHub](https://github.com/conversationai/perspectiveapi/tree/master/2-api)) provides machine learning models to score the perceived impact a comment might have on a conversation.
2. The Detox wiki page ([Overview](https://meta.wikimedia.org/wiki/Research:Detox), [Data Dictionary](https://meta.wikimedia.org/wiki/Research:Detox/Data_Release)) provides information on the underlying project and the data dictionary.

## Data and Code for Replication
Source data from (in .tsv format) from [Figshare](https://figshare.com/projects/Wikipedia_Talk/16731):

- aggression.tsv
- aggression_comments.tsv
- aggression_demo.tsv
- attack.tsv
- attack_comments.tsv
- attack_demo.tsv
- toxicity.tsv
- toxicity_comments.tsv
- toxicity_demo.tsv

Code for data acquisition and analysis: 
data-512-a2.ipynb

Final visualizations: 
- data-512-a2-1.png (aggression bar graph)
- data-512-a2-2.png (aggression score distribution)
- data-512-a2-3.png (aggression score bar graph)
- data-512-a2-4.png (hostile speech disagreement plot)

## Fields
The value of the fields from the final datasets are as follows:

- worker_id (int64): Provides the id of the worker providing the annotation
- rev_id (int64): Provides the id of the comment with the annotation
- gender (string): Gender of worker (male/female)
- english_first_language (int64): Indicates whether or not the worker's first language is English (0,1)
- age_group (string): Age group of the worker (under 18, 18-30, 30-45, 45-60, over 60)
- education (string): Education status of the worker (none, some, hs, bachelors, masters, doctorate, professional)
- aggression (float64): Is a comment considered aggressive by reviewer (0,1)
- aggresion_score (float64): How aggressive was the comment (-3 (most aggressive), 3 (most friendly))
- attack (float64): Is the comment considered to be a personal attack (0,1)
- toxicity (float64): Is the comment considered to be toxic (0,1)
- comment (string): Comment text
- Disputed (boolean): Were the reviewers in disagreement about whether a comment should be considered hostile speech (True, False)
