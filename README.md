# Static Websites and Community Documentation: Samvera Connect 2018

This repository contains presentation materials and exercise files for an introductory workshop on using [Jekyll](https://jekyllrb.com/) for digital libraries projects and maintaining [Samvera's community documentation](http://samvera.github.io/).

In this workshop, we will be following an example use case. We will be building a conference website for a collection of presentations we're storing in our Samvera repository.

Prerequisites: You will need to have Jekyll and all of its dependencies installed on your computer. Follow [these instructions](https://jekyllrb.com/docs/installation/) for tips based on your operating system. You will also need a text editor, git client (optional), and some familiar with a computer terminal.

We will be using the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) theme to build our conference website. Feel free to refer to the [theme's documentation](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/) to try out some layout options and features or view examples of how the theme can be used.  

## Getting started

Clone this repository to your computer and open it with a terminal. Navigate to the `example` directory (`cd example`). All of the Jekyll files for the website are contained in the `example` folder. Run `bundle update` to install the websites dependencies. If you get an error, then you might not have [Bundler](https://bundler.io/) installed, so run `gem install bundler` and try again.

To make sure the site's dependencies are properly installed, run `bundle exec jekyll serve` and open a web browser to http://localhost:4000/ to preview the site.

**Some common commands**
- `bundle exec jekyll serve` starts Jekyll's built-in server for you to preview your site locally
- `bundle exec jekyll build` processes the files and outputs HTML/CSS to the `_site` directory. It is this directory that gets used when deploying to GitHub Pages.

## Setting up your site

All of the site's configurations are contained in the `_config.yml` file. Open up the `_config.yml` file and start adding in your own information (feel free to ignore any fields you don't plan on using). If you are previewing the site, you won't see any changes you make to the `_config.yml` file until you restart the server (i.e. `bundle exec jekyll serve`).

Go ahead and start editing the configurations:
- title
- name
- description
- site author section

**Activity 1**: Change the [theme's skin](https://mmistakes.github.io/minimal-mistakes/docs/configuration/).
**Activity 2**: Enable Jekyll's [collections features](https://mmistakes.github.io/minimal-mistakes/docs/collections/) to begin working with different content types.

## Content

*Publish a new submission*

## Metadata

*Organize submissions by tag*

## Layouts

*Use different layouts for papers and posters*

## Deployment

*Deploy your site to GitHub Pages*

## Acknowledgements
