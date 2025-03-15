# Hotel Recommendation System

### By: Akshat Jain, Eunice Cho, Ryan Wong for CSE 150A Winter '25

### Synopsis
Our project revolves around a hotel recommendation system that is based on Naive Bayes, something we learned in this class. Our system will recommend hotels based on three main factors: customer reviews, price, and reviewer score. The end goal of this project is to provide a model that allows a user to receive a hotel recommendation that best fits their needs.

## PEAS/Agent Analysis

### Introduction
After on our research on datasets and possible project ideas, we came to this idea of a hotel recommendation system, which provides a user with a hotel recommendation. As such, we designed a hotel recommendation system that provides a recommendation based on customer reviews, price, and reviewer scores.

### Performance Measure, Environment, Actuators, Sensors (PEAS)
- **Performance Measure**: The main performance measure is how the user feels about the provided hotel recommendations, which can be meausred by how well the recommended hotel aligns with the user's preferences.
- **Environment**: The recommendation system is virtual, in a space where it can hypothetically be accessed by users on the internet.
- **Actuators**: The recommendation system outputs hotel recommendations based on the results of naive bayes model, which is first fed the inputs.
- **Sensors**: The model receives user input, being budget range, hotel preferences, and the scors of reviewers.

### Type of Agent
The agent is a **goal-based agent**, intending to provide hotel recommendations that align with user preferences. It utilizes **probabilistic reasoning through naive bayes**, which calculates the probability of a hotel being a good fit for a user, based on their preferences.

## Agent Setup, Data Preprocessing, and Training

