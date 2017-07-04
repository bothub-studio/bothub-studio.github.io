# BotHub CLI

This package provides a command line interface to BotHub.Studio service.

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
  clone      Clone existing project
  configure  Setup credentials
  deploy     Deploy project
  init       Initialize project
  logs       Show error logs
  ls         List projects
  nlu        Manage project NLU integrations
  property   Manage project properties
  rm         Delete a project
  test       Run test chat session
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

Clone an existing project.

```sh
$ bothub clone <project-name>
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

Show error logs.

```sh
$ bothub logs
```

Run current project on local machine for test.

```sh
$ bothub test
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

### NLU management

List of NLU integration for current project.

```sh
$ bothub nlu ls
```

Add a NLU integration for current project.

```sh
$ bothub nlu add apiai --api-key=<api-key>
```

Remove a NLU integration from current project.

```sh
$ bothub nlu rm <nlu>
```
