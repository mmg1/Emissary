# Emissary
Send notifications via different channels such as Slack, Telegram, Discord etc.

## Motivation
The idea is to hook Emissary into https://github.com/BountyStrike/Bountystrike-sh which will notify me on Telegram when new domains have been found.

## Usage

```
$ emissary
Send data through chat channels. Made by @dubs3c.

Usage:
  emissary [channel] [message]

Options:
  -s,  --slack        Send via Slack
  -t,  --telegram     Send via Telegram
  -e,  --email        Send via Email
  -si, --stdin        Get message from stdin
  -m,  --message      Message to send
  -v,  --version      Show version

Examples:
  emissary -telegram --message "Hello telegram"
  cat domins.txt | emissary --slack --stdin
```

**Create emissary.ini in the same location as the executable:**
```
[Telegram]
chat_id=xxxxxx
api_key=xxxxxxx:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

[Slack]
webhook=https://hooks.slack.com/services/xxxxxxxxxx/xxxxxxxxxx/xxxxxxxxxx

[Email]
username=
password=
recipient=
server=smtp.gmail.com
port=587
subject="New domains found!"
```

*When using gmail, you need to activate less secure apps on your account: [https://myaccount.google.com/lesssecureapps](https://myaccount.google.com/lesssecureapps)*

Now you can start using emissary :)

**Pipe data via stdin:**
```
$ cat domains.txt | emissary --telegram --stdin
```

**Specify a message as an argument:**
```
$ emissary --telegram --message "This is a very cool message"
```

**Send to multiple channels:**
```
$ cat domains.txt | emissary -t -s -si
```

Right now the Emissary will only deliver 20 rows, to protect against accidentally sending a gazillion domains :) 

## Todo
Some stuff that I plan to implement:
- [X] Slack
- [X] Telegram
- [ ] Discord
- [ ] Email
- [ ] Let user decide max rows to be sent
- [ ] Place config file in ~/.config/emissary.ini

## Contributing
Any feedback or ideas are welcome! Want to improve something? Create a pull request!

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D