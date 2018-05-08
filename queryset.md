C:\django_src>python manage.py shell
~~~
Python 3.6.4 (v3.6.4:d48eceb, Dec 19 2017, 06:54:40) [MSC v.1900 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> Post.objects.all()
Traceback (most recent call last):
  File "<console>", line 1, in <module>
NameError: name 'Post' is not defined
>>> from blog.models import Post
>>> Post.objects.all()
<QuerySet [<Post: 제1회 인공지능 최근 기술 동향 강좌>, <Post: 2차 기관탐방 워크샵>, <Post: 제12회 한국정보과학회/한국빅데이터학회 공동학술 심포지엄>]>
>>> from django.contrib.auth.models import User
>>> me = User.objects.get(username='admin')
>>> me
<User: admin>
>>> Post.objects.create(author=me, title='타이틀', text='히히')
<Post: 타이틀>
>>> Post.objects.all()
<QuerySet [<Post: 제1회 인공지능 최근 기술 동향 강좌>, <Post: 2차 기관탐방 워크샵>, <Post: 제12회 한국정보과학회/한국빅데이터학회 공동학술 심포지엄>, <Post:타이틀>]>
>>> Post.objects.filter(title__contains='회')
<QuerySet [<Post: 제1회 인공지능 최근 기술 동향 강좌>, <Post: 제12회 한국정보과학회/한국빅데이터학회 공동학술 심포지엄>, <Post: 제12회 한국정보과학회/한국빅데이터학회 공동학술 심포지엄>]>
~~~
C:\django_src>python manage.py shell
~~~
Python 3.6.4 (v3.6.4:d48eceb, Dec 19 2017, 06:54:40) [MSC v.1900 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> from blog.models import Post
>>> mypost = Post.objects.get(title='타이틀')
>>> mypost
<Post: 타이틀>
>>> mypost = Post.objects.get(title=' 타이틀')
Traceback (most recent call last):
  File "<console>", line 1, in <module>
  File "C:\Program Files\Python36\lib\site-packages\django\db\models\manager.py", line 85, in manager_method
    return getattr(self.get_queryset(), name)(*args, **kwargs)
  File "C:\Program Files\Python36\lib\site-packages\django\db\models\query.py", line 380, in get
    self.model._meta.object_name
blog.models.DoesNotExist: Post matching query does not exist.
>>> Post.objects.get_object_or_404(title=' 타이틀')
Traceback (most recent call last):
  File "<console>", line 1, in <module>
AttributeError: 'Manager' object has no attribute 'get_object_or_404'
>>> mypost.publish()
>>> Post.objects.filter(published_date__lte=timezone.now())
Traceback (most recent call last):
  File "<console>", line 1, in <module>
NameError: name 'timezone' is not defined
>>> from django.utils import timezone
>>> Post.objects.filter(published_date__lte=timezone.now())
<QuerySet [<Post: 타이틀>]>
>>>

~~~
