# mckinsey_recommendation
Solution for mckinsey recommendation challenge held on analyticsvidhya (3rd rank)

Approach: 
1. Thought of it as a problem where a sequence of words used to predict the next word (like in time series) or similar words (like in market basket analysis)
2. Started with building embeddings for the challenges using gensim word2vec. 
3. The embeddings were used to find the most similar words/challenges to the last few challenges the user has attempted. 
4. This model was optimsed first. The size of embedding, iteration and window size was tuned. (Gave me a decent leaderboard score)
5. Now, I built a GRU network which predicted the next challenge given the 10 challenges a user has solved. 
6. The target variable was the list of challenges solved on 11th,12th,13th place. 
7. The train data samples were duplicated 3 times ( 1 each for 11th, 12th, 13th)
8. Sample weights were given to each sample and the samples in which target was 11th challenge, were given more importance.  
9. The word embeddings trained from word2vec were fed into the GRU. 
10. The GRU was trained for different sets of training data 
11. Predcitions were made by taking the most 3 likely samples for each user
