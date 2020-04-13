# SSH Tunneling

The meaning of the parts in the `-L` arg:

> local_port:remote_host:remote_port


```
ssh $user@$remote_host -L 8080:$remote_host:8000 -N
```

The above will reroute port 8080 on the local host to port 8000 on `$remote_host` over
the `ssh` connection.
