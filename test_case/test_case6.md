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

    def test_tweet_created(self):
        tweet_obj = Tweet.objects.create(content="my tweet", user=self.user)
        self.assertEqual(tweet_obj.id, 1)
        self.assertEqual(tweet_obj.user, self.user)

    def get_client(self):
        client = APIClient()
        client.login(username=self.user.username, password="somepassword")
        return client

    def test_tweet_list(self):
        client = self.get_client()
        response = client.get("/api/tweets/")
        print(response)
```

---

```shell
Creating test database for alias 'default'...
System check identified no issues (0 silenced).
.<Response status_code=200, "application/json">
.
----------------------------------------------------------------------
Ran 2 tests in 1.040s

OK
Destroying test database for alias 'default'...
```