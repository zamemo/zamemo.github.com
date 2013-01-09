---
layout: post
tags: html
title:
---
Use this to write HTML in the Plain Text field, click on Encode and bookmark/copy Data URI field.
{% highlight html %}
<html>
<head><title>Data URI Generator</title></head>
<body>
<label>Plain Text</label>
<br />
<textarea id="plaintext" rows="10" cols="50">
</textarea>
<br />
<button id="encode">Encode &gt;&gt;</button>
<br />
<button id="decode">&lt;&lt; Decode</button>
<br />

<label>Data URI</label>
<br />
<input id="data-uri" type="text" size=60></input>
<script>
var plaintext = document.getElementById('plaintext');
var dataUri = document.getElementById('data-uri');
var decode = document.getElementById('decode');
var encode = document.getElementById('encode');
plaintext.focus();
encode.addEventListener('click', function(){
    dataUri.value = 'data:text/html;charset=utf-8;base64,' + base64Encode(plaintext.value);
    }, false);
decode.addEventListener('click', function(){
    var data = dataUri.value;
    plaintext.value = base64Decode(data.replace(/data:text\/html;charset=utf-8;base64,/,''));
    }, false);
/* Base64 conversion methods.
 * Copyright (c) 2006 by Ali Farhadi.
 * released under the terms of the Gnu Public License.
 * see the GPL for details.
 *
 * Email: ali[at]farhadi[dot]ir
 * Website: http://farhadi.ir/
 */

//Encodes data to Base64 format
function base64Encode(data){
    //if (typeof(btoa) == 'function') return btoa(data);//use internal base64 functions if available (gecko only)
    var b64_map = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/=';
    var byte1, byte2, byte3;
    var ch1, ch2, ch3, ch4;
    var result = new Array(); //array is used instead of string because in most of browsers working with large arrays is faster than working with large strings
    var j=0;
    for (var i=0; i<data.length; i+=3) {
        byte1 = data.charCodeAt(i);
        byte2 = data.charCodeAt(i+1);
        byte3 = data.charCodeAt(i+2);
        ch1 = byte1 >> 2;
        ch2 = ((byte1 & 3) << 4) | (byte2 >> 4);
        ch3 = ((byte2 & 15) << 2) | (byte3 >> 6);
        ch4 = byte3 & 63;
        
        if (isNaN(byte2)) {
            ch3 = ch4 = 64;
        } else if (isNaN(byte3)) {
            ch4 = 64;
        }

        result[j++] = b64_map.charAt(ch1)+b64_map.charAt(ch2)+b64_map.charAt(ch3)+b64_map.charAt(ch4);
    }

    return result.join('');
}

//Decodes Base64 formated data
function base64Decode(data){
    data = data.replace(/[^a-z0-9\+\/=]/ig, '');// strip none base64 characters
    //if (typeof(atob) === 'function') return atob(data); //use internal base64 functions if available (gecko only)
    var b64_map = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/=';
    var byte1, byte2, byte3;
    var ch1, ch2, ch3, ch4;
    var result = new Array(); //array is used instead of string because in most of browsers working with large arrays is faster than working with large strings
    var j=0;
    while ((data.length%4) != 0) {
        data += '=';
    }
    
    for (var i=0; i<data.length; i+=4) {
        ch1 = b64_map.indexOf(data.charAt(i));
        ch2 = b64_map.indexOf(data.charAt(i+1));
        ch3 = b64_map.indexOf(data.charAt(i+2));
        ch4 = b64_map.indexOf(data.charAt(i+3));

        byte1 = (ch1 << 2) | (ch2 >> 4);
        byte2 = ((ch2 & 15) << 4) | (ch3 >> 2);
        byte3 = ((ch3 & 3) << 6) | ch4;

        result[j++] = String.fromCharCode(byte1);
        if (ch3 != 64) result[j++] = String.fromCharCode(byte2);
        if (ch4 != 64) result[j++] = String.fromCharCode(byte3);    
    }

    return result.join('');
}
</script>
</body></html>
{% endhighlight %}
