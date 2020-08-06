```shell
>>> from django.contrib.auth import get_user_model

>>> User = get_user_model()

>>> j = User.objects.first()

>>> j
<User: ankiwoong>

>>> j.tweets.all()
Traceback (most recent call last):
  File "<console>", line 1, in <module>
Traceback (most recent call last):
  File "<console>", line 1, in <module>
AttributeError: 'User' object has no attribute 'tweet'  

>>> j.tweet_set.all()
<QuerySet [<Tweet: hello world>, <Tweet: sfa>, <Tweet: None>, <Tweet: None>, <Tweet: test>, <Tweet: eheheheh>, <Tweet: None>, <Tweet: None>, <Tweet: None>, <Tweet: hi>, <Tweet: None>, <Tweet: hi>, <Tweet: None>, <Tweet: hehello>, <Tweet: None>, <Tweet: None>, <Tweet: hello>, <Tweet: hay man>, <Tweet: hi there>, <Tweet: let'go>, '...(remaining elements truncated)...']>'

>>> from django.contrib.auth import get_user_model

>>> User = get_user_model()

>>> j = User.objects.first()

>>> j.tweets.all()
<QuerySet [<Tweet: hello world>, <Tweet: sfa>, <Tweet: None>, <Tweet: None>, <Tweet: test>, <Tweet: eheheheh>, <Tweet: None>, <Tweet: None>, <Tweet: None>, <Tweet: hi>, <Tweet: None>, <Tweet: hi>, <Tweet: None>, <Tweet: hehello>, <Tweet: None>, <Tweet: None>, <Tweet: hello>, <Tweet: hay man>, <Tweet: hi there>, <Tweet: let'go>, '...(remaining elements truncated)...']>'

>>> j.tweetlike_set.all()
<QuerySet [<TweetLike: TweetLike object (6)>, <TweetLike: TweetLike object (7)>, <TweetLike: TweetLike object (18)>, <TweetLike: TweetLike object (20)>, <TweetLike: TweetLike object (21)>]>

>>> my_likes = [x.tweet for x in j.tweetlike_set.all()]

>>> my_likes
[<Tweet: Hay man>, <Tweet: hello>, <Tweet: hi>, <Tweet: 
None>, <Tweet: None>]
5

>>> j.tweets.count()
64

>>> j.tweet_user.all()
<QuerySet [<Tweet: None>, <Tweet: hi>, <Tweet: None>, <T: hi>, <Tweet: None>, <Tweet: hello>, <Tweet: Hay man>]>        

>>> len(j.tweet_user.all())     
5

>>> j.tweet_user.count()        
5
```