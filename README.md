# Static Websites and Community Documentation: Samvera Connect 2018

This repository contains presentation materials and exercise files for an introductory workshop on using [Jekyll](https://jekyllrb.com/) for digital libraries projects and maintaining [Samvera's community documentation](http://samvera.github.io/).

Workshop Use Case: We will be building a conference website for a collection of posters and papers we're storing in our Samvera repository.

Prerequisites: You will need to have Jekyll installed on your computer. Follow [these instructions](https://jekyllrb.com/docs/installation/) for tips based on your operating system.

We will be using the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) theme to build our conference website. Feel free to refer to the theme's documentation to try out some layout options and features or view examples of how the theme can be used.  

To get started, clone this repository to your computer and open it with a terminal. Navigate to the `example` directory (`cd example`). All of the Jekyll files for the website are contained in the `example` folder. Run `bundle update` to install the websites dependencies. If you get an error, then you might not have [Bundler](https://bundler.io/) installed, so run `gem install bundler` and try again.

To make sure the site's dependencies are properly installed, run `bundle exec jekyll serve` and open a web browser to http://localhost:4000/ to preview the site.
