---
layout: page
title: "JavaScript basename function"
comments: true
sharing: true
footer: true
alias:
- /functions/view/basename:360
- /functions/view/basename
- /functions/view/360
- /functions/basename:360
- /functions/360
---
<!-- Generated by Rakefile:build -->
A JavaScript equivalent of PHP's basename

{% codeblock filesystem/basename.js lang:js https://raw.github.com/kvz/phpjs/master/functions/filesystem/basename.js raw on github %}
function basename(path, suffix) {
  //  discuss at: http://phpjs.org/functions/basename/
  // original by: Kevin van Zonneveld (http://kevin.vanzonneveld.net)
  // improved by: Ash Searle (http://hexmen.com/blog/)
  // improved by: Lincoln Ramsay
  // improved by: djmix
  // improved by: Dmitry Gorelenkov
  //   example 1: basename('/www/site/home.htm', '.htm');
  //   returns 1: 'home'
  //   example 2: basename('ecra.php?p=1');
  //   returns 2: 'ecra.php?p=1'
  //   example 3: basename('/some/path/');
  //   returns 3: 'path'
  //   example 4: basename('/some/path_ext.ext/','.ext');
  //   returns 4: 'path_ext'

  var b = path;
  var lastChar = b.charAt(b.length - 1);

  if (lastChar === '/' || lastChar === '\\') {
    b = b.slice(0, -1);
  }

  b = b.replace(/^.*[\/\\]/g, '');

  if (typeof suffix === 'string' && b.substr(b.length - suffix.length) == suffix) {
    b = b.substr(0, b.length - suffix.length);
  }

  return b;
}
{% endcodeblock %}

 - [Raw function on GitHub](https://github.com/kvz/phpjs/blob/master/functions/filesystem/basename.js)

Please note that php.js uses JavaScript objects as substitutes for PHP arrays, they are 
the closest match to this hashtable-like data structure. 

Please also note that php.js offers community built functions and goes by the 
[McDonald's Theory](https://medium.com/what-i-learned-building/9216e1c9da7d). We'll put online 
functions that are far from perfect, in the hopes to spark better contributions. 
Do you have one? Then please just: 

 - [Edit on GitHub](https://github.com/kvz/phpjs/edit/master/functions/filesystem/basename.js)


### Other PHP functions in the filesystem extension
{% render_partial _includes/custom/filesystem.html %}
