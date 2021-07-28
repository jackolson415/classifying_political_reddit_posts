# Using NLP to Flag Political Reddit Posts

Reddit.com is a aggregation website for a wide variety of forums, called subreddits. One of the most popular aspects of Reddit is its upvote/downvote system. This voting system allows the community to self-moderate, but only to a certain extent. As Reddit has grown in popularity and size over the years the need for dedicated moderation has grown.

For Reddit moderators to effectively work they use a variety of tools. This project is to make another tool for them: a flagging system that identifies posts that are political.

**The goal of this project is to make a model that accurately flags AskReddit posts that are poltical in nature.** To do this I will use NLP to classify posts into either AskReddit or Poltics. If a post on AskReddit is identifed as belonging in Politics it would be flagged and sent to the moderator.

## Modeling Results

|                                          | Training Score | Testing Score | Posts/3000 Flagged | Correct Flag Rate |
|------------------------------------------|----------------|---------------|--------------------|-------------------|
| 1. Count Vectorizer, Naive Bayes         | .9746          | .9556         | 29                  | 31.0%             |
| 2. TFIDF Vectorizer, Naive Bayes         | .9743          | .9545         | 26                  | 30.7%              |
| 3. Count Vectorizer, Logistic Regression | .9886          | .9530         | 75                 | 20.0%              |

- The first model has the highest correct flag rate at 31.0%. Nine of the 29 flagged posts was actually political. The first model also has the highest testing score. About 95.5% of the posts in the testing set were correctly classified into the subreddit where they were posted
- The third model is the only one to use Logistic Regression. This resulted in more posts getting flagged. The correct flag rate was lower than model #1 at 20.0%. Depending on how fast flagged posts could be handled it might be best to use model #3 since it flags the most posts, despite it's lower testing score and lower correct flag rate.

## Conclusion

In this project I set out to identify and flag for removal AskReddit posts that are political in nature. Therefore the success of these models is measured by what percentage of flagged AskReddit posts are political.

- Successes:
  - High testing scores, meaning the models were good at predicting where a post originated
  
  
  
- Areas for improvement:
  - Read through the entire AskReddit dataset to find the number that are truly political. That would allow analysis of how many polical AskReddit posts were "missed"
  - Only perform analysis on posts with 50+ upvotes. That would reduce the "noise" in the dataset and ensure we are only worrying about posts that are likely to get visiibility

In conclusion, these models were effective at classifying posts to the subreddit where they were posted. But to use them as a moderation tool we would want to increase the correct flag rate.

