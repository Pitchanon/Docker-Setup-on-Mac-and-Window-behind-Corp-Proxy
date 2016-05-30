# Docker Setup on Mac behind Corp Proxy

Configure your docker VM with your proxy settings

```
$ docker-machine ssh default
$ sudo vi /var/lib/boot2docker/profile
```

```
                        ##         .
                  ## ## ##        ==
               ## ## ## ## ##    ===
           /"""""""""""""""""\___/ ===
      ~~~ {~~ ~~~~ ~~~ ~~~~ ~~~ ~ /  ===- ~~~
           \______ o           __/
             \    \         __/
              \____\_______/
 _                 _   ____     _            _
| |__   ___   ___ | |_|___ \ __| | ___   ___| | _____ _ __
| '_ \ / _ \ / _ \| __| __) / _` |/ _ \ / __| |/ / _ \ '__|
| |_) | (_) | (_) | |_ / __/ (_| | (_) | (__|   <  __/ |
|_.__/ \___/ \___/ \__|_____\__,_|\___/ \___|_|\_\___|_|
```

Now paste in your proxy settings.

```
export "HTTP_PROXY=http://{your.proxy.name}:{PORT}"
export "HTTPS_PROXY=http://{your.proxy.name}:{PORT}"
export "NO_PROXY="
```

Example:
```
export "HTTP_PROXY=http://10.0.0.15:80"
export "HTTPS_PROXY=http://10.0.0.15:80"
export "NO_PROXY="
```

Now exit out of your Docker Machine VM and restart it so the new proxy settings can take affect.

```
$ exit
$ docker-machine restart default
```

```
$ eval $(docker-machine env default)
```
