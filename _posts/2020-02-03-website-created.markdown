---
layout: post
title:  "Notes about maintaing this website (constantly updated)"
date:   2020-02-02 15:36:00 -0000
categories: changelog
---

## February 3, 2021 --- Upload of a CV

After a year of not doing anything on the website, I decided to upload my CV.
However, it was not that straightforward and I had to recall some knowledge of Jekyll, Ruby, OpenSuse and Markdown and confirm my choices.

1.	There are two mainstream static website generators: [Jekyll][jekyll-home] and [Hugo][go-home].
	An advantage of Jekyll over Hugo is supposedly its bigger extensibility by plugins and a disadvantage the necessity to have a working installation of Ruby. 
	
	I decided to use **Jekyll**.

2.	My system is **openSUSE Leap 15.2** (`cat /usr/lib/os-release`).
	
	[Ruby][ruby-home], which provides the command `ruby`, was probably installed a long time ago by running `sudo zypper in ruby`.
	Running `ruby -v` gives `ruby 2.5.8p224`.
	RubyGem, which provides the command `gem`, is a package manager for Ruby, which is probably packaged together with Ruby.
	
	[Bundler][bundler-home], the "consistent environment for Ruby projects by tracking and installing the exact gems and versions that are needed", is installed by running `sudo gem install bundler`.
	Using Bundler, one can specify gems and versions in the file `Gemfile` in the project directory.
	For some reason, the correct bundler executable on my system is `/usr/bin/bundle.ruby2.5` and not `/usr/bin/bundle`, which also exists, but running it gives some RubyGem version error. 
	This is probably related to an automatic update to a new version of Ruby during the last year and an effort of the system to keep also the old version **(?)**.
	Running `bundler.ruby2.5 -v` gives `Bundler version 2.2.5`.
	One can information about the current Ruby and RubyGem installation by running `gem environment`.
	It shows that the installation path for gems is `/usr/lib64/ruby/gems/2.5.0`.
	Some people on the internet suggest that it is better to install gems in a local folder in `~`.
	However, because the zypper installation is configured to put gems in the `/usr` path, I decided to install everything there using `sudo`.
	Some propose to remove the whole package installation of Ruby and install everything locally using [RVM][rvm-home].
	However, running `sudo zypper rm ruby` would lead to  removal of many packages on my system.
	Therefore, I will stick with the global installation as root.

	Jekyll was installed by running `sudo gem install jekyll`.
	Running `bundler.ruby2.5 exec jekyll -v` gives `jekyll 3.8.5`.

3.	In order to convert the project to a website, run `bundler.ruby2.5 exec jekyll build` in the project directory.
	This produces a static website consisting of HTML, CSS and possibly JavaScript **(?)** in the directory `_site/`.
	The website can be tested on the local machine by running `bundler.ruby2.5 exec jekyll serve` and then opening `http://localhost:4000/` in Google Chrome.

4. 	I encountered a problem when adding a static file---my CV in pdf---to the website.
	I created a directory `assets/pdf` in the project folder and copied `academic-cv.pdf` to it.
	I referred to it by defining `[CV]:{{ site.url }}/assets/pdf/academic-cv.pdf` and writing `[Academic CV][CV]` in `about.markdown`.
	However, the link was not working either locally or on GitHub because `bundler.ruby2.5 exec jekyll build` did not copy `assets/pdf/academic-cv.pdf` to `_site/`.
	The solution was to add the following to `_config.yml`:

			include:
				- assets/

	Also, I first created `academic-cv.pdf` as symlink, but for some strange reasons it was not copied to `_site/` and was not working even on GitHub Pages, although Git should replace symlinks by copies of the actual files in a commit **(?)**.

5.	After making changes to the project, I ran `git add *`, `git commit -m "message"` and `git push master origin` to push the changes to GitHub.
	This should be automatically processed by [GitHub Pages][github-pages] within seconds and published on the given URL.
	If this takes too long, there is probably an error message in `GitHub/Settings`.
	I got one error about a non-working link before I modified `_config.yml` as above and another error about trying to publish sensitive data before I removed `Gemfile.lock` from the commit.
	Until I corrected these issues, GitHub Pages was silently refusing to publish the website and it took me a while to find the error messages in `GitHub/Settings`.	

6.	I should be using the folder `_drafts/` which contains posts under construction which are not incorporated by Jekyll in the final website.
	Weirdly, this directory seems not to be included in a git commit, even if it is not in `.gitignore` **(?)**.
	However, I put it there just to be sure.
	The files are stored under the name `name.markdown`, i.e., not `yyyy-mm-dd-name.markdown` as in `drafts`.
	

## February 2, 2020 --- Website created!

My first post after setting up the website using `jekyll` (see [jekyll-docs][jekyll-docs]).
I put together a [list of git repositories]({% link git-repositories.markdown %}) which I want to publish.  
		
[jekyll-docs]:https://jekyllrb.com/docs/home
[github-pages]:https://pages.github.com/
[jekyll-home]:https://jekyllrb.com/
[go-home]:https://gohugo.io/
[ruby-home]:https://rubyonrails.org/
[bundler-home]:https://bundler.io/
[rvm-home]:https://rvm.io/
