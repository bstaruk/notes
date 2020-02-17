
# [rsync](https://rsync.samba.org) examples

#### basic local sync:
```bash
rsync -hrtP /path/to/source/ /path/to/destination/
```

#### sync remote to local:
```bash
rsync -hrtP user@remote.com:/home/user/files/ /home/user/files/
```

#### sync local to remote:
```bash
rsync -hrtP /home/user/files/ user@remote.com:/home/user/files/
```

#### custom ssh port:
```bash
rsync -hrtP -e "ssh -p 4220" /home/user/files/ user@remote.com:/home/user/files/
```

##### --delete
To delete anything found in the destination, which is not found in the source, add `--delete` to the end of any command.
