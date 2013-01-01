---
layout: post
tags: python flask
title: Setup Flask with virtualenv
---
Install virtualenv
{% highlight bash %}
aptitude install python-virtualenv
{% endhighlight %}

Create virtual env
{% highlight bash %}
virtualenv flask_env
{% endhighlight %}

Activate virtual env
{% highlight bash %}
source flask_env/bin/activate
{% endhighlight %}

Install flask
{% highlight bash %}
pip install flask
{% endhighlight %}

To test, create a file called hello.py (Copied from <http://flask.pocoo.org/>)
{% highlight python %}
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"

if __name__ == "__main__":
    app.run()
{% endhighlight %}

Run
{% highlight bash %}
python hello.py
{% endhighlight %}

Deactivate virtualenv
{% highlight bash %}
deactivate
{% endhighlight %}


