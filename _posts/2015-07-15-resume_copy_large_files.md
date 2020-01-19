# Resumable copy of large files

In case you have a spotty internet connection, you can use [rsync](https://en.wikipedia.org/wiki/Rsync) to
copy files to/from a remote host.

If your connection drops in the middle of the transfer, you can just re-run the command and it will pick
up where it left off.

## local --> remote
```bash
$ rsync –partial –progress –rsh=ssh $local_file $user@$host:$destination_file
```

## local <-- remote
```bash
$ rsync –partial –progress –rsh=ssh $user@$host:$remote_file $local_file
```
