---
author: Enoch Yu
title: Building My Blog With Hugo and GitHub
date: 2025-12-14
categories: ["Miscellaneous"]
---

When I first decided to write my blog, I was thrown into bunch of
options. I noticed that *wordpress.com* and *medium* are popular
options when it comes to writing blogs. However, I also noticed that
many of the popular options would generally give less control over
my blog and require payments to use many of its features.
So it became a natural choice for me to just build one myself,
which was both a dumb and greatest choice that I ever made.
Maybe I can save this for later blogs.

## Static Site Generator (SSG)

I had two options of hosting via CMS (Content Management System) or
hosting through SSG (Static Site Generator). The main difference is
that CMS like Wordpress creates contents dynamically, whereas SSG is
simply showing the users a pre-built sites. Here, I realized that
most of my blogs would be text based, which does not require dynamic
features such as user accounts. Also, sites created with SSG is
much faster and secure compared to ones created with CMS since no
server-side processing is required when accessing.

Again, I faced multiple options for Static Site Generators.
I personally found Hugo as the ideal SSG because I seek to write large
amounts of posts and Hugo is known to be fast with Go's performance.

Finally after generating the blog locally, there must be a hosting
platform to actually deploy it. I thought of using github pages
because I will be storing the source files there anyways, but as I get
my domain I just decided to host in my subdomain. The
[source files](https://github.com/enochness/blog.enochyu.com) are still
hosted in GitHub for anyone interested.


## Installing Hugo and Making Repository in GitHub

To install Hugo, please refer to the official
[installation guide](https://gohugo.io/installation/). But if you
chose to stick here and you are on Windows, copy and paste
`winget install Hugo.Hugo.Extended` to your terminal to install.
For Mac users with Homebrew, `brew install hugo` will do the job.
I don't think I need to include one for Linux users :))

For text editors, I personally use [NeoVim](https://neovim.io/)
due to its speed and flexibility. But there are really great
text editors and IDE, and it is up to you!

If you have Hugo and code editor ready to go, we need to create a
repository in GitHub. I personally made a public repository named 
**blog.enochyu.com**. Next, we need to enter following commands
in terminal.
```bash
cd BLOG-NAME
git init
git add .
git commit -m "Initial commit"
git remote add origin
git push -u origin main
```
Sometimes, you many need to create a token in GitHub to run the
final command. When creating, "repo" section must be checked!

## Theme

As for my theme, I decided to create my own theme to be free from
copyright issues. My Hugo theme was created by merging and reading
multiple themes from [Hugo Themes](https://themes.gohugo.io/).
Please check this page out if you haven't yet; all themes that you
can imagine is probabily up there.

But if you would like to implement my theme as a submodule,
you can run the following commands in your project.
```bash
git submodule add https://github.com/enochness/EnochBlogTheme themes/EnochBlogTheme
git submodule update --init --recursive
```

To integrate the theme, please update your `hugo.toml`. It should
include the following.
```toml
baseURL = 'https://YOUR-GITHUB-ID.github.io/YOUR-REPOSITORY-NAME/'
languageCode = 'en-US'
title = "NAME OF YOUR BLOG"
theme = 'EnochBlogTheme'

[params]
  author = "YOUR NAME"
  avatar = "/images/avatar.png"
  mainSections = ["posts"]
  favicon = "favicon.ico"

[taxonomies]
category = "categories"
tag      = "tags"
```

## Creating Initial Post

To write a post, create a Markdown file `YOUR-POST.md` in
`BLOG-NAME/content/post`. For users on Unix-based operating
system, `touch YOUR-POST.md` creates the empty file.

In your Markdown file, it should include the following.
```markdown
---
author: YOUR NAME
title: YOUR TITLE
date: DATE
categories: ["YOUR CATEGORY"]
---

YOUR CONTENTS
```

After writing your initial post, the following commands must be
ran to update the GitHub repository.
```bash
git add .
git commit -m "YOUR-CHANGE"
git push
```
Next, follow the steps from
[Cloudflare Pages](https://pages.cloudflare.com/).

And this is how I published my blog!!





