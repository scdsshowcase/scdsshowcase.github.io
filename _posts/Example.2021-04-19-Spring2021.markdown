---
layout: post
title:  "Spring2021"
date:   2021-04-17 11:55:45 -0400
categories: jekyll update
---

test2 `code` goes here. 

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

List of project titles, linked to below: 
<ul>
{% for teami in site.data.test %}
  <li>
    <a href="#{{ teami.Title }}">
      {{ teami.Title }}
    </a>
  </li>
{% endfor %}
</ul>

Make a more presentable one: 
Video embedding: assumes last 11 chars are the video specific and uses that to create an embed link. So, timed links, etc. will be broken. 

<!-- loop through each team's data from CSV file as teami -->
<!-- CSV file should be saved to _data folder. Ex: _data/test.csv -->
{% for teami in site.data.test %}
  <ul>
  <p id="{{ teami.Title }}"></p> <!-- Create a link to this section of the page -->
  <h2> Project: {{ teami.Title }}</h2>
    <b>Team Members:</b> {{teami.Members}}<br>
    <b>Program:</b> {{teami.Program }}<br>
    <b>Keywords:</b> {{teami.Keywords }}<br>
    <b> YouTube video: </b><a href="{{ teami.YouTube }}">
      {{ teami.YouTube }}</a><br>
      <!-- Youtube link embedding: assume that last 11 chars are the video id and use that to create an embed link -->
      {% assign vlink = teami.YouTube | | slice: -11, 11%}
     <iframe width="420" height="315" src="https://www.youtube.com/embed/{{ vlink }}"  frameborder="0" allowfullscreen></iframe><br>
    <b>Abstract:</b> {{teami.Abstract }}<br>
    </ul>
{% endfor %}


Testing csv processing:
tr/th tages to create the table header row

<table>
  {% for row in site.data.authors %}
    {% if forloop.first %}
    <tr>
      {% for pair in row %}
        <th>{{ pair[0] }}</th>
      {% endfor %}
    </tr>
    {% endif %}

    {% tablerow pair in row %}
      {{ pair[1] }}
    {% endtablerow %}
  {% endfor %}
</table>

Test the student responses as a simple table 

<table>
  {% for row in site.data.test %}
    {% if forloop.first %}
    <tr>
      {% for pair in row %}
        <th>{{ pair[0] }}</th>
      {% endfor %}
    </tr>
    {% endif %}

    {% tablerow pair in row %}
      {{ pair[1] }}
    {% endtablerow %}
  {% endfor %}
</table>



Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
