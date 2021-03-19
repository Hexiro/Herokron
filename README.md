## Herokron


Herokron is a python package used to make switching [Heroku](https://heroku.com/) apps on/off easy, especially between accounts. The primary use case is from the command line in the form of a cron job (hence the ending *kron*), but Herokron does work in a python file. Optionally, all on/off state changes called from the command line are logged in a discord server by a webhook.

![Forks](https://img.shields.io/github/forks/Hexiro/Herokron)
![Stars](https://img.shields.io/github/stars/Hexiro/Herokron)
![Issues](https://img.shields.io/github/issues/Hexiro/Herokron)
![License](https://img.shields.io/github/license/Hexiro/Herokron)

![Herokron Webhook Example](https://i.imgur.com/42O2mbP.png)


## 📦 Installation

Install the package with pip.

```
pip3 install git+https://github.com/Hexiro/Herokron
```


## 💾 Setup

Load all the keys you have, there is no limit.
```console
$ Herokron --add-key {key} 
$ Herokron --set-webhook {discord_webhook}
$ Herokron --set-color {discord_embed_color}
```
View the database to make sure everything is working.
```console
$ Herokron -database
```

## 📝 Usage
```python
# Changes state of Heroku app to `on`.
Herokron -on [app] # command line
Herokron.on(app) # .py
>>> {"changed": bool, "online": bool, "app": str}
```
```Python
# Changes state of Heroku app to `off`.
Herokron -off [app] # command line
Herokron.off(app) # .py
>>> {"changed": bool, "online": bool, "app": str}
```

```Python
# Returns the current state of the Heroku app.
Herokron - status[app]  # command line
Herokron.status(app)  # .py
>> > {"online": bool, "app": ""}
```
```Python
# Returns the local database pretty printed.
Herokron -database # command line
```

# ⌛ Cron
The following example will start a Heroku app everyday at 8 am.

### crontab
```
0 8 * * * herokron -on [app]
```

If this isn't working, cron is most likely just having issues finding Herokron. If this happens, you will need to specify the Herokron path. 

### command line
```
$ which herokron
/home/pi/.local/bin/herokron
```
### crontab
```
0 8 * * * /home/pi/.local/bin/herokron -on [app]
```


# Contributing
Pull requests are always 100% welcomed and appreciated. Right now, I have no way of Testing Mac OS and other Linux distributions. All modern operating systems should work. Operation system is only used to find the local database file. 