## Image for exporting SSH keys 

Use this image to create a volume that can be used by other docker containers
for ssh. 

```bash
# build the image yourself
sudo docker build -t ezhaar/keys-host .

# run the container
sudo docker run --name keys_host ezhaar/keys-host

# use the ssh keys in another container e.g hadoop container
sudo docker run -it \
    --volumes-from keys_host \
    --name htest \
    -h master.localdomain \
    --dns-search=localdomain \
    ezhaar/hadoop-2.4.0

```
