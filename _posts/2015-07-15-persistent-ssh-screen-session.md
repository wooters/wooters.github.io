# Create a persistent ssh connection to a screen session

(Install `autossh` via homebrew)

```
autossh -M50000 -t server.example.com 'screen -raAd mysession'
```
