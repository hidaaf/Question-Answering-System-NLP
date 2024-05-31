# Question-Answering-System-NLP
This project was part of the TKO_8964 Textual Data Analysis course at the Universiy of Turku.

Authored by :
- Hiba Daafane
- Shadman Ishraq
- Dishant Sukhwal

This project was centered around the Question Answering (QA) task which was introduced in the course. The overall objective was to gain some understanding of what the QA systems are able to do, and where their limitations lie. The assignment was structured into different tasks, each addressing a specific functionality or aspect of understanding the QA system.

## Task 1: Familiarize yourself with the original data

This task introduced two papers, which summarize the SQuAD datasets, the goal was to try and truly understand what this data is about, we were also encouraged to list a few aspects we found especially puzzling or interesting.

  http://arxiv.org/abs/1606.05250
  
  http://arxiv.org/abs/1806.03822


## Task 2: Look at the data, learn to know it

For this task we wrote a little program which will randomly sample at least 25 `(context,question)` pairs and then manually record what we think the answer should be. Then we cross-check with the gold answer in the data. In this experiment we came to the conclusion that the anticipated answers of the questions were indeed attained by the predictor in most cases.

## Task 3: Test the QA models in practice

In this section we needed to pick at least 10 paragraphs from any non-encyclopedic source and invent a handful of questions for each just like it was described in the papers. In addition, we needed to test a ready-made QA model on these (we chose the 'DistilBERT base cased distilled SQuAD' model), and report our findings.

Based on the results we got it seems like in most cases the model was successfully able to get the right answer for the questions. Additionally, we provided some misconstrued questions which were not mentioned in the paragraph & the model was also able to predict that execpt for one question. So, looking at the scores and the prediction the model performed decently. In addition, the model wasn't able to answer 3 questions(one of them was misconstrued question) and in all instances the score wasn't more than 0.4.


## Bonus Task 4: Implement the retriever-reader model

Given a question, and a set of background documents - here we used the YLE dataset - we used the dense representation model to retrieve the top K articles most similar to a given question, and then use the QA model to find the answer from among these top K articles. 

To retrieve the top K articles most similar to the question, we used the argsort method of numpy to get the indices of these articles based on the cosine similarity scores. We were then able to retrieve the article text for these top K articles and use a QA model to find the answer. To handle long articles, we split the articles into smaller sections of a fixed length (512 as it is the maximum length of input that can be accepted by the model) and feed these sections to the QA model one at a time. We then loop through each article and its sections to find the section that gives the highest score from the QA model, and finally we output the answer with the highest score.

## Bonus Task 5: Format your test data in the SQuAD-2 json format

For the final task we prepared our test data from tasks 2+3 in the valid json format for SQuADv2 and made it loadable as a dataset which can be distributed as a small QA test set. This needed some format reverse engineering, and learning how the dataset loading works in HuggingFace.


