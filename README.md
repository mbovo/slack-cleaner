# slack_cleaner2

[![License: MIT][mit-image]][mit-url] [![CircleCI][ci-image]][ci-url] [![PyPi][pypi-image]][pypi-url] [Read the Docs][docs-image]][docs-url]

Bulk delete messages and files on Slack.

## Install

Install from PyPi:

```bash
pip install slack_cleaner2
```

latest version
```bash
pip install -e git+https://github.com/sgratzl/slack_cleaner2.git
```

#ä Usage

In contrast to the original version this version is a pure python package only that allows for easy scripting instead of a vast amount of different command line arguments. 

basic usage

```python
from slack_cleaner2 import *

s = SlackCleaner('SECRET TOKEN')
# list of users
s.users
# list of all kind of channels
s.conversations

for msg in s.msgs(filter(match('.*-bots'), s.conversations)):
  msg.delete()
```


## Tokens

You will need to generate a Slack legacy token to use slack-cleaner. You can generate a token [here](https://api.slack.com/custom-integrations/legacy-tokens):

[https://api.slack.com/custom-integrations/legacy-tokens](https://api.slack.com/custom-integrations/legacy-tokens)



## Minimal Slack permission scopes required

- `channels:history`
- `channels:read`
- `chat:write:bot`
- `users:read`


## Tips

After the task, a backup file `slack-cleaner.<timestamp>.log` will be created in current directory if `--log` is supplied.

If any API problem occurred, try `--rate=<delay-in-seconds>` to reduce the API call rate (which by default is unlimited).

If you see the following warning from `urllib3`, consider to install missing
packages: `pip install --upgrade requests[security]` or just upgrade your Python to 2.7.9.

```
InsecurePlatformWarning: A true SSLContext object is not available.
          This prevents urllib3 from configuring SSL appropriately and may cause certain SSL connections to fail.
          For more information, see https://urllib3.readthedocs.org/en/latest/security.html#insecureplatformwarning.
```

## Credits

**To all the people who can only afford a free plan. :cry:**

[mit-image]: https://img.shields.io/badge/License-MIT-yellow.svg
[mit-url]: https://opensource.org/licenses/MIT
[ci-image]: https://circleci.com/gh/sgratzl/slack_cleaner2.svg?style=shield
[ci-url]: https://circleci.com/gh/sgratzl/slack_cleaner2
[pypi-image]: https://pypip.in/version/slack_cleaner2/badge.svg
[pypi-url]: https://pypi.python.org/pypi/slack_cleaner2/
[docs-image]: https://readthedocs.org/projects/slack_cleaner2/badge/
[docs-url]: https://readthedocs.org/projects/slack_cleaner2
