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

<div class="input-append">
  <input class="span5" id="changeme" type="text">
  <button class="btn" type="button" id="change_button">Update Text</button>
</div>

<script>
var old_val = $('#changeme').val();
$('#change_button').on('click', function(){
    $(".bash,p").each(function(i){
        $(this).text($(this).text().replace(old_val, $('#changeme').val()));
    });
    old_val = $('#changeme').val();
});
</script>
