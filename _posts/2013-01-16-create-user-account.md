---
layout: post
tags: linux
title:
---
Create a new user called user1 with home directory
{% highlight bash%}
useradd -m user1
{% endhighlight %}

Setup password for user1
{% highlight bash%}
passwd user1
{% endhighlight %}

Add user1 to group sudo
{% highlight bash%}
useradd -G sudo user1
{% endhighlight %}

<script>
function test(){
    alert('1');
}
</script>
