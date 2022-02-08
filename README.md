# Northstar server Parseable Logs

This mod adds a bunch of logs to Northstar servers. The logs output in JSON format, to allow for easily parsing them with external tools.

## companion python library

I made a companion python library that parses these logs and provides callbacks for handling events logged by this mod:

Check it out here: https://github.com/laundmo/northstar-parseable-logs-lib

## Log format

A log line might look like this:

```
[20:42:14] [info] [SERVER SCRIPT] [ParseableLog]{"subject":{"type":"player","name":"laundmo","playerIndex":0,"teamId":3,"uid":"1006865660022","ping":196685,"kills":0,"deaths":0,"alive":false},"verb":"existing"}
```

The logs take a subject-verb or subject-verb-object structure. The subject is any thing which happens to do something, the verb is what it does, and the object what it does it to.

In the example line, i had set the `parsable_player_interval` convar to `10`, meaning every player is logged with the verb `existing` every 10 seconds. Without this, logs only happen when certain events happen.

Currently logged events:

- client connecting
- client connected
- client disconnected
- player respawned
- player killed
- round ended
- game state changed

## Config

This mod defines one config variable, `parsable_player_interval` in seconds. Its used to periodically log all players. default `0` (disabled)
