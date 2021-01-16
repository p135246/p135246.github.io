---
layout: post
title:  "Notes about maintaing this website (constantly updated)"
date:   2020-02-02 15:36:00 -0000
categories: changelog
---

## February 3, 2021 --- Upload of a CV

After a year of not doing anything on the website, I decided to upload my CV.
However, it was not that straightforward and I had to recall some knowledge about Jekyll, Ruby, OpenSuse and Markdown and confirm my choices.

1.	There are two mainstream static website generators: [Jekyll][jekyll-home] and [Hugo][go-home].
	An advantage of Jekyll over Hugo is supposedly its bigger extensibility by plugins and a disadvantage the necessity to have a working installation of Ruby. 
	I decided to use *Jekyll*.
2.	My system is *openSUSE Leap 15.2* (`cat /usr/lib/os-release`).
	[Ruby][ruby-home] was probably installed via `sudo zypper in ruby`.
	Running `ruby -v` gives `ruby 2.5.8p224`.
	[Bundler][bundler-home], the "consistent environment for Ruby projects by tracking and installing the exact gems and versions that are needed", is installed via `sudo gem install bundler`.
	Using Bundler, one can specify gems and versions in Gemfile in the project directory.
	For some reason, the bundler executable is `/usr/bin/bundle.ruby2.5`.
	Running `bundler.ruby2.5 -v` gives `Bundler version 2.2.5`.
	Jekyll was installed `sudo gem install jekyll`.
	Recall that RubyGem is a package manager for Ruby was probably packaged together with Ruby.
	One can information about the current Ruby and RubyGem installation by running `gem environment`.
	It shows that the installation path for gems is `/usr/lib64/ruby/gems/2.5.0`.
	There is a discussion on that it is better to install gems in the local folder.
	However, because the zypper installation is configured to put gems in the above path, I have to install everything using `sudo`.
	It is proposed to remove the whole installation of Ruby and install everything locally using [RVM][rvm-home].
	However, running `sudo zypper rm ruby` would lead to the removal of many packages.
	Hence, I stick with the global root installation of gems.
3.	In order to convert the project to a website, run `bundler.ruby2.5 exec jekyll build` in the project directory.
	This produces a static website (HTML, CSS, JavaScript) in `_site`.
	The website can be tested on the local machine by running `bundler.ruby2.5 exec jekyll serve` and then opening `http://localhost:4000/` in your favorite internet browser.
4. 	I encountered a problem of adding a static file (my CV) to the website.
	I created a directory `assets/pdf` in the project folder and created a symlink `academic-cv.pdf` in it.
	I referred to it by defining `[jekyll-home]:{{ site.url }}/assets/pdf/academic-cv.pdf` and writing `[Academic CV][jekyll-home]` in `about.markdown`.
	However, the link was not working because `bundler.ruby2.5 exec jekyll build` did not copy `assets/pdf/academic-cv.pdf` in `_site`.
	The solution was to add the following to `_config.yml`:

			include:
				- assets/

5.	If updating the website after a `git push master origin` takes too long, it is possible that there is an error message in `GitHub/Settings`.
	The repository containing the website must be public.
	If it is switched to private, the website is not published anymore.

## February 2, 2020 --- Website created!

My first post after setting up the website using `jekyll` (see [jekyll-docs][jekyll-docs]).
I put together a [list of git repositories]({% link git-repositories.markdown %}) which I want to publish.  
		
[jekyll-docs]:https://jekyllrb.com/docs/home
[jekyll-home]:https://jekyllrb.com/
[go-home]:https://gohugo.io/
[ruby-home]:https://rubyonrails.org/
[bundler-home]:https://bundler.io/
[rvm-home]:https://rvm.io/
