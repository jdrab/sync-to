### sync-to
It's just a simple wrapper for rsync with configuration support.
It might be usefull if you're very often syncing files to remote server 
and don't want to remember the path on the server. 
Configuration is saved in .sync_to file in actual directory

#### How might this be usefull for you?
If you need to 'rsync' your files from ~/Your/Dir to whatever@remote-server:/some/weird/path and you're too lazy to write full paths or just don't use bash 'search in history' ctrl+r.

#### .sync_to file syntax
remote-hostname:username-can-be-ommited:remote-path

example .sync_to
```sh
workstation1::/home/w1user/Work/weird/path
host7::~/rpmbuild/SPECS
host8:userX:~/backup/specs
```
Now imagine you need to sometime sync your files to remote 'host7'
```sh
cortex@workstation:~/Projects/spec-files $  sync-to host7
```
In this case, sync-to will look for 'host7' configuration in .sync_to config.
It will sync files as logged in user to host7 to my $HOME into rpmbuild/SPECS directory.
```sh
cortex@workstation:~/Projects/spec-files $  sync-to host8
```
In this case sync-to will use config line for host8 and sync files to this host as userX to directory ~/backup/specs

#### How to 'install' it?
Just copy or symlink it to your $PATH.
I use it as a symlink from git repository

```sh
export PATH=$PATH:$HOME/bin
```

#### notes
- It might be a good idea to put .sync_to into your .gitignore for some projects
