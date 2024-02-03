+++
title = 'New Hugo blog'
date = 2024-01-07T14:14:31-05:00
draft = false
+++

Hello there, my first posts on this blog will be how I created the blog using Hugo.  
Below are the step to initiate the blog.

## Official documentation

Here the [link](https://gohugo.io/getting-started/quick-start) to the quick start to create a blog with Hugo.

## Custom theme

First of all, to display something in Hugo you need a theme.
I don't want to reuse an existing theme but learn how to create one by doing my own blog.
So first let's create a custom blog theme!

* Open a command line tool
* Go in a folder where you want to create your theme
* Execute the following command 
  `hugo new theme .`  
  A **themes** folder will be created containing all the elements for a fresh theme
* *Optional : rename the folder with your theme name*
* If you don't want default content in your theme, remove the sub folder **content**
* Initialize a git repository inside the theme (at the README level) and publish your repository  
  ```
  git init
  git remote add origin ...
  git add .
  git commit -m 'init'
  git push ...
  ```

## New site

We now have a custom theme available, let's use it in our blog!

* In a command line tool
* Go in a folder where you want to create your blog sources
* Execute the following command 
  `hugo new site mysite`  
  A **mysite** folder will be created containing all the elements for a new site, except the theme
* Move inside the **mysite** folder
* Init git  
  `git init`
* Add the theme with the following command  
  `git submodule add THEME_REPOSITORY_URL themes/THEME_NAME`  
  where we replace THEME_REPOSITORY_URL and THEME_NAME by their value, example :  
  `git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke`
* Add theme in the **hugo.toml** file by adding  
  `theme = 'THEME_NAME'`

## Test it locally

The site is ready, let's test it!

* In a command line tool
* Go in the blog folder and execute  
  `hugo server --buildDrafts`

## Add a first post

While the `hugo server` command run, we can create new content and have a fast feedback on what we create.

* Open another command line tool
* Go in the blog folder
* Create the folder **posts** in **content**
* Then from from the source root, create a new post with the command  
  `hugo new content posts/first-post.md`  
  *Do not forget the filename extension!*  
  The post should be visible in the local web site

## Publish a post

By default the created contents is in draft status. When your content is ready set the draft property to false in order to to have it visible in the production build (without *--buildDrafts*).

Set the first post draft property to false then run hugo server without *--buildDrafts* to check the post is visible.

## Host it on Github

To start hosting the blog, the easier is to use [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site).

* In a command line tool
* Go in a folder where you want to create your blog sources
* Run the following command to generate the static files in the **docs** folder  
  `hugo -d docs`
* Commit files in the *mysite* repository and push the changes in Github
* Connect to Github and open the settings of the *mysite* repository
* In the left menu access the **Pages** item
* Source : keep *Deploy from branch*  
  Select the **main** branch and the **docs** folder
* Save and refresh the page  
  The link of the site should be visible now

We will explain how to host it in a custom domain and on something else in a later post.

*Remark: if your repository is not the **<user>.github.io** repository, you may need to change the **baseURL** property in **hugo.toml** in order to the links to work correctly.*
