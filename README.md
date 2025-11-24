# Comparative Analysis of Fact-Checking Organizations

This repository contains a comparative analysis of fact-checking organizations through toxicity and sentiment analysis, K-Means clustering, and Latent Dirichlet Allocation (LDA). We investigate how different fact-checking organizations approach misinformation detection and vary in their editorial patterns.

**Context:** This study was conducted as part of the Text and Media Analytics course in the Master's program in Applied Data Science at Utrecht University.

**Contributors:** Philip Wehry, Tom Adelmeijer, Sneha Manikkandan, and Hong-Ye Guo

**Data Source:** This analysis builds upon research by Sian Lee, Aiping Xiong, Haeseung Seo, and Dongwon Lee ([Harvard Misinformation Review](https://misinforeview.hks.harvard.edu/article/fact-checking-fact-checkers-a-data-driven-approach/)). We use their scraped dataset of fact-checking articles from multiple organizations.

**NOTE:** This repository was created after the study was completed as an addition to my personal portfolio. The code has been refactored to meet portfolio standards, addressing inconsistencies and logical errors from the original implementation, as well as incorporating improved data analysis methods. As a result, there may be discrepancies between the findings presented here and those in the original course paper.

Main changes include:
- Making the code more DRY. 
- Adding a section analysing the top words used by both Politifact and Snopes across time (Section 2.4.2.1. in the Notebook) to analyse correlations between certain words and noteable events.
- Making graphs more visually informative.
- Instead of only analyzing the toxicity and sentiment of the articles made in response to the claims, but also including the claims itself in the toxicity and sentiment analysis (Section 6.1.1. in the Notebook).

## Introduction
The rapid spread of misinformation in the digital age has made fact-checking organizations essential in verifying claims and curbing false information. Platforms like PolitiFact and Snopes play a crucial role in this effort, yet their effectiveness and consistency in evaluating claims have come under scrutiny. With Meta’s decision to scale back its third-party fact-checking initiatives, concerns have emerged regarding the reliability, agreement, and methodologies used by these independent fact-checking platforms. While their ratings aim to provide clarity, inconsistencies often arise due to differences in rating systems, contextual interpretations, and linguistic nuances.
A key challenge in misinformation assessment is evaluating claims that contain high toxicity or strong sentiment, as emotionally charged language may correlate with how fact-checkers interpret and classify information. This study seeks to answer the main research question: 

“What are the factors affecting fact-checking evaluations between PolitiFact and Snopes, particularly focusing on toxicity, sentiment, and thematic patterns.”

To answer the research question, we will be looking into two sub-questions:

1.	How do toxicity and sentiment levels relate to the ratings assigned by PolitiFact and Snopes?
2.	What thematic patterns are common across "Fake" and “Real” claims as rated by PolitiFact and Snopes?

Through statistical analysis and linguistic evaluation, this study examines trends in misinformation assessment using a computational approach to fact-checking methodologies. Sentiment and toxicity analysis will be used to evaluate the role of emotionally charged content, and thematic patterns will highlight recurring themes and structures in misinformation. By integrating multiple methods, the study aims to clarify fact-checking transparency, consistency, and potential biases in claim appraisal.

 
## Literature Review
### Similarity and Differences Between PolitiFact and Snopes
Fact-checking groups include PolitiFact and Snopes (PolitiFact, n.d.; Snopes, n.d.). Identifying various claims and evaluating their veracity, accuracy, and any biases that could affect how information is disseminated and interpreted is the main goal of both PolitiFact and Snopes. Both of them are members of the International Fact-Checking Network (IFCN), a consortium that unites different fact-checking groups under a common umbrella. Five fundamental criteria are upheld by fact-checking organisations thanks to IFCN (IFCN, 2024):
1.	Non-partisanship and Fairness
2.	Transparency of Sources
3.	Transparency of Funding and Organization
4.	Transparency of Methodology
5.	Open and Honest Corrections Policy

By adhering to these principles, PolitiFact and Snopes aim to maintain credibility and trust in their fact-checking efforts. However, some differences occur in the types of claims both parties assess and the way they rate the claims. Snopes, for example, employs a larger rating system with 20 categories compared to PolitiFact with only six (Snopes, 2024; PolitiFact, 2024). A comprehensive table that summarises the various rating systems is located in Appendix A, Sections 1 and 2. As a result, the disparity in granularity draws attention to the two organisations' disparate scopes. Snopes' more comprehensive and sophisticated rating system implies that its main goal is to look into claims that are true, making sure that those that have been confirmed to be authentic are appropriately categorised. On the other hand, PolitiFact's more streamlined rating system indicates an emphasis on investigating suspicious claims, simplifying its scale to focus on degrees of falsehood rather than nuanced truthfulness.

### Misinformation on Public Opinion and Behavior
The influence of misinformation on public opinion and behavior is very serious. For example, Lazer et al. (2018) show how misinformation about democratic processes may undermine trust in the democratic process through the spread of false claims about how elections and the media work.

This may also affect public health behavior in that in the COVID-19 pandemic spread of fake news regarding health guidelines and vaccination policies has caused a lot of hesitancy, especially among some groups. A peer-reviewed article by Friggeri et al. (2014) discussed how false health information has rapidly spread across social media, feeding into a broad-based misunderstanding of actual facts that gets in the way of public health interventions.

In this respect, misinformation does not only touch on specific political or health behaviors but also covers general social behavior, such as consumer choice or the enhancement of social cleavages. The ability of misinformation to shape behavior points out the demand for sound information and the elaboration of strategies in contrasting fake news, including improving media literacy and strengthening information verification processes. Vosoughi et al. (2018).

### Sub-Question 1: How do toxicity and sentiment levels correlate with the ratings assigned by PolitiFact and Snopes?
According to research, statements that are regarded as true are typically more neutral or even positive, but those that are rated as false frequently contain more poisonous language and negative sentiment. Venkit and Wilson (2021), for example, discovered that common sentiment and toxicity models assign higher toxicity scores to language that can be associated with misinformation, indicating that erroneous assertions tend to use more forceful or emotionally charged vocabulary. Parallel to this, Venkit et al. (2023) found that biases in these tools are highly associated with poorer truth ratings, indicating that the wording of a claim might influence fact-checkers' perceptions of its correctness. Furthermore, it has been demonstrated by Brassard-Gourdeau and Khoury (2020) that sentiment analysis can be used to identify harmful words at an early stage, which in turn might flag misleading claims before they spread. By turning the fact-checkers’ ratings into numbers, researchers can better study how changes in toxicity and sentiment match up with the ratings, offering a clearer picture of the link between language style and bias in claims.

### Sub-Question 2: Thematic Patterns
Fake news is a broad and adaptable phenomenon that can emerge from various sources and be applied to virtually any topic. Its features and structure, however, exhibit recognisable trends. According to a meta-analysis by Tandoc et al. (2020), fake news is a typology with six different categories that are frequently seen in scientific literature rather than a single concept: 
-	Satire
-	Parody
-	Fabrication
-	Manipulation
-	Propaganda
-	Advertising

The intricacy of fake news is demonstrated by these six categories, which also highlight how crucial context is in differentiating between fake and authentic news. As demonstrated by the distinctions between satire, propaganda, and blatant fabrication, misinformation can take many different forms, necessitating critical analysis to determine its impact and aim.
A thorough meta-analysis of the common themes, feelings, forms, and objectives of false news is carried out in another paper by Pérez-Escolar et al. (2023).
Pérez-Escolar’s analysis of different types of fake news mostly overlaps with that of Tandoc et al. except for that Pérez-Escolar uses categories created by Wardle and Derakhshan (2017) which expands the topology to eight categories instead of the six found in Tandoc et al.:
-	Misleading
-	False 
-	Fabricated
-	Manipulated
-	Impostor
-	False
-	Satire or parody
-	No specific type

This expanded classification reinforces the complexity of fake news, illustrating how different forms of misinformation exploit trust, authority, and context to mislead audiences.

The paper also lists twelve different themes within fake news (with number 1 being the most common theme and number 12 being the least common):
1.	Health
2.	Politics/democracy
3.	Scientific experiment
4.	Science (conspiracy theory)
5.	Economics, development, and business
6.	Education
7.	Climate change
8.	Immigration
9.	Gender
10.	Historical facts
11.	Famous people
12.	Young generation

The importance of a thematic analysis is to understand the different topics and themes that are most prevalent within fake news. This aids in forecasting which misleading stories are most likely to surface and proliferate. Researchers may better understand how disinformation spreads and which subjects are most susceptible to manipulation by charting the thematic landscape of fake news. This will help them develop more effective measures to lessen the negative effects of fake news on society.

## Data & Methodology
Dataset Description
The datasets used in this study is derived from a research paper conducted by Harvard Kennedy School researching the behaviour and agreement levels among four different fact-checking organizations. The four organizations researched were Snopes, PolitiFact, Logically, and the Australian Associated Press FactCheck (AAP). The data mainly consists of the articles that are written by the fact-checking organizations, and was gathered using a web scraping algorithm that spans the dates January 1, 2016, to August 31, 2022. Table 1 shows the number of articles scraped for each organization:

| Organizations | Number of Articles |
| ------------- | ------------------ |
| Snopes        | 11639              |
| PolitiFact    | 10710              |
| Logically     | 4365               |
| AAP           | 844                |

Table 1 - Overview of the dataset sizes

Due to the significant disparity in the number of articles scraped from each organization within the given time frame, this case study will focus solely on PolitiFact and Snopes. These organizations were selected not only for their larger datasets but also to ensure a balanced, consistent, and comprehensive analysis. Table 2 outlines the overlapping attributes present in both datasets:

| **Politifact Attributes** | **Snopes Attributes** | **Explanation**                                                              |
| ------------------------- | --------------------- | ---------------------------------------------------------------------------- |
| 1. claim                  | 1. claim              | The text of the claim being fact-checked.                                    |
| 2. link                   | 2. link               | URL of the fact-check article.                                               |
| 3. rating                 | 3. rating             | Truthfulness rating assigned by the fact-checker (e.g., True, False, Mixed). |
| 4. author                 | 4. author_name        | Name of the author who wrote the fact-check article.                         |
| 5. title                  | 5. title              | Title or headline of the fact-check article.                                 |
| 6. tags                   | 6. tags               | Keywords or thematic tags associated with the claim.                         |
| 7. bodyt                  | 7. bodyt              | Full text or main body content of the fact-check article.                    |
| 8. sources_num            | 8. sources_num        | Number of sources cited in the fact-check.                                   |
| 9. sources                | 9. sources            | List or text of sources referenced.                                          |
| 10. fc_date               | 10. date_published    | Date when the fact-check was published.                                      |

Table 2 - Overview of the main attributes in Snopes and PolitiFact datasets

This analysis will focus on the attributes `claim`, `rating`, `bodyt`, and `cdate`/`date_published`. The two organizations also differ in their rating systems and scales, with PolitiFact using six categories and Snopes using fourteen. This difference reflects the varying scopes of the organizations: PolitiFact focuses on verifying suspicious claims, while Snopes places greater emphasis on verifying truthful claims. To ensure that both datasets can be compared properly, the ratings need to be normalized. Table 3 displays the ratings from both organizations and their new normalized rating. An explanation for why certain ratings are either grouped together or removed is given in Appendix A, Section 1.

| **Politifact rating** | **Snopes rating**                                                           | **Normalized Rating** |
| --------------------- | --------------------------------------------------------------------------- | --------------------- |
| `TRUE`                | `True`, `Correct Attribution`, `Legit`, `Recall`                            | `True`                |
| `mostly-true`         | `Mostly True`                                                               | `Mostly True`         |
| `half-true`           | `Mixture`                                                                   | `Half true`           |
| `barely-true`         | `Mostly False`, `Miscaptioned`, `Misattributed`, `Outdated`                 | `Mostly False`        |
| `FALSE`, `pants-fire` | `False`, `Scam`, `Originated as Satire`, `Unfounded`                        | `False`               |
| NaN                   | `Legend`, `Unproven`, `Labeled Satire`, `Research In Progress`, `No Rating` | REMOVED               |

Table 3 - Mapping of PolitiFact and Snopes Ratings to a Normalized Truthfulness Scale

## Methodology
To answer the research question, the following methods will be employed. To start, an Exploratory Data Analysis (EDA) will be conducted. This step will look at the distribution of the articles across the two organizations and across the normalized rating, to get a preliminary understanding of how balanced the data is. Additionally, the claims and the article bodies (`bodyt`) will be analyzed to visualize the most common words. This helps develop an understanding of the dominating narratives and themes in the dataset, as well as potential biases or points of interest of each organization. 

Next, Data Preprocessing will be applied to prepare the data for analysis. This involves calculating TF-IDF vectors for each document (i.e. each claim) and then applying cosine similarity to the vectors to find documents with a similarity score threshold of 0.5 and higher. A similarity score of 0.5 to is chosen to align with the methodology of the paper on which this case study is based. Articles with a rating of 0.5 and higher will be normalized, and below will be removed. Details on the ratings removed and normalized can be found in Table 3.

For further simplification, Feature Engineering is used to further normalize the ratings to a binary classification of ‘Real’ and ‘Fake’ called the ‘Veracity Score’. This binary classification will make it easier to compare the results across the dataset.

Following EDA, Data Preprocessing, and Feature Engineering, manual assessment will be conducted to evaluate the accuracy, precision, and recall of the matches identified with a similarity score threshold of 0.5.  To do this, a random sample containing 50% of the matched claims is manually assessed by four individuals who will rate the match as either ‘True’, ‘Partial’ or ‘False’. Partial matches are matched claims that need to be further assessed by others due to nuanced differences in the match. See Table 5 for examples. The result of this can then be used to aggregate and make assumptions for all matches, giving us insights into what percentage of the matches are false matches, and at which threshold value (i.e. how accurate the matches are and how reliable the analysis is).

The final step involves Data Analysis, which will be used to answer the main and sub-research questions:.

1.	Sub-question 1 - How do toxicity and sentiment levels correlate with the ratings assigned by PolitiFact and Snopes?
Sentiment and toxicity which will be calculated using the libraries Detoxify and `VADER` sentiment analyzer from the `nltk` library. The toxicity and sentiment scores will be calculated for the body text (see table 8 for information on which attribute ‘body’ refers to) as it provides more context. Using these scores we can answer the second sub-question by developing a correlation heatmap of the toxicity, sentiment, and normalized ratings. Since the normalized ratings are non-numeric ordinal categories, they will be converted into numeric ordinal values to enable correlation analysis.
2.	Sub-question 2 - What are the thematic patterns in the claims categorized as Real or Fake by PolitiFact and Snopes?
K-means clustering and Linear Discriminant Analysis (LDA) will be used for topic modelling to identify different themes and topics between Fake and Real claims.

