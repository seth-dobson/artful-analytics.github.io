A simple approach using Jekyll, GitHub, and RStudio Cloud

Introduction
------------

Let’s be honest. Can you really call yourself a member of the
[\#rstats](https://twitter.com/search?q=%23rstats&src=hashtag_click)
community if you don’t have your own blog where you share cool stuff
about [R](https://www.r-project.org/about.html)? Yes. But many R users
and developers blog regularly about R, and many of them use the package
[blogdown](https://bookdown.org/yihui/blogdown/) to do it.

Blogdown is awesome. It helps you create really nice looking personal
websites using [R Markdown](https://rmarkdown.rstudio.com/). And with
RStudio’s built-in blogdown package support, creating a new blog is as
easy as `File -> New Project -> New Directory -> Website`, once blogdown
and [Hugo](https://gohugo.io/) are installed locally.

Here’s my problem. I prefer to use a
[Chromebook](https://www.google.com/chromebook/) for my recreational
data science activities, which means I work almost exclusively in
[RStudio Cloud](https://rstudio.cloud). So for me, blogdown is not a
viable option. Blogdown requires you to download Hugo and build your
site locally, which defeats the purpose of a Chromebook in my opinion.
I’d rather do everything in the cloud if possible.

Fortunately, RStudio Cloud has excellent integration with GitHub, and
[GitHub Pages](https://pages.github.com/) lets you create a blog
directly from a repository with [Jekyll](https://jekyllrb.com/). Like
Hugo, Jekyll is a static website generator. The advantage of Jekyll for
Chromebook and/or RStudio Cloud users is that setting up a blog is as
easy as [forking a
repository](https://help.github.com/en/github/getting-started-with-github/fork-a-repo)
(see below). With Jekyll, there is no need to download anything, or to
build the site locally before deploying it GitHub Pages. You can, but
it’s not necessary.

In this post, I will describe how to quickly set up an R blog on GitHub
Pages using Jekyll and RStudio Cloud.

Getting started with Jekyll Now
-------------------------------

Barry Clark has written an excellent tutorial entitled [Build A Blog
With Jekyll And GitHub
Pages](https://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/)
that you should read. In this section, I will briefly summarize some of
the main points of the tutorial. I will assume you already have a GitHub
account.

The first step in building your own site is to go to the [Jekyll
Now](https://github.com/barryclark/jekyll-now) repository (or other
Jekyll theme repo) and click `fork` in the upper right hand corner. Now
you have an exact copy of the repo on your GitHub account.

Next, simply rename the forked repository as \[yourusername\].github.io
and presto! GitHub Pages will build a site using the Jekyll Now theme,
and host it for free at the aformentioned URL. It’s just that simple.

At this point, you will want to customize your site’s appearance by
making changes to the `_config.yml` file in the main branch of the repo.
This is where you can give your site a name and a brief description. You
can also add an avatar, RSS feed, and social links that will appear at
the bottom of your site. The Jekyll Now config file is well commented
and easy to follow.

Lastly, you should update the `about.md` file in the main branch if you
want to have an “About Me” page on your blog that is well…about you.

After following these simple steps to set up your blog, you’re ready to
connect to RStudio Cloud and start writing \#rstats posts.

Writing Posts in RStudio Cloud
------------------------------

### Connect to repository

To connect your new GitHub repo to RStudio Cloud, all you have to do is
follow a few [simple
steps](https://bren.zendesk.com/hc/en-us/articles/360015826731-How-to-connect-RStudio-Cloud-with-Github).

First, in your Workspace, click on “New Project” and select “New Project
from GitHub Repo”. Here you will be asked to enter the URL of your blog
repository. Just copy and paste it, and click enter. RStudio Cloud will
do the rest!

The next thing you’ll want to do is configure Git in the RStudio Cloud
terminal tab with the following lines of code:

`git config --global user.email "your email address"`
`git config --global user.name "your GitHub user name"`

Now you can add, commit, and push to your heart’s content (If you have
no idea what the heck I’m talking about, read this [Git/GitHub
tutorial](https://kbroman.org/github_tutorial/) by [Karl
Broman](https://twitter.com/kwbroman)).

### Create RMarkdown file

After you get your GitHub repo connected to RStudio Cloud, you’re ready
to start writing your posts.

Jekyll uses [Markdown](https://www.markdownguide.org/getting-started/)
files to create your website, but you will want to write your posts in
RMarkdown. That means you have to create a new RMarkdwon document and
add the following to the [YAML](https://en.wikipedia.org/wiki/YAML)
front matter so you can [knit](https://yihui.org/knitr/) to Markdown.

output: md\_document: variant: markdown\_github

Save your .Rmd files in the format year-month-day-title.Rmd. I save mine
to a “drafts” folder in the main branch of my blog’s repo/project. If
your post has charts, make sure to name the associated R chunks so that
the saved images will have meaningful names after knitting to Markdown.

### Knit to Markdown

Before you publish your post, you first need to knit to Markdown by
clicking `Knit -> Knit to md_document` at the top of your notebook. This
will create a .md version of your post, as well as a folder of images
with any charts that you created.

Move the .md file to the "\_posts" folder in the main branch of your
repo/project. And move the charts and any other images to the “images”
folder. Now you’re ready to publish.

Publishing on GitHub Pages
--------------------------

### Commit and Push Changes

To publish your post on GitHub Pages, you need to Commit and Push the
changes to your project. I use the Git tab in RStudio Cloud for this.
It’s right next to the Connections tab.

First check the box that says “Staged” next to each document, then click
Commit. This will open a new Git window where you can enter a Commit
message (like “added new post”) and click Commit once more. If all goes
well, you will be allowed to click Push and sign-in to GitHub with your
credentials. Once you’ve authenticated, the post will be pushed to
GitHub and published on your website.

### Don’t forget!

Before you’re done, there is a couple of things you need to do to the
.md version of your post in GitHub.

You need to manually add links to the images in you blog post by editing
the .md file. Each image should be coded as
`![](/images/image-name.png)`.

You should also add the following to the YAML front matter of the .md
file.

layout: post title: Title of Post

Conclusion
----------

If you’re a Chromebook user like me and you want to use RStudio Cloud to
blog about R, then the easiest way to get started is to fork the Jekyll
Now theme (or another theme) to your GitHub account. Then follow the
simple instructions in this post to leverage RStudio Cloud’s excellent
GitHub integration to create and publish blog posts on your free
github.io website.

Questions or comments?
----------------------

Feel free to reach out to me at any of the social links below.

**For more R content, please visit
[R-bloggers](https://www.r-bloggers.com/) and
\[RWeekly.org\](<a href="https://rweekly.org/" class="uri">https://rweekly.org/</a>.**
