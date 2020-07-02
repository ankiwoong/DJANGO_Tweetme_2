```shell
>>> from tweets.models import Tweet, TweetLike

>>> TweetLike.objects.all()
<QuerySet []>

>>> TweetLike.objects.all()
<QuerySet [<TweetLike: TweetLike object (1)>, <TweetLike: TweetLike object (2)>]>

>>> TweetLike.objects.all().delete()
(2, {'tweets.TweetLike': 2})

>>> TweetLike.objects.all()
<QuerySet []>

>>> Tweet.objects.all()
<QuerySet [<Tweet: Tweet object (10)>, <Tweet: Tweet object (9)>, <Tweet: Tweet object (8)>, <Tweet: Tweet object (7)>, <Tweet: Tweet object (6)>, <Tweet: Tweet object (5)>, <Tweet: Tweet object (4)>, <Tweet: Tweet object (3)>, <Tweet: Tweet object (2)>, <Tweet: Tweet object (1)>]>

>>> obj = Tweet.objects.first()

>>> obj.likes.all()
<QuerySet []>

>>> from django.contrib.auth import get_user_model

>>> User = get_user_model()

>>> User.objects.all()
<QuerySet [<User: ankiwoong>]>

>>> me = User.objects.first()

>>> me
<User: ankiwoong>

>>> obj.likes.add(me)

>>> obj.likes.all()
<QuerySet [<User: ankiwoong>]>

>>> obj.likes.remove(me)

>>> obj.likes.remove(me)

>>> obj.likes.remove(me)

>>> obj.likes.remove(me)

>>> obj.likes.all()
<QuerySet []>

>>> qs = User.objects.all()

>>> obj.likes.set(qs)

>>> obj.likes.all()
<QuerySet [<User: ankiwoong>]>

>>> TweetLike.objects.all()
<QuerySet [<TweetLike: TweetLike object (4)>]>

>>> TweetLike.objects.first().timestamp
datetime.datetime(2020, 7, 2, 22, 51, 5, 912276, tzinfo=<UTC>)

>>> obj.likes.remove(me)

>>> obj.likes.all()
<QuerySet []>

>>> TweetLike.objects.create(user=me, tweet=obj)
<TweetLike: TweetLike object (5)>

>>> obj.likes.all()
<QuerySet [<User: ankiwoong>]>

>>> obj.likes.add()

>>> obj.likes.remove()

>>> obj.likes.set()     # requires a queryset
Traceback (most recent call last):
  File "<console>", line 1, in <module>
TypeError: set() missing 1 required positional argument: 'objs'

>>> TweetLike.objects(user=, tweet=)
  File "<console>", line 1
    TweetLike.objects(user=, tweet=)
                           ^
SyntaxError: invalid syntax

>>> obj.likes.add(me)

>>> obj.likes.all()
<QuerySet [<User: ankiwoong>]>

>>> empty_users = User.objects.none()

>>> empty_users
<QuerySet []>

>>> obj.likes.set(empty_users)

>>> obj.likes.all()
<QuerySet []>
```