---
title:		"Website's technical changelog"
categories: IT
mathjax: 	true
utterances: true
---

# Website's technical changelog

Here I will keep notes on technical changes made to this website.
Current workflow will be summarized on the [repository page](https://github.com/p135246/p135246.github.io).

## January 22, 2023 --- Main rework

I stopped using the [minima theme](https://github.com/jekyll/minima) and wrote the website from scratch.

## January 17, 2021 --- Adding support for comments, mathjax, emojis and syntax highlighting

I wanted to include *comments* and [Mathjax][mathjax] support in my posts.

1.	There is various ways to include comments in a static website hosted on GitHub.
	One way is to use an external web application and database like [Disqus][disqus] and an other way is to use an external script [Staticman][staticman], which simulates the dynamic behavior by processing and pushing user input to GitHub automatically.

	Nevertheless, there is also [Utterances][utterances] which works on a similar principle as Staticman, but instead of storing comments in new files in the repository,  it creates an Issue in the native GitHub discussion system and puts the commentaries there!
	This is seemingly the best solution, and hence I decided to use **Utterances**.
	Staticman might be useful in the future when I need, e.g., input forms.

2. 	A disadvantage of the GitHub's issues and comments system is that it does not support Mathjax.
	In order to insert formulas in the comments, internet people (:= people on the internet) recommend to use
	```html
	<img src="https://latex.codecogs.com/svg.latex?f(x)=\pi^2+x+\sum_{i=1}^ka_i"/>
	```
	which renders the formula $$f(x)=\pi^2+x+\sum_{i=1}^ka_i$$ as an image on the fly.
	If your formula contains a space or some special characters, please, test the URL before posting your comment.
	For instance, the white space can be written as `%20` in the URL.

3.	GitHub comments support a ton of emoji's, which are listed for instance [here][emojis].
	Emojis can be also inserted in my posts.
	The recommended plugin `jemoji`, which uses GitHub's emojis, is mentioned in the [documentation][github-pages-and-jekyll].
	The corresponding gem is installed on the local machine via Bundler by adding  `gem "jemoji"` in `Gemfile` and running `bundler.ruby2.5 install` in the project directory. 
	In order to tell jekyll to use it, one has to add `jemoji` to the list of plugins in `_config.yml`.
	Writing 
	{% raw %}
	```ruby
	:blush: :bowtie: :hankey: :+1:
	```
	{% endraw %}
	in Markdown produces  :blush:, :bowtie:, :hankey:, :+1:.
        Unfortunately, it seems like that there is not the :vomiting_face: emoji, which can be used normally in the comments. :cry:	

4.	I wanted to modify the default layout for a post so that comments and mathjax can be turned on and off liquidly by setting the variables `comments` and `mathjax` in the  YAML front matter of a post (the header between `--- ... ---`).
	Internet people claim that it can not be done easily and one has to copy the default layouts of the jekyll theme in use to the project folder and modify those.  
	I use the `mimina` theme, which is installed as a gem.
	I ran `bundler.ruby2.5 info minima` to get the path to the gem, which is `/usr/lib64/ruby/gems/2.5.0/gems/minima-2.5.1` in my case.
	I displayed the directory structure using the `tree` command and had a look at what is in `_includes` (HTML snippets to be included), `_layouts` (page layouts) and `_sass` (some CSS related things).
	Because I wanted to modify the layout for posts, I copied  `_layouts/post.html` to the project directory.
	I then created the files `_includes/mathjax-support.html` and `_includes/comments-utterances.html` with the following content in the project directory. 

	File `_includes/mathjax-support.html:` 
	```html
	<!-- for mathjax support -->
	<script type="text/x-mathjax-config">
		MathJax.Hub.Config({
		TeX: { equationNumbers: { autoNumber: "AMS" } }
		});
	</script>
	<script type="text/javascript" async src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
	</script>
	```
	File `_includes/comments-utterances:`
	```html
	<!-- for comment section -->
	<script src="https://utteranc.es/client.js"
		repo="p135246/p135246.github.io"
		issue-term="title"
		label="comment"
		theme="preferred-color-scheme"
		crossorigin="anonymous"
		async>
	</script>
	```
	These snippets can be found in the documentation of [Mathjax][mathjax] and of [Utterances][utterances], respectively.

	Finally, I modified `_layouts/post.html` by including
	{% raw %}
	```ruby
	{%- if page.mathjax -%}
		{%- include mathjax-support.html -%}
	{%- endif -%}
	```
	{% endraw %}
	in the header tag and
	{% raw %}
	```ruby
	{%- if page.comments -%}
		{%- include comments-utterances.html -%}
	{%- endif -%}
	```
	{% endraw %}
	at the end of the article tag, which is where I want the comments to be displayed.
	Note that I quote the liquid syntax by enclosing it in the `raw` and `endraw` liquid commands.

	In `_config.yml`, I put the following
	```ruby
	markdown: kramdown
	math_engine: mathjax	
	input: GFM
	highlighter: rouge
	```	
	The first option tells `Jekyll` which Markdown interpreter to use and the second enables Mathjax.
	The third option tells to use [GitHub flavored Markdown][GFM] and the fourth to use the syntax highlighter [rogue][rogue]. 
	See the official documentation of GitHub Pages about Jekyll [here][github-pages-and-jekyll].
	

	Now, Mathjax support and the comment section, which appears on the bottom of the page, can be turned on and off in the header as in the example of this post:
	```ruby
	---
	layout: post
	title:  "Notes about maintaining this website (constantly updated)"
	date:   2020-02-02 15:36:00 -0000
	categories: changelog
	comments: true
	mathjax: true
	---
	```

5.	A note on Mathjax.
	Formulas are enclosed in `$$...$$` and whether they are inline, like $$\sqrt{45\pi}$$, or displayed, like

	$$
	\begin{aligned}
		a_1 &= 16\pi e^2, \\
		a_2 &= 5.3534, \\
		a_3 &= \ldots,
	\end{aligned}
	\qquad
	A = 	\begin{pmatrix}
			4 & 8 & 5 \\
			2 & 1 & 0 \\
			3 & 9 & 6
		\end{pmatrix},
	$$

	is decided by the markdown indentation.

6.	In order to enable syntax highlighting, one has to add `rogue` to `_config.yml` as above.
	The following construction, where `md` can be replaced by `html`, `ruby`, ...  highlights the code:
	````md
	```md
		Some markdown **code** here.
	```
	````
	Note that in order to render this code block with three ticks, I had to enclose it in four ticks, and so on (the following was enclosed in five ticks):	
	`````md
	````md
	```
		Some markdown **code** here.
	```
	````
	`````
	Internet people say that in order to highlight inline code, the following construction has to be used
	```
	`x = 4`{:.ruby}
	``` 
	However, it produces `x = 4`{:.ruby}, which does not seem to work on my local machine.

## January 15, 2021 --- Upload of a CV

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
	```ruby
	include:
		- assets/
	```
	Also note that I first created `academic-cv.pdf` as a symlink, but it was not copied to `_site/` and was not working on GitHub Pages even after modifying `_config.yml` as above.
	This is strange because Git should replace symlinks by copies of the actual files in a commit, and hence it should have worked at least on GitHub Pages **(?)**.

5.	After making my changes to the project, I ran the standard triple `git add *`, `git commit -m "message"` and `git push master origin` to push the changes to GitHub.
	As soon as the commit arrives to GitHub, it should be automatically processed by the engine of [GitHub Pages][github-pages] and within seconds published on the given URL, provided that it is properly configured in `GitHub/Settings`.
	If this process takes too long, there is probably an error while running `jekyll` on the server side, and an error message appears in `GitHub/Settings`.
	Before modifying `_config.yml`, I was getting an error which said that the link to `academic-cv.pdf` was not working.
	After that, I was getting another error which sad that I was trying to publish sensitive data.
	This was solved by removing `Gemfile.lock`, which seems to contain information about versions of gems on the machine, from the commit.
	Before I discovered and corrected these issues, GitHub Pages had been silently refusing to publish the website and it took me a while to find out that there were error messages in `GitHub/Settings`.	
	I discovered much later that GitHub was sending build errors and error messages via email!

6.	I should be using the folder `_drafts/` which contains posts under construction which are not incorporated by Jekyll in the final website.
	Weirdly, this directory seems not to be included in a git commit even if it is not in `.gitignore` **(?)**.
	However, I put it in `.gitignore` just to be sure that the drafts do not leak to public.
	The files in `_drafts/` have names in the form `name.markdown`, i.e., not `yyyy-mm-dd-name.markdown` as the files in `drafts`.
	

## February 2, 2020 --- Website created!

My first post after setting up the website using `Jekyll` (see [jekyll-docs][jekyll-docs]).

[rogue]:http://rouge.jneen.net/
[GFM]:https://github.github.com/gfm/
[github-pages-and-jekyll]:https://docs.github.com/en/github/working-with-github-pages/about-github-pages-and-jekyll
[emojis]:https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md
[disqus]:https://disqus.com/
[staticman]:https://staticman.net/
[mathjax]:https://www.mathjax.org/
[utterances]:https://utteranc.es/
[jekyll-docs]:https://jekyllrb.com/docs/home
[github-pages]:https://pages.github.com/
[jekyll-home]:https://jekyllrb.com/
[go-home]:https://gohugo.io/
[ruby-home]:https://rubyonrails.org/
[bundler-home]:https://bundler.io/
[rvm-home]:https://rvm.io/

