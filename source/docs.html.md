---
title: Documentation - BotHub.Studio
toc:
  - id: why-bothub-studio
    title: Why BotHub Studio?
  - id: installation
    title: Installation
  - id: getting-started
    title: Getting Started
  - id: usage
    title: Usage
---

Hello! Welcome to BotHub.Studio's developer documentation!

BotHub.Studio is a backend platform for chatbot deployment and management. Our goal is to help developers to focus on their own logic not on engineering issues.

## Why BotHub Studio?

### Take Code Ownership

There are meny services already on chatbot service ecosystem.

Some of them are great, especially for UI chatbot builder even non-developer can build a chatbot with case.

But we are developers. We can't bear our efforts are melted into someone's service UI, which can't be expressed in the form of code, be stored to GitHub. Moreover, sometimes we want a flexibility to use other tools the service doesn't provide yet.

We don't have a enough time and money to make whole part of chatbot by our own hands. So we search some tools or frameworks can help us. And we also want to have ownership of most important part.

BotHub.Studio helps us to deploy and run our own code. They only supports backend service. I can own important core of my chatbot and control it.


### Backend Free

There are many 'Make a chatbot in 10 minutes' stuffs today. Even BotHub.Studio says that too.

But, getting more traction, you need to solve many hard engineering problems.

1. You should handle increasing throughput
1. Send massive messages to messenger platform efficiently to keep reasonable responsiveness
1. Sometimes message orders messed up
1. Someday you need a scheduler
1. Someday you need a database. Moreover each users need their own persistent storage
1. You need a deployment automation to eliminate SPOF to improve a reliability
1. Someday you need a logging system
1. ... And statistics, and analytics based on that

You need a skilled backend software engineer to solve these tough issues. Hiring this kind of engineer is not so easy with a limited budget.

Imagine this, many backend software engineers all over the world solves same issues in their own company. How inefficient it is. You can use your energy to solve better, more important, more productive issues.

BotHub.Studio is operated by senior backend engineers, we improve a backend of BotHub.Studio by everyday. We only charges only a dozens of dollars per month. It's much like a supporting open source project. You pay tens of dollars per month, we can build a more robust backend, so everyone can enjoy the platform.


### Start Lean

We offers elastic pricing plans.

Start with a Start Plan. With it, you can build up to 5 chatbots, 50k interactions per month. Always with BotHub.Studio advertisement.

When you build a serious chatbots, take Pro Plan. With tens of dollars, you can build unlimited chatbots, usage based pricing. You can earn profit with advertisement.


### Monetization

You may have or have not a monetization plan. BotHub.Studio helps you to earn profit with advertisement with ease. Just embed a ad code.

## Installation

`bothub-cli` is an unified tool to manage your chatbot project.

To install `bothub-cli` on `virtualenv`:

```sh
$ pip install bothub-cli
```

or, if you are not work on `virtualenv`:

```sh
$ sudo pip install bothub-cli
```

The `bothub-cli` package works on python2 and 3 both.


## Getting Started

Before using `bothub-cli`, you need to tell it about your BotHub.Studio credentials.

```sh
$ bothub configure
Username: myuser
Password: mysecret
```

Then it stores access token on `~/.bothub` directory.

To start build a new chatbot:

```sh
$ mkdir mybot
$ cd mybot
$ bothub init
Project name: mybot
```

Now you have a starter echo bot running on BotHub.Studio server:

```
.
|-- bothub
|  |--bot.py
|  `--__init__.py
|-- bothub.yml
|-- requirements.txt
`-- tests
```

You need to configure channel to use.

```sh
$ bothub channel add telegram --api-key=<my-api-key>
$ bothub channel add facebook --app-id=<app-id> --app-secret=<app-secret> --page-access-token=<page-access-token>
```

Now, try talk to your chatbot.

Modify `bot.py` for your purpose.

```python
# -*- coding: utf-8 -*-

from bothub_client.bot import BaseBot
from bothub_client.messages import Message

class Bot(BaseBot):
"""Represent a Bot logic which interacts with a user.

BaseBot superclass have methods belows:

* Send message
  * self.send_message(message, chat_id=None, channel=None)
* Data Storage
  * self.set_project_data(data)
  * self.get_project_data()
  * self.set_user_data(data, user_id=None, channel=None)
  * self.get_user_data(user_id=None, channel=None)

When you omit user_id and channel argument, it regarded as a user
who triggered a bot.
"""
  def handle_message(self, event, context):
    message = Message(event).set_text('You says: {}'.format(event['content']))\
                            .add_quick_reply('Yes')\
                            .add_quick_reply('No')
    self.send_message(message)
```

and deploy it.

```sh
$ bothub deploy
```

## Usage

```sh
Usage: bothub [OPTIONS] COMMAND [ARGS]...

Bothub is a command line tool that configure, init, and deploy bot codes
to BotHub.Studio service

Options:
  --help  Show this message and exit.

Commands:
  channel    Setup channels of current project
  configure  Setup credentials
  deploy     Deploy project
  init       Initialize project
  ls         List projects
  rm         Delete a project
```

### Setup

Authorize an user and get access token.

```sh
$ bothub configure
```

### Project management

Initialize project on current directory. Create an initial echo chatbot.

```sh
$ bothub init
```

Deploy current project.

```sh
$ bothub deploy
```

Show project list.

```sh
$ bothub ls [-l]
```

Delete a project.

```sh
$ bothub rm <project-name>
```

### Channel management

List of channels for current project.

```sh
$ bothub channel ls
```

Add a channel for current project.

```sh
$ bothub channel add telegram --api-key=<api-key>
$ bothub channel add facebook --app-id=<app-id> --app-secret=<app-secret> --page-access-token=<page-access-token>
```

Remove a channel from current project.

```sh
$ bothub channel rm <channel-name>
```
