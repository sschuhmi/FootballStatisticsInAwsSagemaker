## Proposal for Capstone Project

# Topic: "Predicting results in modern football games using Machine Learning algorithms in AWS SageMaker"

Part of Udacity's Nanodegree Program "AWS Machine Learning Engineer" (nd189) - 

## 1. Domain Background

<!-- Student briefly details background information of the domain from which the project is proposed. Historical information relevant to the project should be included. It should be clear how or why a problem in the domain can or should be solved. Related academic research should be appropriately cited. A discussion of the student's personal motivation for investigating a particular problem in the domain is encouraged but not required. -->

In modern football, data in shape of match statistics is comprehensive and vital e.g. for club managers to investigate strengths and weaknesses of their clubs, but also for fans placing their bets on specific football matches. 
In the last years, the amount of analysis data that is generated in modern football matches using cameras, drones or other advanced technologies has significantly increased. This makes football statistics to an interesting goal for data scientists and machine learning engineers predicting results by exploiting modern approaches and algorithms from their research fields.

## 2. Problem Statement

<!-- Student clearly describes the problem that is to be solved. The problem is well defined and has at least one relevant potential solution. Additionally, the problem is quantifiable, measurable, and replicable. -->

The problem we are addressing here is the prediction of the winner of a match without exploiting the score data (i.e., which team shot how many goals). A football match always consists of exactly two teams that play against each other: The first team is called the 'home team', while the second team is called the 'away team'. In order to win a match, a team has to score more goals than the other team after full time (90 minutes; note that in international championships, it is common to continue the match in case of a draw after full time by extra time and/or penalty shooting; however, we do not regard extra time or penalty shootings here). If both teams scored the same number of goals, the result is called a 'draw'.

Thus, in a single match, there are always 3 possible results where exactly one will be the outcome:

- 'win_home': The home team scores more goals than the away team and wins
- 'win_none': The home team and the away team score exactly the same number of goals, i.e. the result is a draw
- 'win_away': The away team scores more goals than the home team and wins

While other works (e.g., ...) rather focused on the algorithmic aspects, we are additionally aiming at making the results production-ready in AWS by additionally considering topics like deployment, security, or cost efficiency of our solution. To achieve this operationalizing, we are relying on the modern AWS SageMaker framework ([cite]).

<!-- Refer to related work and note the differences -->

## 3. Solution Statement

<!-- Student clearly describes a solution to the problem. The solution is applicable to the project domain and appropriate for the dataset(s) or input(s) given. Additionally, the solution is quantifiable, measurable, and replicable. -->

## 4. Datasets and Inputs

<!-- The dataset(s) and/or input(s) to be used in the project are thoroughly described. Information such as how the dataset or input is (was) obtained, and the characteristics of the dataset or input, should be included. It should be clear how the dataset(s) or input(s) will be used in the project and whether their use is appropriate given the context of the problem. -->

In this project, we rely on the well-known StatsBomb open source dataset, which encompasses extensive statistics of thousands of played matches in different competitions like the global World Cup, continental championships such as the Copa America in South America, or club championships like the European Champions League.

StatsBomb comprises competitions as well as seasons, with matches for each competition and season.
Each match consists of over 3,400 events in average as well as the lineups. The matches are widely spreat across 190+ competitions, combined with player-location data for 40+ key leagues.
There exist 119 different events which are included, such as passes, shots, fouls, dribblings, or goalkeeper related events (e.g., saves, clearances, punches).

The StatsBomb dataset is publicly available via GitHub [1].

## 5. Benchmark Model

<!-- A benchmark model is provided that relates to the domain, problem statement, and intended solution. Ideally, the student's benchmark model provides context for existing methods or known information in the domain and problem given, which can then be objectively compared to the student's solution. The benchmark model is clearly defined and measurable. -->

We exploit the large open data set and use Machine Learning multi-output Classifiers and Regressors to make predictions on an unknown match by exploiting the events and results of known matches. We compare the benchmark model to a simple non-ML Classifier which randomly predicts e.g. on the winner of a match.

Amongst the mentioned Classifiers and Regressors that will be considered are the following well-known models included in scikit-learn [3]:
- Decision Trees
- Random Forests
- Gradient Descent

## 6. Evaluation Metrics

<!-- 	Student proposes at least one evaluation metric that can be used to quantify the performance of both the benchmark model and the solution model presented. The evaluation metric(s) proposed are appropriate given the context of the data, the problem statement, and the intended solution.  -->

Common classification metrics in Machine Learning (e.g., summarized in [2]) like Precision, Recall, or the F1 Score will be considered in this project, while the most important metric here will be the **Accuracy Score**, which represents the fraction of correctly classified samples, since it determines how many of the matches' results have been correctly classified.

Here, the Accuracy is calculated in a row-wise manner representing single football matches.


Accuracy is defined as the proportion of correct predictions:

$$
\text{Accuracy} = \frac{\text{number of correct predictions}}{\text{total number of predictions}}
$$

For a dataset of size $n$, this means:

$$
\text{Accuracy} = \frac{1}{n} \sum_{i=1}^{n} \mathbf{1}(\hat{y}_i = y_i)
$$

where:

- $\hat{y}_i$ = predicted label  
- $y_i$ = true label  
- $\mathbf{1}(\cdot)$ = indicator function  


## 7. Presentation

<!-- The proposal follows a well-organized structure and would be readily understood by its intended audience. Each section is written in a clear, concise and specific manner. Few grammatical and spelling mistakes are present. All resources used and referenced are properly cited. -->

The results of the project will be presented in a final report following a well-organized structure, intended to be readily understood by readers interested in the general football topic as well as the specific data analysis and Machine Learning background of the paper.

## 8. Project Design

<!-- Student summarizes a theoretical workflow for approaching a solution given the problem. A discussion is made as to what strategies may be employed, what analysis of the data might be required, or which algorithms will be considered. The workflow and discussion provided align with the qualities of the project. Small visualizations, pseudocode, or diagrams are encouraged but not required. -->

In this project, we will perform the following workflow tp approach a solution to the described problem - this represents a common approach with typical steps in Machine Learning projects:
1. **Data Preparation** *- required to make the data available with an adequate quality*
  - Downloading a subset of the StatsBomb Open Data set
  - Pre-processing and cleaning the data (if needed)
  - Uploading the data to an S3 Bucket to make it available for SageMaker training
2. **Data Exploration** *- important to gain an insight of the data*
  - Visualizing some specific details of the data to give an insgight into the data
3. **Creation of Training Script** *- standard proceeding in modern Machine Learning approaches*
  - First, reading, loading and pre-processing the StatsBomb data
  - Then, splitting the data into train, test, and validation
  - Finally, training the data with the chosen architecture
4. **Deployment of the model** *- making the results of the model training available to other users*
  - Providing a SageMaker inference endpoint to test the model with previously unregarded match data of StatsBomb

## 9. References

[1] StatsBomb Open Data: https://github.com/statsbomb/open-data
[2] Beyond Accuracy: The Ultimate Guide to Classification Metrics in Machine Learning, by Amit Kharche. https://medium.com/@amitkharche/beyond-accuracy-the-ultimate-guide-to-classification-metrics-in-machine-learning-b19b84273b7c
[3] Gradient boosting, random forests, and other Supervised Learning algorithms in skicit-learn. https://scikit-learn.org/stable/modules/ensemble.html
