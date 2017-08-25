## Installation

Requirement: Ruby installed

```sh
$ git clone --origin gitlab git@gitlab.com:bothub-studio/bothub-website.git
$ git remote add origin git@github.com:bothub-studio/bothub-studio.github.io.git
$ gem install bundle
$ bundle install
```

Run dev server

```sh
$ middleman server
```

Deploy to GitHub pages

```sh
$ middleman deploy
```


## Attributes

Front-matter attributes

 * title: Page title
 * description: Page description
 * cover_image: OpenGraph cover image URL
 * cover_image_width: image width
 * cover_image_height: image height
 * isFront: is this a front page?

Data elements

 * botstore.yml: contains chatbot list
 * docs.yml: contains table of contents of docs page
 * sitemap.yml: URL prefix
