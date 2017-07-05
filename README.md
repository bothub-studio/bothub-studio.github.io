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
