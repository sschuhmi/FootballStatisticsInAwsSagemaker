## Proposal for Capstone Project

# Topic: "Predicting results in modern football games using Machine Learning algorithms in AWS SageMaker"

Part of Udacity's Nanodegree Program "AWS Machine Learning Engineer" (nd189) - 

## 1. Domain Background

<!-- Student briefly details background information of the domain from which the project is proposed. Historical information relevant to the project should be included. It should be clear how or why a problem in the domain can or should be solved. Related academic research should be appropriately cited. A discussion of the student's personal motivation for investigating a particular problem in the domain is encouraged but not required. -->

In modern football, data in shape of match statistics is comprehensive and vital to understand why 

## 2. Problem Statement

<!-- Student clearly describes the problem that is to be solved. The problem is well defined and has at least one relevant potential solution. Additionally, the problem is quantifiable, measurable, and replicable. -->

## 3. Solution Statement

<!-- Student clearly describes a solution to the problem. The solution is applicable to the project domain and appropriate for the dataset(s) or input(s) given. Additionally, the solution is quantifiable, measurable, and replicable. -->

## 4. Datasets and Inputs

<!-- The dataset(s) and/or input(s) to be used in the project are thoroughly described. Information such as how the dataset or input is (was) obtained, and the characteristics of the dataset or input, should be included. It should be clear how the dataset(s) or input(s) will be used in the project and whether their use is appropriate given the context of the problem. -->

In this project, we rely on the well-known StatsBomb open source dataset, which encompasses extensive statistics of thousands of played matches in different competitions like the global World Cup, continental championships such as the Copa America in South America, or club championships like the European Champions League.

The StatsBomb dataset is publicly available via GitHub [1].

## 5. Benchmark Model

<!-- A benchmark model is provided that relates to the domain, problem statement, and intended solution. Ideally, the student's benchmark model provides context for existing methods or known information in the domain and problem given, which can then be objectively compared to the student's solution. The benchmark model is clearly defined and measurable. -->

## 6. Evaluation Metrics

<!-- 	Student proposes at least one evaluation metric that can be used to quantify the performance of both the benchmark model and the solution model presented. The evaluation metric(s) proposed are appropriate given the context of the data, the problem statement, and the intended solution.  -->

Regarding analytical data in modern football, ...

## 7. Presentation

<!-- The proposal follows a well-organized structure and would be readily understood by its intended audience. Each section is written in a clear, concise and specific manner. Few grammatical and spelling mistakes are present. All resources used and referenced are properly cited. -->

## 8. Project Design

<!-- Student summarizes a theoretical workflow for approaching a solution given the problem. A discussion is made as to what strategies may be employed, what analysis of the data might be required, or which algorithms will be considered. The workflow and discussion provided align with the qualities of the project. Small visualizations, pseudocode, or diagrams are encouraged but not required. -->

In this project, we will perform the following workflow tp approach a solution to the described problem:
1. Data Preperation:
- Downloading a subset of the StatsBomb Open Data set
- Pre-processing and cleaning the data (if needed)
- Uploading the data to an S3 Bucket to make it available for SageMaker training
2. Data Exploration:
- Visualizing some specific details of the data to give an insgight into the data
3. Creation of Training Script:
- First, reading, loading and pre-processing the StatsBomb data
- Then, splitting the data into train, test, and validation
- Finally, training the data with the chosen architecture
4. Deployment of the model:
- Providing a SageMaker inference endpoint to test the model with previously unregarded match data of StatsBomb

## 9. References

[1] StatsBomb Open Data: https://github.com/statsbomb/open-data
