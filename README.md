# Sinhala-English Language Identifier
Concurrent programming with semaphores

# About Project
The objective of the project is to identify the language of the word entered to the application based charactor sequence of the language words.

# Methodology 

## 1 Data Preparation

First, we extract a Sinhala dataset and an English dataset from the Wikipedia articles using the Python Wikipedia library. We used the character sequence properties as the main feature of this model. We convert Sinhala words to Singlish words  (Unidecode) before train the model in order to make a common feature for both Sinhala and English language. 

## 2 Data Preprocessing

First, we tokenize each word of the article from the white spaces. Then we convert each Sinhala word into English words (Unidecode). 
(Example: අම්මා => amma, බල්ලා => ballaa)

Then we created one-hot vectors for each of the characters for a particular word and then combined then and created a multi-hot vector with length 312 (26*max_word_length). That vector represents the character properties for a particular word. When creating vectors, we only considered words, which have a maximum size of 12. Otherwise, the vector length gets much longer.

## 3 Model Training

After we have done all the preprocessing required to train the model, we have divided our data set into training and test data sets(x_train,x_test) as 85% of the dataset is training data and 15% of the data is test data. In this language classifier for Sinhala & English languages, we used a supervised learning approach with Keras 5-layer neural network model. Every hidden layer in the neural network used ‘sigmoid’ function as the activation function. Also, we used MSE(Mean Squared Error) as the error calculating approach and 50 epochs for our model training. 
After we trained our model we have saved model weights into a file called “weights.hdf5” for further usage(In our FYP). 
In the model training process, we have used the approximately equal size of datasets for both the English and Sinhala languages for avoiding the model bias.

## 4 Summary and Results

After testing the model with a test data set, we observed the following accuracy and error from the neural network model.

				#### Accuracy: 92.97% (for 50 epochs)
				#### Mean Squared Error (MSE): 0.0652

Here we only used 13 Wikipedia articles for both Sinhala and English languages. Those articles have similar content. If we use more articles and train the model with larger epochs we can increase the accuracy of this neural network model.
