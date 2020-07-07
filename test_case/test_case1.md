```python
from django.contrib.auth import get_user_model
from django.test import TestCase

from .models import Tweet

# Create your tests here.
User = get_user_model()


class TweetTestCase(TestCase):
    def setUp(self):
        User.objects.create_user(username="abc", password="somepassword")
        User.objects.create_user(username="cfe", password="somepassword")

    def test_user_created(self):
        user = User.objects.get(username="cfe")
        self.assertEqual(user.username, "cfe")
```

---

```shell
Creating test database for alias 'default'...
System check identified no issues (0 silenced).
.
----------------------------------------------------------------------
Ran 1 test in 0.606s

OK
Destroying test database for alias 'default'...
```