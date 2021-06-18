---
layout: post
title: Get tweets from a user
excerpt_separator:  <!--more-->
tags:
  - Discord
  - Twitter

---

This guide is about using Python and the Twitter API to get the latest tweets from a user on twitter

## Setup a Twitter Developer Account

To setup a Twitter Developer Account, we first need a regular user Account.
- head to [twitter](twitter.com) and register your Account

Once we have a User Account, we can setup the Developer Account
- [register](https://developer.twitter.com/en/apply-for-access) a Developer Account

After both are setup we need to create a new App under the Projects & Apps tab on the left side.
It's important to create the Project, and then assign the App to that Project.

Creating the App allows us to get access to an API Key, which we can then use to make API calls to the Twitter Endpoints to retrieve the data.

### Setup authentication with Python

To handle our API calls to Twitters Endpoint we need to import `tweepy`

```python
# import the tweepy package
import tweepy
```

To allow `tweepy` to authenticate us we need to provide it with the API Key, API Secret, Access Token and Access Token Secret. I created an extra file `keys.py` to store those information and import them easily.

```python
# Import keys and tokens from key.py
from keys import twitter_api_key, twitter_api_secret, twitter_access_token, twitter_access_token_secret

# Setup tweepy authentication
auth = tweepy.OAuthHandler(twitter_api_key, twitter_api_secret)
auth.set_access_token(twitter_access_token, twitter_access_token_secret)

# Initialize tweepy api
api = tweepy.API(auth, wait_on_rate_limit=True, wait_on_rate_limit_notify=True)
```

### Calling the API

Creating a function and passing the name of the User we want to get Tweets from.
For easier readability I also created a constant for the Twitter URL

```python
# Assign url constant
TWITTER_URL = "https://twitter.com"
```

```python
# Function to get tweets
def get_tweets(user_name):

  # Calling api.get_user(user) to get the users information
  user = api.get_user(t_user)

  # Searching the json for the 'id' that matches the Users name
  user_id = user._json["id"]

  # Get latest tweets of user with specified ID
  latest_tweets = api.user_timeline(user_id=user_id,
                                    count=1,
                                    exclude_replies="true",
                                    include_trs="true")

# Call the get_tweets function and provide an username as parameter
get_tweets('elonmusk')
```

`count` - specifies the amount of tweets, starting with the newest

To get the actual Text message of the latest Tweet we can access the `text` keyword in the json:

```python
# Loop through the latest_tweets
for tweet in latest_tweets:
  # Filter out the values where the key matches 'text'
  tweet_text = tweet._json['text']

# Print the value of the tweet
print(tweet_text)
```

For further information check the official [Tweepy documentation](https://docs.tweepy.org/en/latest/api.html#tweepy.API.user_timeline)
