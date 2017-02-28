# Python-project
import tweepy
from tweepy import OAuthHandler
import os

consumer_key = 'BbLi4xrg5DyVhrXixL4IHhOXN'
consumer_secret = 'mmO3DG6jdMrFY0nwpYvtZZkG7vI5nIqDSlDNr6nUFtjS0qzqi1'
access_token = '2574978056-0fhfgc3upQlVt4LjLPp10xuKywtwhGFOca7d5BD'
access_secret = 's5AneiEbyivRcP3LivzEqxloJM1HjnOmUYEx7TzCxHdfp'
auth = OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_secret)
api = tweepy.API(auth)

accountvar = raw_input("First account name: ")

ids = []
for page in tweepy.Cursor(api.followers_ids, screen_name=accountvar).pages():
     ids.extend(page)

users = api.lookup_users(user_ids=ids)
for u in users:
     print u.screen_name

accountvar2 = raw_input("Second account name: ")

ids2 = []
for page in tweepy.Cursor(api.followers_ids, screen_name=accountvar2).pages():
     ids2.extend(page)

users2 = api.lookup_users(user_ids=ids2)
for u in users2:
     print u.screen_name

c=[]
for u in users:
    for y in users2:
        if u.screen_name==y.screen_name:
            c.append(u)

print '\ncommon followers:\n'
for u in c:
    print u.screen_name


if len(c)==0:
    print '0 common followers'
