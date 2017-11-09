---
layout: post
title:  "A Little Programming"
date: Tue Nov 7 21:52:15 EST 2017
categories: django api websockets channels asgi
---

My most excellent friends over at <a href="https://workhaus.ca/" target="_blank">Workhaus</a>
needed some help with their network tonight after a long day of AWS at work.  I popped by
hoping it would be a quick fix so I could Uber right home and drill some holes before it got too late (I've other neighbours attached to my dwelling).

... It got too late, not to mention stressful - So I visited a local pub for a beer and decided since I'm doing less than nothing
I should probably put together the boilerplate API and worker code.

Requirements :
* Realtime functionality
* Maintainable and simple
* Relaible, tested and ubiquitous
* Extensible and open
* Light enough to run on a Pi, powerful enough to grow peppers :)

Thus, I went with (what I know) the following :
* <a href="https://www.djangoproject.com/" target="_blank">Django</a>
* <a href="http://www.django-rest-framework.org/" target="_blank">Django Rest Framework</a>
* <a href="https://channels.readthedocs.io/en/stable/" target="_blank">Channels</a>
* <a href="https://pypi.python.org/pypi/RPi.GPIO" target="_blank">RPi.GPIO</a>

Django channels is the coolest thing to happen to Django since Django REST Framework.
With channels I'll be able to push notifications from sensors to the DB reliably supporting
two-way data-binding - this means whether the app lives on the Pi or in the cloud I
can view my metrics knowing they are safely stored on disk.

The boilerplate code is available (pardon the empty readme) <a href="https://github.com/chlorobot/chlorobot-app" target="_blank">here</a>

I will update (with pics) when the fans arrive and are installed, hopefully tomorrow!
