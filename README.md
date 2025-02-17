# Hotel Recommendation System
### By: Akshat Jain, Ryan Wong, Eunice Cho

Our project focuses on developing a hotel recommendation system using Naive Bayes. Our system will recommend hotels based on customer reviews, price, and reviewer score. We will also incorporate sentiment analysis on reviews. The goal of our model is to produce the best hotel option for the user.

Explain what your AI agent does in terms of PEAS. What is the "world" like? 

Our agent is a hotel recommendation system which aims to produce the best hotel option for the user. The performance measure will be user feedback on how they rate the hotel we recommend to them. The environment will be the device the user uses to interact with the model. The actuators are the hotels that our agent recommends to the users based on their hotel preferences and hotel reviews. The sensors will be the data we receive from users about how much they are willing to spend on a hotel as well as which type of hotel they would like to stay in.


What kind of agent is it? Goal based? Utility based? etc. 

Our agent is a goal-based agent which aims to recommend hotels that aligns with the user preferences. The agent uses probabilistic reasoning through Naive Bayes, which calculates the likelihood of a hotel being a good fit for a user based on their preferences. 

Describe how your agent is set up and where it fits in probabilistic modeling

Our agent works by analyzing the training data then creating a CPT for each feature. The CPTs are then used to calculate the likelihood of a hotel being a good fit for a user based on their preference for price and rating. The agent then recommends the hotel with the highest likelihood.

Our data
https://www.kaggle.com/datasets/maelysboudier/hotel-prices-in-europe 
https://www.kaggle.com/datasets/jiashenliu/515k-hotel-reviews-data-in-europe


Train your first model
Evaluate your model
Create/Update your README.md to include your new work and updates you have all added. Make sure to upload all code and notebooks. Provide links in your README.md
- [Notebook: Hotel Recommendation System](./worko.ipynb)

Conclusion section: What is the conclusion of your 1st model? What can be done to possibly improve it?
From our first iteration, we can see that our model has initial good fitting. As seen on the graph, our model is not over or underfit. However, we can make more improvements by taking into account the user's preferences such as size, budget, etc.
