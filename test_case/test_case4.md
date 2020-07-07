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
        tweet_obj = Tweet.objects.create(content="my tweet", user=self.user)
        self.assertEqual(tweet_obj.id, 1)
        self.assertEqual(tweet_obj.user, self.user)
```

---

```shell
Creating test database for alias 'default'...
System check identified no issues (0 silenced).
.
----------------------------------------------------------------------
Ran 1 test in 0.315s

OK
Destroying test database for alias 'default'...
```