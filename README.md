[Winston](https://github.com/winstonjs/winston) Transport for
[Slack](https://slack.com/) chat integration.

    npm install --save winston-slack-transport

Basic transport that works just like all other winston transports. Sends logged
messages to a specified Slack chat channel.

Configuration options:

 * `webhook_url`: **required** The webhook URL, something like
   `https://hooks.slack.com/services/XXXXXXXXX/YYYYYYYYY/ZZZZZZZZZZZZZZZZZZZZZZZZ`
 * `token`: **required for new postMessage api endpoint**
 * `level`: If specified, this logger will only log messages at the specified
   level of importance and more important messages
 * `custom_formatter`: a `function (level, msg, meta)` which returns a Slack
   payload object

Additionally, you can specify any Slack message parameters (such as `username`
and `channel`), and it will be applied as a fallback if the given argument is
not specified per message.

---

    var winston = require('winston');
    var Slack = require('winston-slack-transport');

    winston.add(Slack, {
        webhook_url: "https://slack.com/api/chat.postMessage",
        token: "xoxb-xxxxxxxxxx",
        channel: "#test-channel",
        username: "ErrorBot",
        level: "error",
        handleExceptions: true
    });
