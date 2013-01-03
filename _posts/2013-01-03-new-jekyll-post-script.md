---
layout: post
tags: jekyll
title:
published: false
---
Add environment variable to ~/.bashrc
{% highlight bash %}
export POST_ROOT=$HOME/zamemo.github.com/_post
{% endhighlight %}

Create a bin directory in home
{% highlight bash %}
mkdir ~/bin
{% endhighlight %}

Add to PATH in ~/.bashrc
{% highlight bash %}
export PATH=$PATH:$HOME/bin
{% endhighlight %}

Reload environment variables
{% highlight bash %}
source ~/.bashrc
{% endhighlight %}

create a new file in ~/bin
{% highlight bash %}
cat << "EOF" > ~/bin/np
#!/usr/bin/env sh

FILENAME=$(echo $@ | sed -e "s/ /-/g")
TODAY=$(date +%F)
FILENAME="$TODAY-$FILENAME.md"

cp $POST_ROOT/template.md $POST_ROOT/$FILENAME
"${EDITOR:-vi}" $POST_ROOT/$FILENAME
EOF
{% endhighlight %}

Allow user to execute np
{% highlight bash %}
chmod +x ~/bin/np
{% endhighlight %}

Make sure that there is a template.md in $POST_ROOT, for example:
{% highlight bash %}
---
layout: post
tags:
title:
published: false
---
{% endhighlight %}

Create new post
{% highlight bash %}
np new post name
{% endhighlight %}
