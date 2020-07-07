```python
from django.contrib.auth import get_user_model
from django.test import TestCase

from rest_framework.test import APIClient

from .models import Tweet

# Create your tests here.
User = get_user_model()


class TweetTestCase(TestCase):
    def setUp(self):
        self.user = User.objects.create_user(username="cfe", password="somepassword")
        Tweet.objects.create(content="my first tweet", user=self.user)

    def test_tweet_created(self):
        tweet_obj = Tweet.objects.create(content="my second tweet", user=self.user)
        self.assertEqual(tweet_obj.id, 2)
        self.assertEqual(tweet_obj.user, self.user)

    def get_client(self):
        client = APIClient()
        client.login(username=self.user.username, password="somepassword")
        return client

    def test_tweet_list(self):
        client = self.get_client()
        response = client.get("/api/tweets/")
        self.assertEqual(response.status_code, 200)
        print(response.json())
```

---

```shell
Creating test database for alias 'default'...
System check identified no issues (0 silenced).
.[{'id': 1, 'content': 'my first tweet', 'likes': 0, 'is_retweet': False, 'parent': None}]
.
----------------------------------------------------------------------
Ran 2 tests in 1.005s

OK
Destroying test database for alias 'default'...
```