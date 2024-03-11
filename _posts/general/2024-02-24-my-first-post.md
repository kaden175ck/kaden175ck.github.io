---
layout: post
title: "Notes about Jekyll"
date: 2024-02-24
categories: general
permalink: "/General/NotesAboutJekyll"
---

#### This is just me messing around with Jekyll and some random notes about it. If you are interested about using Jekyll, this might be usefull, just saying:)


![This is just me Testing the Images:)](/assets/images/my-first-post-image.jpg)

* this is called front matter, just vars, key value pair, you can write it in JSON or YAML. Not that important, but must have.

```
layout: post
title: "Test Post"
date: 2024-02-24
categories: general
```
<hr>
<br>


**_drafts**: Draft blog posts can be kept here. They are posts you're still working on, which won't be displayed on the live site until they are moved to the `_posts` directory and given a date in the filename.

* command: jekyll serve --draft
* But I think this method is really unnecessay, you can just put a future date and view it directly with command "Jekyll serve" , and when you think its good, just change the data and post it.

#### Another way: You can include a line in your YAML Front Matter to indicate whether a post is published or not: published: true or published: false

#### One more note: If I delete the permalink in front matter, it will just be default link like cat/date/postname...and that is ok!
