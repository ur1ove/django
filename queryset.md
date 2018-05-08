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
<QuerySet [<Post: 제1회 인공지능 최근 기술 동향 강좌>, <Post: 2차 기관탐방 워크샵>, <Post: 제12회 한국정보과학회/한국빅데이터학회 공동학술 심포지엄>, <Post:
타이틀>]>
~~~
