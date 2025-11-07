
# Dataset Schema (Twitter Spam/Sybil Detection)

| Column              | Type | Description                          | Example |
|---------------------|------|--------------------------------------|---------|
| accout_age          | int  | Account age (low = new Sybil)        | 1860    |
| no_follower         | int  | Followers (low = fake)               | 591     |
| no_following        | int  | Following (high = spam farming)      | 562     |
| no_userfavorites    | int  | Favorites (low = bot)                | 1256    |
| no_lists            | int  | Lists (low = isolated Sybil)         | 0       |
| no_tweets           | int  | Tweets (high = repetitive spam)      | 5441    |
| no_retweets         | int  | Retweets (high = farming)            | 0       |
| no_tweetfavourites  | int  | Tweet favorites (low = generic)      | 0       |
| no_hashtag          | int  | Hashtags (low = generic replies)     | 0       |
| no_usermention      | int  | Mentions (high = spam)               | 0       |
| no_urls             | int  | URLs (high = phishing)               | 1       |
| no_char             | int  | Characters (short = generic)         | 38      |
| no_digits           | int  | Digits (high = username numbers)     | 0       |
| label               | int  | 0=genuine, 1=spam/Sybil              | 0       |

- Size: 2000 rows (balanced)
- Source: Public Twitter spam collection (UCI/Kaggle variant)
- Labeling: Behavior-based (high tweets/low followers = spam)
- License: CC0 (public domain)
