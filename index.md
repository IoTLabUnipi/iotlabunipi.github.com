---
layout: page
title: Internet of Things
tagline: Lab Website
---
{% include JB/setup %}
This is the lab page of the Internet of Things course held within the second year program of L.M. in Computer Engineering of the Dept. of Information Engineering of the University of Pisa by [Prof. Enzo Mingozzi](http://www2.ing.unipi.it/~a009395/home/index.htm).
The lab classes are held by [Dr. Giacomo Tanganelli](http://www.iet.unipi.it/g.tanganelli/).
This page contains specific material for the lab classes. General material for the course can be found [here](http://www2.ing.unipi.it/~a009395/corsi/iot/index.shtml).

<ul style="list-style: none;">
            {% for post in site.posts %}
		    {% assign currentDate = post.date | date: "%Y" %}
			{% if currentDate == "2016" %}
		            <li>
		            <a href="{{ post.url }}">
		             <h3>{{ post.title }}</h3> </a>
		             <p class="blogdate">{{ post.date | date: "%d %B %Y" }}</p>
		             <div>{{ post.content }}</div>
		             </li>
			{% endif %}
            {% endfor %}
</ul> 