### Dataset Exploration
- **Dataset Overview**:
  - TODO: add a disclaimer?? that our data is all from europe
  - Here are the datasets that we used, both found on Kaggle.
    - [Hotel Prices in Europe Dataset](https://www.kaggle.com/datasets/maelysboudier/hotel-prices-in-europe)
    - [515K Hotel Reviews in Europe Dataset](https://www.kaggle.com/datasets/jiashenliu/515k-hotel-reviews-data-in-europe)
  - The main data that can be found in these datasets are: 
    - hotel names
    - prices
    - reviewer scores
    - review sentiment data.
- **Important Variables**:
  - TODO: Explain variables further and also draw a picture to show the variables/to help visualise it
  - `Review_Total_Positive_Word_Counts`: the count of positive words in reviews for a given hotel
  - `Review_Total_Negative_Word_Counts`: the count of negative words in reviews for a given hotel
  - `Reviewer Score`: the score given by a reviewer, out of 10, which is divided into two categories: low score (<=7) and high score (>7)
  - `Price`: the price of the hodel, which is also divided into two categories: affordable and expensive
  - `Hotel Recommendation Score`: calculated using sentiment score and reviewer score to create a binary output: recommended or not recommended
- **Variable Interactions**:
  - sentiment analysis to place into positive/negative/neutral category is found by comparing `Review_Total_Positive_Word_Counts` and `Review_Total_Negative_Word_Counts`
  - Hotels are categorized into low/high score and also affordable/expensive
  - The naive bayes model predicts whether a hotel should be recommended based on these engineered features

<br><br>
The following image depicts how the different factors influence the main hotel recommendation:

![Bayesian Network](BN_structure.png)

### Model Selection and Structure
- **Model Choice**:
  - TODO: need more of an explanation for why this model works, and why we chose it (since the main variables were assumed to be condtionally independent)
  - We selected the **naive bayes classifier** for our model since it is good at prdicting probabilities given we have conditional independence assumptions
- **Structure Explanation**:
  - The model is uses **cpts** to calculate probabilities for features like sentiment, reviewer score (low/high), and price (affordable/expensive)

### Parameter Estimation
- TODO: need to better explain, with PHOTO/Code snippet, how we calculated the CPTs and why that is important
- **Calculating Parameters**:
  - The conditional probabilities were estimated using the **naive bayes formula**.
  - We also used **laplace smoothing** to stop any issues regarding 0 probabilities
- **Algorithms Used**:
  - We used the naive bayes algorithm for classification
  - Sentiment classification was performed by compaing the number of positive words and negative words
- **Library Usage**:
  - We used `numpy` for handling the arrays and probabilities
  - We also used `pandas` for processing the data
  - We also used `matplotlib.pyplot` for our graphs

### Training Process
- **Training Setup**:
  - Training data was preprocessed by binning price and reviewer score into categories to engineer new features
  - Conditional probabilities were then computed for each feature
  - The model was trained using older hotel reviews and tested on unseen data
- **Code Snippet or Notebook Link**:
  - TODO: [code snippet] for main training and what it means
  - TODO: link to notebook

## Conclusion and Results

### Performance Evaluation
- **Results Summary**:
  - Our bayesian network model achieved an accuracy of **93.21%** in predicting hotel recommendations (let's go!!!!!!!)
- **Visualizations**:
  - The graph below shows the relationship between model complexity and error

![Model Complexity vs. Error](accuracy.png)

### Interpretation of Results
- **Performance Analysis**:
  - Our model has a **low error rate**, indicating that it is able to successfully recommend a hotel
  - It holds a good balance between **underfitting** and **overfitting**, as shown by the plot above
- **Comparison to Baseline**:
  - A random recommendation would achieve significantly lower accuracy, validating our approach.
  - TODO: show the results of a random approach, since that would be our baseline
  - TODO: maybe even do one where a human like us guesses hotel recommendations?? would be a cool thing to add to the final submission

### Areas for Improvement
- TODO: need more detail with this step, right now we just kinda stating stuf LOL
- TODO: address that our data is from europe
- **Data Preprocessing Enhancements**:
  - Our sentiment analysis at the moment is very weak. We currently just compare the counts of positive/negative words in the reviews for a hotel. In reality, some words, positive or negative, might hold more weight than others. A potential improvement would be to use advanced NLP on the reviews, rather than using the counts of positive/negative reviews. This would however, require us to access the reviews and conduct expensive operations.
- **Training Optimization**:
  - We could add even more features regarding hotels. For example, location and season are important factors that could come into play.
- **Model Adjustments**:
  - We can change the **CPT structure** so that more user preferences can come into play. Ultimately, if this were a recommendation system we were releasing for people to use, it would be very important for there to be more user preferences. This necessarily would not improve the accuracy of our model, but it would allow the users to finepick the hotel recommendations they get.

## References
- TODO: add any other resources that we used
- [Hotel Prices in Europe Dataset](https://www.kaggle.com/datasets/maelysboudier/hotel-prices-in-europe)
- [515K Hotel Reviews in Europe Dataset](https://www.kaggle.com/datasets/jiashenliu/515k-hotel-reviews-data-in-europe)

<br>

---

<br>

# [IGNORE] Previous Milestone Submission
## Hotel Recommendation System
### By: Akshat Jain, Ryan Wong, Eunice Cho

Our project implements a hotel recommendation system using Naive Bayes. Our system will recommend hotels based on customer reviews, price, and reviewer score. The goal of our model is to produce the best hotel option for the user.


Bayesian Network:

![Bayesian Network](BN_structure.png)


## Model Accuracy & Overfitting Analysis  

Our Bayesian Network model achieved an accuracy of **93.21%** when predicting hotel recommendations based on sentiment, reviewer score, and price.  

The plot below illustrates how model complexity affects training and testing error. The green dot represents our model’s position, showing that it has low error. This means our model has a good balance between underfitting and overfitting.  


![Model Complexity vs. Error](accuracy.png)  


A well-fitting model should have a small gap between training and testing error, avoiding both high bias (underfitting) and high variance (overfitting). Our model appears to generalize well, but further tuning could help optimize performance.  


Explain what your AI agent does in terms of PEAS. What is the "world" like? 

Our agent is a hotel recommendation system which aims to produce the best hotel option for the user. The performance measure will be user feedback on how they rate the hotel we recommend to them. The environment will be the device the user uses to interact with the model. The actuators are the hotels that our agent recommends to the users based on their hotel preferences and hotel reviews. The sensors will be the data we receive from users about how much they are willing to spend on a hotel as well as which type of hotel they would like to stay in.


What kind of agent is it? Goal based? Utility based? etc. 

Our agent is a goal-based agent which aims to recommend hotels that aligns with the user preferences. The agent uses probabilistic reasoning through Naive Bayes, which calculates the likelihood of a hotel being a good fit for a user based on their preferences. 



Describe how your agent is set up and where it fits in probabilistic modeling

Our agent works by analyzing the training data then creating a CPT for each feature. The CPTs are then used to calculate the likelihood of a hotel being a good fit for a user based on their preference for price and rating. The agent then recommends the hotel with the highest likelihood.

Our hotel recommendation agent uses the Naive Bayes classifier where the conditional probabilities are calculated to represent the likelihood of a recommendation given certain features. 

We performed sentiment classification by categorizing the reviews as positive, neutral or negative baseed on the count of positive and negative words.

The sentiment of the hotel reviews was classified using the provided columns:

Review_Total_Positive_Word_Counts: Total number of positive words in the positive review.
Review_Total_Negative_Word_Counts: Total number of negative words in the negative review.

Each hotel has a positive and negative review. There is a column of the counts of positive words in the positive review and a column of the counts of negative words in the negative review. The sentiment classification is done by comparing the number of positive words and negative words against each other. If the count of positive words is more than the count of negative words then we classify it as positive. If the count of negative words is more than the count of positive words than we classify the count as negative. Finally, if the count of positive words and negative words are equal to each other, then we classify it as neutral.

Then we binned the reviewer score and price binning. The price category is in bins of affordable/expensive and the reviewer score is in bins of low/high.

Then we computed the hotel recommendation score which is computed for each hotel based on its reviewer score and sentiment. This score is used to create a binary label for whether a hotel is recommended or not.

Our agent relies on the CPT to store and calculate the probability of a hotel being recommened given the combinations the features: sentiment, reviewer score bin, price bin

We implemented laplace smoothing to ensure there are no missing probabilities in our CPT. 

The probability of our hotel being recommended is calculated based on the conditional probabilities of each feature (sentiment, reviewer score, price) given the recommendation label

Our agent uses the conditional probabilites to infer the likehood of a recommendation for a given hotel. It chooses the probability of a hotel being recommneded (1) or not recommended (0) and then it picks the higher probability from the model's output.


There are two ways the user can interact with the model

The first way is by providing a hotel name and the agent will say whether the hotel is recommended or not

The second way is by finding the best hotel based on price preference and inputting t he minimum reviewer score which then returns a list of top recommended hotels based on the stored probabilities




Our agent works by analyzing the training data then creating a CPT for each feature. The CPTs are then used to calculate the likelihood of a hotel being a good fit for a user based on their preference for price and rating. The agent then recommends the hotel with the highest likelihood.

Our data
https://www.kaggle.com/datasets/maelysboudier/hotel-prices-in-europe 
https://www.kaggle.com/datasets/jiashenliu/515k-hotel-reviews-data-in-europe


Conclusion

From our first iteration, we can see that our model has initial good fitting. As seen on the graph, our model is not over or underfit. However, we can make more improvements by taking into account the user's preferences such as size, budget range, etc.

Our model achieved an accuracy of 93.21% which means our hotel recommendation system is performing well. There is room to improve in our model by incorporating more features that the user will consider such as including time of year to consider the season and by incorporating hotel amenities. 

To further enhance our model, we plan on implementing more advanced techniques such as modifying our CPT with additional features and improving user interaction for greater usability.  
