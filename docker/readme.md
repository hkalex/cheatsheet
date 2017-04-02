# Docker cheatsheet

## Run command
```
# --name is mandatory, or the name will be random!!!
# -d run in background
# --rm can remove the contains immediate after stop
# --volume "rw" read and write mode
# links to another docker container by name in the same machine

sudo docker run \
  -d \
  --restart=always \
  --publish=$PORT:$PORT \
  --volume=$DIR/bundle:/bundle/bundle \
  --volume=$DIR/kicker.sh:/bundle/kicker.sh \
  --volume=$DIR/settings.json:/bundle/settings.json \
  --volume=cfsvolume:/bundle/cfs:rw \
  --volume=$DATADIR/temp:/temp:rw \
  --env-file=$DIR/env.list \
  --link=mongodb \ 
  --name=$APPNAME \
  --hostname=$APPNAME \
  $IMAGENAME \
  bash /bundle/kicker.sh
```

## SSH Volume
```
# install the plugin
sudo docker plugin install vieux/sshfs

# create the volume
sudo docker volume create -d \
  vieux/sshfs \
  -o sshcmd=shared@<IP>:/opt/data/cfs \
  -o password=<Password> \
  cfsvolume
```

