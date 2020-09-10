# Simple Site
testing procedure for spinning up a plain, new jekyll site for dummies (like me)

## Basic installation
Note to future self. Here's what I did:
1. Create repo on github
  - Add readme and jekyll flavor of .gitignore
1. Create gem file locally by running `bundle init`.
1. Add the Github pages gem:
  ```
  Add the following in the gemfile (replacing the existing contents):
  source 'https://rubygems.org'
  gem 'github-pages'
```
1. Run `bundle install` to get all the necessary things.
1. Add a blank `_config.yml` file.
  - Not totally necessary at this point, as GH pages will just use defaults, but will probably use later and gets rid of warning message during build.

At this point, you have a basic jekyll site (with no theme) that will build locally and automatically as a Github pages site.

## Adding a CSS framework
I thought I wanted to install USWDS using npm, but that was too complicated for me.

Instead, I leveraged the built-in sass compiler of Jekyll like so:
1. Download the latest USWDS zip file and unzip.
1. Move files to (site root)/assets/uswds-2.8.1.
1. Update SASS Directory setting in `_config.yml` to look in the right place for the USWDS files:
~~~
sass:
  sass_dir: assets/uswds-2.8.1/scss
~~~
1. Create a "placeholder" *SCSS* file for the compiled SASS to be copied to.
  - Create `(site root)/assets/css` folder and add `main.css`.
  - When the site builds, it will create a *CSS* file in the same location.
1. Add an import statement to the target SCSS file:
  - Note: it must include the "front matter" dashes at the top so the compiler knows what to do with it:

~~~
---
---
@import "uswds";
~~~

6. Copy the fonts folder to the assets folder so the built site can reference them.
1. Add some theme files into the mix so you can start to customize things.

~~~
---
---
@import "theme/uswds-theme-color";
@import "uswds";
~~~

8. Start adding some utility classes to the markdown:
~~~
[This is a link to nowhere.](#){: .usa-link}
~~~
