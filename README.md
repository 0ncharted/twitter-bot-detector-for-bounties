# Twitter Spam/Sybil Detector for Bounty Platforms

[![Stars](https://img.shields.io/github/stars/0ncharted/twitter-bot-detector-for-bounties)](https://github.com/0ncharted/twitter-bot-detector-for-bounties)

## Problem Definition
Twitter spam accounts (Sybils/bots) use repetitive tweets/generic replies (high no_tweets, low followers) to farm engagement—analog to automated bounty submissions/reward-farming on Pond. Detects manipulation for platform trust.

Pond Profile: https://cryptopond.xyz/developer/fd4bb0a3-6b5f-11f0-a1f3-024775222cc3

## Dataset
- [twitter_spam_dataset.csv](data/twitter_spam_dataset.csv): 2000 real Twitter accounts (balanced spam).
- Schema: [schema.md](data/schema.md) (no_digits for username numbers, no_tweets for repetitive spam).
- Sources: Public UCI/Kaggle Twitter spam collection (behavior-labeled).
- License: CC0; repo MIT.

## Method
- Features: Account age, tweets/followers (src/detector.py—high activity/low authenticity = fake).
- Model: Random Forest (80/20 split, balanced—replicates paper/repo).
- Run: `pip install -r requirements.txt && python src/detector.py`.

## Findings & Evaluation
- Pond Tailoring: let's take into account the pond website and bouty system, the pond platform requires users to connect their twitter to their account which makes this method even more tailored to the pond bounty program and pond website as a whole because now the details used in this ML can be replicated precisely and help greatly in finding bots and spams, by lookinng at number of tweets which is key for spotting farming patterns, we took it a step further applyiung username digits + tweet frequency for generic reply spam,
  because another common factor among spam accounts is ususaly unsuaual amount of digits in the username of the accounts usually created i bulk an uncharastic quality of human behavior who would prefer to modify or change letters to arrive at a unique name devoid of numbers while the comment also usually remains generic and repetitive and usually lacking in context as can be found even in the pond website in the comment section of the "Discussion" channel of each Model-Factory competition
  let's take exact examples that can be found as we speak on the pond website, take this comment sectio i the discusiom: https://cryptopond.xyz/modelfactory/detail/2564617?tab=4&topicId=10956423
  <image-card alt="spam example" src="spam.png" ></image-card>
  
- F1=0.86 (macro avg precision 0.87, recall 0.86; weighted 0.86)—strong balance on imbalanced real data. Confusion matrix: [[181 19] [35 165]] (86% overall accuracy, 82% recall on spam—catches most Sybils, only 19 false positives on genuine).
- Key Insights: Top feature no_tweets (0.19 importance)—high tweet volume flags repetitive spam/farming (e.g., bots blasting generic replies for rewards). no_follower (0.15 imp) spots low-follower fakes (isolated Sybils). no_hashtag (0.12 imp) detects generic replies (low hashtags = context-less comments). no_digits (0.07 imp) highlights username numbers (bulk-created bots like "user12345" vs human creativity). These drove 0.90 precision on spam (low false alarms) and 0.82 recall (spots 82% fakes).
  <image-card alt="Feature Importances" src="features.png" ></image-card>
  
- Robust: 0.86 F1 on real Twitter data; generalizes to bounty farming (low followers = fake subs, high tweets = automated entries).

- Innovation: Username digits + tweet frequency for generic reply spam (generalizes to bounty Sybils).

## Usage
1. Clone repo.
2. `pip install -r requirements.txt`
3. `python src/detector.py` – Prints report, saves model.
4. Predict: Load model, feed new profiles.

## License
MIT!

Pond Bot Bounty: Real Twitter data for spam/fake prevention (86% F1 utility).
