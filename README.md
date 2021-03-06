# fordworg

[![Build Status](https://travis-ci.org/Atlas7/fordworg.svg?branch=master)](https://travis-ci.org/Atlas7/fordworg)

Home page for Friends of Russia Dock Woodland. Currently hosted on this GitHub page. You can access it via either of these URLs:

- [http://fordw.org/](http://fordw.org/) custom domain name as defined in `CNAME` file.
- [https://atlas7.github.io/fordworg/](https://atlas7.github.io/fordworg/): default github pages URL. If you access via this URL you will get re-directed to the custom domain as above.

## Tech Stack

Built with:

- [Jekyll](https://jekyllrb.com/): blog framework supported by Github pages.
- [GitHub Pages](https://pages.github.com/): for hosting Github repositories
- [Jekyll Massively Theme](https://github.com/iwiedenm/jekyll-theme-massively-src): so we don't need to start from sratch!
- [formspree.io](https://formspree.io/): enable users to send email messages from the website.
- pagination with jekyll-paginate gem
- CSS: for styling

Continuous Integration with:

- Travis CI: to reduce the risk of breaking the production website by test building the Jekyll site.
- HTML Proofer Gem: enhance the Travis CI test by sanity checking the built files (`/_site`)

Some Handy References on Travis CI and Jekyll integration:

- [Jekyll, Travis CI, and Github](https://jekyllrb.com/docs/continuous-integration/travis-ci/)
- [HTML Proofer](https://github.com/gjtorikian/html-proofer): check HTML syntax

## Development Instruction

Fork the repository on Github. Then git clone from your frok:

```
git clone https://github.com/your-github-id/fordworg
```

Alteratively, git clone the repository (and push to your own repsitory later)

```
git clone https://github.com/Atlas7/fordworg
```

Navigate to the project roote:

```
cd fordworg
```

Make sure git repository has the appropriate remote. This is what you should see if you follow the fork method.

```
$ git remote -v
origin  https://github.com/Atlas7/fordworg (fetch)
origin  https://github.com/Atlas7/fordworg (push)
upstream  https://github.com/your-github-id/fordworg (fetch)
upstream  https://github.com/your-github-id/fordworg (push)
```

If you had followed the direct git clone method, you may find these dandy docs on setting up remotes (`origin` and `upstream`):

- [Github help: Changing a remote's URL](https://help.github.com/articles/changing-a-remote-s-url/)
- [Github help: Adding a remote](https://help.github.com/articles/adding-a-remote/)

Install dependencies (Ruby gems - as defined in the `Gemfile`)

```
bundle install
```

Serve the website locally:

```
bundle exec jekyll serve
```

This will serve the blog post locally at [http://127.0.0.1:4000/](http://127.0.0.1:4000/)

## How to create a new blog post

First of all, it's always a good practice to create a new branch and work there (instead of directly on master branch)

```
git checkout -b my-new-branch
```

Use an IDE (I use Webstorm, though Sublime text will also do) and a terminal (e.g. iterm2, or Mac Terminal).

### Create a new blog post

- Got to `/_posts`
- Create a markdown file with a name like this: `yyyy-mm-dd-hello-this-is-my-title.md`
- Create a meta block at the top (so called "front matters"). I usually just copy and paste from older posts and tweak.
- Write the post in markdown syntax. Feel free to embed HTML tags within your markdown post, as needed.
- (optional) add (`jpg` or `png`) images to `/images/blog`. And within your blog post you may reference to it like this:

  HTML tag style:

  ```
   <img class="image main" src="/images/blog/Bob4.jpg" alt="Bob4.jpg"/>
  ```

  or Markdown style:

  ```
  ![Bob4.jpg](images/blog/Bob4.jpg)
  ```

- Save post

### Preview post

To view the website locally:

```
bundle exec jekyll serve
```

This will serve the blog post locally at [http://127.0.0.1:4000/](http://127.0.0.1:4000/)

### Ready to push?

```
git add .
git commit -m "add new features"
git push origin my-new-branch
```

Go to Github, create a new pull request. (and as an admin myself I will happily approve and merge). Delete the
GitHub branch afterwards for tidiness (it can always be restored so no worries)

Now that GitHub is updated, update local master and sync fork:

```
git fetch upstream
git merge upstream/master
git push origin master
```

Delete the local branch for tidiness:

```
git branch -d my-new-branch
```

### Handy articles

- [Jekyll blog posts on non index.html pages](https://stackoverflow.com/questions/26048623/jekyll-blog-posts-on-non-index-html-pages): unfortunately GitHub pages doesn't support `jekyll-paginate-v2` gem yet so will need to continue with `jekyll-paginate` gem. One limitation is that pagination only works on `index.html`. To get pagination to work on a non root end point (e.g. `/pages/blog/` or `/blog/`), one must create a sub-directory (or sub-sub directory) at root, and create `index.html` inside it.
- [Setting the DNS for GitHub Pages on GoDaddy](https://medium.com/@LovettLovett/github-pages-godaddy-f0318c2f25a): use this
  instruction to link up `fordw.org` with this github page `atlas7.github.io/fordworg`
- [Configuring A records with your DNS provider](https://help.github.com/articles/setting-up-an-apex-domain/)
- [Custom domain for GitHub project pages](https://stackoverflow.com/questions/9082499/custom-domain-for-github-project-pages): to check and see if domain A records have been updated on DNS provider side, do this: `dig yourdomain.com +nostats +nocomments +nocmd`.
It should says the same thing as the DNS provider control panel. Otherwise, it could be just some kind of delay.

## Credits

This project will not be as painless / enjoyable if it's not for the Jekyll Massively Theme - which is open source
on GitHub under a Creative Common Licence. Many thanks to these folks!!! (thank you thank you thank you).

### Formspring.io Integration

Formspring is supported out of the box! Just add your email to ```_config.yml```

### Original README from HTML5 UP

```
Massively by HTML5 UP
html5up.net | @ajlkn
Free for personal and commercial use under the CCA 3.0 license (html5up.net/license)


This is Massively, a text-heavy, article-oriented design built around a huge background
image (with a new parallax implementation I'm testing) and scroll effects (powered by
Scrollex). A *slight* departure from all the one-pagers I've been doing lately, but one
that fulfills a few user requests and makes use of some new techniques I've been wanting
to try out. Enjoy it :)

Demo images* courtesy of Unsplash, a radtastic collection of CC0 (public domain) images
you can use for pretty much whatever.

(* = not included)

AJ
aj@lkn.io | @ajlkn


Credits:

	Demo Images:
		Unsplash (unsplash.com)

	Icons:
		Font Awesome (fortawesome.github.com/Font-Awesome)

	Other:
		jQuery (jquery.com)
		Misc. Sass functions (@HugoGiraudel)
		Skel (skel.io)
		Scrollex (github.com/ajlkn/jquery.scrollex)
```
