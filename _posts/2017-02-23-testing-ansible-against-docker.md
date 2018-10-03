---
layout: post
title:  "Testing ansible roles against docker"
date:   2017-02-23
desc: "Example of executing ansible roles against a docker container"
keywords: "ansible,docker,devops,vagrant,blog"
categories: [HTML]
tags: [docker,ansible]
icon: icon-html
---

This example of using docker to test ansible roles was based off Chris Meyer's [provision_docker role](https://github.com/chrismeyersfsu/provision_docker).  At the time his role wasn't working against Ansible 2.2.x.x so I stripped out what I didn't need and tailored it for my needs.  Each blog post will be a separate repository with a full working example.

The following demo was tested on macOS Sierra with vagrant 1.9.1 and virtualbox 5.1.12

Everyone wants to have a personal website, you can display your infomation to public, post blogs and make friends. If you are CS engineer, haveing a self website will benefit your interview.

So, if you like this website <https://jarrekk.github.io/Jalpc/> or <http://www.jack003.com> and are willing to have a website, here is a way to build your website in 3 steps(2 minutes). Following are steps to setup your website:

1. Fork [this project -- Jalpc](https://github.com/jarrekk/Jalpc) at [GitHub](https://github.com). If you want to edit website at github, do it as following gif or clone forked repository. `git clone git@github.com:github_username/Jalpc.git`.

	<!-- ![edit]({{ site.img_path }}/3steps/edit.gif) -->
	<img src="{{ site.img_path }}/3steps/edit.gif" width="75%">

2. Enter into repository directory and edit following file list:

	* **_config.yml**: edit 'Website settings', 'author', 'comment' and 'analytics' items.

	* **_data/landing.yml**: custom sections of index page.

	* **_data/index/**: edit sections' data to yours at index page, please notice comment at each file.

	* **_data/blog.yml**: edit navbar(categories) of blog page, if you have different/more blog page, copy `blog/python.html` and change it to your category HTML file, and edit **Python**, **/python/** to your category name at items **title** and **permalink**, make sure title is the same as permalink but capitalized first letter(except HTML).

	* **CNAME**: If you wanna release website at your own domain name: edit it and create `gh-pages` branch; if you want to use *github_username.github.io*: leave it blank.

3. Push changes to your github repository and view your website, done!

From now on, you can post your blog to this website by creating md files at `post/` directory and push it to GitHub, you can clear files at this directory before you post blogs.

If you like this repository, I appreciate you star this repository. Please don't hesitate to mail me or post issues on GitHub if you have any questions. Hope you have a happy blog time!😊