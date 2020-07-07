```python
from django.contrib.auth import get_user_model
from django.test import TestCase

from .models import Tweet

# Create your tests here.
User = get_user_model()


class TweetTestCase(TestCase):
    def setUp(self):
        self.user = User.objects.create_user(username="cfe", password="somepassword")

    def test_tweet_created(self):
        tweet = Tweet.objects.create(content="my tweet", user=self.user)
        self.assertEqual(tweet.id, 1)
        self.assertEqual(tweet.obj.user, self.user)
```

---

```shell
Creating test database for alias 'default'...
System check identified no issues (0 silenced).
E
======================================================================
ERROR: test_tweet_created (tweets.tests.TweetTestCase)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "D:\Code\Study\DJANGO_Tweetme_2\tweets\tests.py", line 19, in test_tweet_created
    self.assertEqual(tweet.obj.user, self.user)
AttributeError: 'Tweet' object has no attribute 'obj'

----------------------------------------------------------------------
Ran 1 test in 0.317s

FAILED (errors=1)
Destroying test database for alias 'default'...
```