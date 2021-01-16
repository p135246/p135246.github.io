---
layout: post
title:  "Notes about maintaing this website (constantly updated)"
date:   2020-02-02 15:36:00 -0000
categories: changelog
---

## February 3, 2021 --- Upload of a CV

After a year of not doing anything on the website, I decided to upload my CV.
Unfortunately, it was not that straightforward and I had to recall some knowledge of Jekyll, Ruby, OpenSuse and Markdown.
I also had to think about the whole concept to confirm my choices from a year ago.

1.	There are two mainstream static website generators: [Jekyll][jekyll-home] and [Hugo][go-home].
	An advantage of Jekyll over Hugo is supposedly its bigger extensibility by plugins and a disadvantage the necessity to have a working installation of Ruby. 
	
	I decided to use **Jekyll**.

2.	My system is **openSUSE Leap 15.2**, which I obtain by running `cat /usr/lib/os-release`.
	
	The interpreter (or compiler) of [Ruby][ruby-home] was probably installed a long time ago by running `sudo zypper in ruby`.
	It provides the command `ruby`, and running `ruby -v` gives `ruby 2.5.8p224`.
	The package (or gem in Ruby terms) manager RubyGem is probably packed in one `*.rpm` together with Ruby or is installed automatically as a dependency **(?)**.
	It provides the command `gem`, and running `gem -v` gives `3.1.2`.

	[Bundler][bundler-home], the "consistent environment for Ruby projects by tracking and installing the exact gems and versions that are needed", is installed by running `sudo gem install bundler`.
	Using Bundler, one can specify the required gems and versions in the file `Gemfile` in the project directory and Bundler automatically takes care of their download and configuration.
	For some reason, the correct bundler executable on my system is `/usr/bin/bundle.ruby2.5` and not `/usr/bin/bundle`.
	The latter also exists on my system, but running it gives a RubyGem version error **(?)**. 
	This is probably related to an automatic `zypper` update to a new version of Ruby during the last year and an effort of the system to keep both the new and old version **(?)**.
	Running `bundler.ruby2.5 -v` gives `Bundler version 2.2.5`.

	Information about the current Ruby and RubyGem installation can be displayed by running `gem environment`.
	It shows that the gems are installed to `/usr/lib64/ruby/gems/2.5.0/`.
	Some people on the internet suggest that it is better to install gems in a hidden folder in `~` (the "user installation directory" in `gem environment`).
	However, because the zypper installation is configured to put gems in `/usr/...` by default, and I do not want to fiddle with that, I decided to install everything globally using `sudo`.
	Some people propose to remove the `zypper` installation of Ruby and install everything locally using [RVM][rvm-home].
	However, running `sudo zypper rm ruby` on my system would lead to removal of many, seemingly important, packages **(?)**, which I don't want.
	Therefore, I will stick to the global installation as root.

	Jekyll was installed by running `sudo gem install jekyll`.
	Running `bundler.ruby2.5 exec jekyll -v` gives `jekyll 3.8.5`.
	The correct executable is again `jekyll.ruby2.5` and not `jekyll`, but it is suggested to run `jekyll` via `bundler.ruby2.5 exec jekyll` anyway.
	It is namely the purpose of Bundler to create a neat environment for Ruby programs.

3.	In order to convert the project to a website, run `bundler.ruby2.5 exec jekyll build` in the project directory.
	This produces a static website consisting of HTML, CSS and possibly JavaScript **(?)** in the directory `_site/`.
	The website can be tested on the local machine by running `bundler.ruby2.5 exec jekyll serve` and then opening `http://localhost:4000/` in a web browser, in my case Google Chrome.

4. 	I encountered a problem when adding the static file `academic-cv.pdf` to the website.
	I created a directory `assets/pdf/` in the project folder and copied `academic-cv.pdf` to it.
	I referred to it by defining `[CV]:{{ site.url }}/assets/pdf/academic-cv.pdf` and writing `[Academic CV][CV]` in `about.markdown`.
	However, the link was not working either locally or on GitHub because `bundler.ruby2.5 exec jekyll build` did not copy `assets/pdf/academic-cv.pdf` to `_site/`.
	The solution was to add the following to `_config.yml`:

			include:
				- assets/

	Also note that I first created `academic-cv.pdf` as a symlink, but it was not copied to `_site/` and was not working on GitHub Pages even after modifying `_config.yml` as above.
	This is strange because Git should replace symlinks by copies of the actual files in a commit, and hence it should have worked at least on GitHub Pages **(?)**.

5.	After making my changes to the project, I ran the standard triple `git add *`, `git commit -m "message"` and `git push master origin` to push the changes to GitHub.
	As soon as the commit arrives to GitHub, it should be automatically processed by the engine of [GitHub Pages][github-pages] and within seconds published on the given URL, provided that it is properly configured in `GitHub/Settings`.
	If this process takes too long, there is probably an error while running `jekyll` on the server side, and an error message appears in `GitHub/Settings`.
	Before modifying `_config.yml`, I was getting an error which said that the link to `academic-cv.pdf` was not working.
	After that, I was getting another error which sad that I was trying to publish sensitive data.
	This was solved by removing `Gemfile.lock`, which seems to contain informations about versions of gems on the machine, from the commit.
	Before I discovered and corrected these issues, GitHub Pages had been silently refusing to publish the website and it took me a while to find out that there were error messages in `GitHub/Settings`.	

6.	I should be using the folder `_drafts/` which contains posts under construction which are not incorporated by Jekyll in the final website.
	Weirdly, this directory seems not to be included in a git commit even if it is not in `.gitignore` **(?)**.
	However, I put it in `.gitignore` just to be sure that the drafts do not leak to public.
	The files in `_drafts/` have names in the form `name.markdown`, i.e., not `yyyy-mm-dd-name.markdown` as the files in `drafts`.
	

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
