# Static Websites and Community Documentation: Samvera Connect 2018

This repository contains presentation materials and exercise files for an introductory workshop on using [Jekyll](https://jekyllrb.com/) for digital libraries projects.

Jekyll is Ruby gem that uses plain-text files to generate HTML. Instead of using a web-based content management system, you interact with the plain-text files with a text editor and run `build` and `serve` commands with your computer terminal to make updates to the site. In this context, we'll be using GitHub to store our plain text files and the GitHub Pages service to host our websites.

In this workshop, we will be following an example use case. We will be building a conference website for a collection of presentations we're storing in our [Samvera repository](https://nurax-dev.curationexperts.com/).

**Prerequisites**: You will need to have Jekyll and all of its dependencies installed on your computer. Follow [these instructions](https://jekyllrb.com/docs/installation/) for tips based on your operating system. You will also need a text editor, git client (optional), and some familiarity with a computer terminal.

We will be using the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) theme to build our conference website. Feel free to refer to the [theme's documentation](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/) to try out some layout options and features or view examples of how the theme can be used.  

## Using the Exercise Files

We'll start by creating a local copy of the files to your computer. Clone or download the .zip of this code repository to your computer and open the file directory using a terminal. Navigate to the `example` directory (`cd example`). All of the Jekyll files for the website are contained in the `example` folder.

Terminal example that is open to the Jekyll project files:
```
user:/mnt/c/user/Desktop/samvera-staticweb/example $
```

In addition to the files, you'll need a few more Ruby gems to use practice theme. To install the additional dependencies, run `bundle update`. If you get an error, then you might not have [Bundler](https://bundler.io/) installed, so run `sudo gem install bundler` and try again.

To make sure the site's dependencies are properly installed, run `bundle exec jekyll serve` in your terminal. This will build a local copy of the website on your computer and make it available on a local server. To see the site in action, open a web browser to http://localhost:4000/ to preview the site.

**Some common commands for your reference**
- `bundle exec jekyll serve` starts Jekyll's built-in server for you to preview your site locally
- `bundle exec jekyll build` processes the files and outputs HTML/CSS to the `_site` directory. It is this directory that gets used when deploying to GitHub Pages.

## Exercise 1

*Customize the website*

All of the site's configurations are contained in the `_config.yml` file with your text editor. Open up the `_config.yml` file and start adding in your own information (feel free to ignore any fields you don't plan on using).

1. Edit the following fiels in the `_config.yml` file:
    - title
    - name
    - description
    - site author section
    - minimal_mistakes_skin
2. Save your changes
3. Start the preview server from the terminal: `bundle exec jekyll serve`
4. Preview the site with a web browser: http://localhost:4000/

If you are previewing the site in your web browser, you won't see any of the changes you made to the `_config.yml` file until you restart the server (i.e. `bundle exec jekyll serve`).

## Exercise 2

*Link a repository collection to the Jekyll website*

In this exercise, we'll use the Jekyll site as a separate front-end to collection of materials in a Samvera repository. This will give users and stakeholders of the repository's collection more options when presenting their content to the world, without the need to alter or enhance the repository's user interface.

We'll imagine that conference presenters uploaded their presentations to the repository, which were then organized in a [collection](https://nurax-dev.curationexperts.com/collections/z603qx59p). The collection contains two papers and two posters. I have already created Markdown files for the papers in the Jekyll site, which are contained in the `_papers` directory.

Open up one of the files (either `diaz.md` or `myers.md`). The file begins with YAML front-matter marked by `---` at the beginning and end of the YAML text. The YAML serves as the paper's metadata. A professional scholarly publication might have a lot more metadata, such as: `doi:`, `author_affiliation:`, `orcid:`, `date:`, etc. The rest of the document is the body of the paper, formatted in [Markdown](https://commonmark.org/help/). When you are previewing the site, you can view the HTML versions of these papers from the presentations listing: http://localhost:4000/presentations/

Right now, the website is not linked to the repository, so let's fix that.

1. Go to the example [repository collection](https://nurax-dev.curationexperts.com/collections/z603qx59p)
2. Copy the URL for both of the papers
3. Go to the Markdown files for the corresponding papers in the Jekyll site
4. Add a YAML field at the top of the `.md` files called `download_url:` and add the URLs as the value
5. Open the `paper.html` layout from the `_layouts` directory in the Jekyll site
6. Edit the Button HTML element: `<a href="#" class="btn btn--primary">Download</a>`
7. Swap `href="#"` with `href="{{ page.download_url }}"`
8. Save the changes to the `paper.html` file
9. Run `bundle exec jekyll serve` to preview your changes

In steps 1-4, you added a new metadata field for the location of the repository version for each paper on the Jekyll site. This will be applied to every Markdown file that uses the `paper.html` layout (currently, that would be every `.md` file in the `_papers` directory). In steps 5-8, you used the Liquid templating language to tell Jekyll to insert the YAML metadata into that particular HTML element. When Jekyll applies the HTML layout to the Markdown file, it will look for the repository URL for each paper and add it to the button element for every paper on the Jekyll website. To test, visit the Jekyll version of either paper, and click on the `Download` button. If you're directed to the repository record of the paper, then it worked!

## Exercise 3

*Let's publish more content*

We also have some posters to add to the website. For the purposes of this exercise, we will create a new directory for the posters using Jekyll's [collections features](https://mmistakes.github.io/minimal-mistakes/docs/collections/). This will give us the flexibility to create a new layout and organize our site's contents by content type.

Open up the `_config.yml` file with your text editor and add the `collections` configurations according to the theme's documentation and save the file. Hint: look at how the `Papers` collection is set up in file and use it as a guide. Notice that the defaults section of the `_config.yml` file allows you to reuse YAML metadata across your entire collection more easily. For example, we will want to have a Table of Contents for our papers and reuse the same layout for all of them, but we we'll want a _different_ layout _without_ a Table of Contents for our posters.

Here's how you'll want to format your `papers` defaults:

```
defaults:
  # _posters
  - scope:
      path: ""
      type: posters
    values:
      layout: poster
      author_profile: false
      share: true
      research: true
```

Next, you'll need to create a new directory called `_posters` to store all of your Markdown files for your posters. Create some Markdown files for the posters in the new `_posters` directory. Use the repository record and the poster itself to determine some metadata to include this front-matter:

```
---
title:
author:
abstract:
---
```

The posters come from Figshare, which has embed code for their image viewer. Let's use the embed code from Figshare as header images for the posters on the site.

Links to the posters in Figshare:
- [Mobilizing...](https://doi.org/10.23645/epacomptox.6626579.v1)
- [An evaluation...](https://doi.org/10.23645/epacomptox.6743762.v1)

Copy the embed code and paste it in the body of the Markdown document for the poster (i.e. below the `---` under the font-matter).

Some additional modifications to the FigShare embed code:

- Change the width value to `width="100%"`
- Change the height value to `height="600"`

```
<iframe src="https://widgets.figshare.com/articles/6626579/embed?show_title=1" width="100%" height="600" frameborder="0"></iframe>
```
Save the Markdown files and preview the changes: `bundle exec jekyll serve`

## Exercise 4

*Deploy your site*

The last step will be to deploy your site to [GitHub Pages](https://pages.github.com/). This service is free for public GitHub repositories and will make your site publicly available online.

GitHub Pages uses three methods for deploying static websites:
- From the `Master` branch
- From a `/docs` folder
- From a `gh-pages` branch

We will be using the `/docs` method. To do this, we'll need to configure a publishing directory for our website. Jekyll uses a default directory called `_site` but we can change this in the configurations (i.e. `_config.yml`).

- Open the `_config.yml` file
- Add `destination: "../docs"`
- Run `bundle exec jekyll build`
- Push your changes to GitHub
- In GitHub, go to your repository settings
- Scroll down to GitHub Pages
- Change your source to `master branch / docs folder`
- Save your changes

Your site should be live at `username.github.io/samvera-staticweb` within a few minutes.
