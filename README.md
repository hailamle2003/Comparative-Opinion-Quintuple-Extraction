# Task Description
The rapid growth of online shopping and e-commerce platforms has led to an explosion of product reviews. These reviews often contain valuable information about users’ opinions on various aspects of the products, including comparisons between different devices. Understanding comparative opinions from product reviews is crucial for manufacturers and consumers alike. Manufacturers can gain insights into the strengths and weaknesses of their products compared to competitors, while consumers can make more informed purchasing decisions based on these comparative insights. To facilitate this process, we propose the “ComOM - Comparative Opinion Mining from Vietnamese Product Reviews” shared task.

The goal of this shared task is to develop natural language processing models that can extract comparative opinions from product reviews. Each review contains comparative sentences expressing opinions on different aspects, comparing them in various ways. Participants are required to develop models that can extract the following information, referred to as a “quintuple,” from comparative sentences:

Subject: The entity that is the subject of the comparison (e.g., a particular product model).
Object: The entity being compared to the subject (e.g., another model or a general reference).
Aspect: The word or phrase about the feature or attribute of the subject and object that is being compared (e.g., battery life, camera quality, performance).
Predicate: The comparative word or phrase expressing the comparison (e.g., “better than,” “worse than,” “equal to”).
Comparison Type Label: This label indicates the type of comparison made and can be one of the following categories: ranked comparison (e.g., “better”, “worse”), superlative comparison (e.g., “best”, “worst”), equal comparison (e.g., “same as,” “as good as”), and non-gradable comparison (e.g., “different from,” “unlike”). Data
Participants will be provided with a labeled dataset consisting of product reviews in Vietnamese. Each review will contain comparative sentences, and the associated quintuples will be annotated. The dataset will be split into training, development, and test sets. The training set can be used to train models, while the development set can be used for fine-tuning and hyperparameter tuning (the public leaderboard will be reported on this dataset for reference). The final evaluation will be performed on the test set, which contains unseen data.

# Evaluation Methodology
For the Comparative Element Extraction, the following evaluation metrics will be used: Precision, Recall, and F1 score for each individual element (subject, object, aspect, predicate, and comparison type label), as well as their Micro-average F1 score.

For the final evaluation, the complete quintuple will be considered, and the following evaluation metrics will be calculated: Precision, Recall, and F1 score for the entire quintuple.

Three matching strategies will be used to measure correct predictions:

Exact Match: The entire extracted quintuple component must match exactly with the ground truth.
Proportional Match: The proportion of matched words in the extracted component with respect to the ground truth will be considered.
Binary Match: At least one word in the extracted component must overlap with the ground truth.
Participants will be ranked based on their models’ performance using these evaluation metrics on the test set. The best-performing system will be determined by the highest F1 score for the Comparative Element Extraction and the whole quintuple extraction.
# Model Description
Model has 2 stage
Comparative Sentence Recognition: Using PhoBert Encoder to learn embedding then put it into fully-connected and logistic regression to extract probability.
Extract Comparative Opinion: Fine tuning T5 model to extract comparative opinions from product reviews
