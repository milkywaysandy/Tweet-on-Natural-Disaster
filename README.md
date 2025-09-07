# Tweet-on-Natural-Disaster
NLP Project with Bidirectional LSTM  
Project Goal
The primary goal of this project is to build deep learning models to accurately classify tweets as either related to a real disaster or not. Using social media data, particularly from X (formally Twitter),  for real-time communication during emergencies, making an automated classification system valuable for organizations like disaster relief agencies and news outlets.

Dataset
The dataset used for this project is sourced from a Kaggle competition (NLP Getting Started). It contains tweets that have been classified with a binary label indicating whether they are about actual disasters.

Training Set Shape: (7613, 5)
Test Set Shape: (3263, 4)

Methodology
The project involved the following steps:

Data Loading and Exploration: The training and test datasets were loaded and basic exploratory data analysis, including examining tweet lengths, was performed.

Data Preparation:
Text data was processed using Keras's TextVectorization layer to handle tokenization and padding of tweet sequences to a fixed length (SEQUENCE_LENGTH = 160). Basic standardization (lowercase and punctuation removal) was included in this step. (An attempt at more comprehensive text cleaning was made but found to be too slow).

Model Building:
A Basic SimpleRNN Model was built, consisting of an Embedding layer, a SimpleRNN layer, and a Dense output layer.
A Bidirectional LSTM Model was built as an improved architecture, consisting of an Embedding layer, a Bidirectional layer wrapping an LSTM layer, and a Dense output layer.
Model Training: Both the SimpleRNN and Bidirectional LSTM models were compiled and trained on the prepared training data, with performance monitored on a validation set.
Model Evaluation: The performance of both models was evaluated on the validation set using metrics such as Accuracy, Precision, Recall, and F1 Score. Confusion matrices were generated to visualize the classification results.

Results and Analysis
The evaluation revealed significant performance differences between the two models:

Model	Accuracy	Precision	Recall	F1 Score
SimpleRNN	0.5739	0.0000	0.0000	0.0000
Bidirectional LSTM	0.8638	0.7935	0.7103	0.7496
The SimpleRNN model performed very poorly, essentially classifying all tweets as non-disasters. Its metrics (Precision, Recall, F1 Score of 0 for class 1) indicate a complete failure to identify positive cases.

The Bidirectional LSTM model, however, showed substantially better results, achieving an accuracy of nearly 80% and respectable Precision, Recall, and F1 Scores. This indicates that the Bidirectional LSTM was much more effective at distinguishing between disaster and non-disaster tweets.

The superior performance of the Bidirectional LSTM is likely due to its ability to:

Capture long-term dependencies in sequences more effectively than SimpleRNNs.
Utilize bidirectional context by processing the text from both directions, providing a richer understanding of the tweet's meaning.

How to Run
Clone the repository.
Open the .py in a Jupyter environment.
Ensure necessary libraries (pandas, numpy, tensorflow, keras_nlp, sklearn, seaborn, matplotlib, nltk, contractions, tqdm) are installed.
Run the cells sequentially to execute the data loading, preprocessing, model training, evaluation, and submission file generation steps.
