```python
from django.test import TestCase

# Create your tests here.
from django.contrib.auth import get_user, get_user_model
from .models import Profile


User = get_user_model()


class ProfileTestCase(TestCase):
    def setUp(self):
        self.user = User.objects.create_user(username="cfe", password="somepassword")
        self.userb = User.objects.create_user(
            username="cfe-2", password="somepassword2"
        )

    def test_profile_created_via_signal(self):
        qs = Profile.objects.all()
        self.assertEqual(qs.count(), 2)

    def test_following(self):
        first = self.user
        second = self.userb
        first.profile.followers.add(second)
        qs = second.following.filter(user=first)
        self.assertTrue(qs.exists())
```

---

```shell
Creating test database for alias 'default'...
System check identified no issues (0 silenced).
..
----------------------------------------------------------------------
Ran 2 tests in 1.384s

OK
Destroying test database for alias 'default'...
```