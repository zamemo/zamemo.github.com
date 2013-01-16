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
usermod -a -G sudo user1
{% endhighlight %}

Force user1 to change password at next login
{% highlight bash%}
chage -d 0 user1
{% endhighlight %}

<div class="input-append">
  <input class="span5" id="changeme" type="text" value="user1" />
  <button class="btn" type="button" id="change_button">Update Text</button>
</div>

<script>
function jQueryLoaded(){
    var old_val = $('#changeme').val();
    $('#change_button').on('click', function(){
        $(".bash,p").each(function(i){
            $(this).text($(this).text().replace(old_val, $('#changeme').val()));
        });
        old_val = $('#changeme').val();
    });
}

function checkJQuery(){
    if(window.jQuery){
        jQueryLoaded();
    }else{
        window.setTimeout(checkJQuery, 50);
    }
}

checkJQuery();
</script>
