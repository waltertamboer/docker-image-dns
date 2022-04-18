# docker-image-dns

A Docker image that can be used to setup DNS using Docker.

## Run

Find the gateway IP address:

```
GATEWAY=$(ip -4 addr show docker0 | grep -oP '(?<=inet\s)\d+(\.\d+){3}')
echo ${GATEWAY}
```

Now run the Docker image:

```
docker run -d --name docker-dns \
  --restart always \
  --net host \
  -e GATEWAY=$GATEWAY \
  --log-opt "max-size=10m" \
  --volume /:/host \
  --volume /var/run/docker.sock:/var/run/docker.sock \
  ghcr.io/waltertamboer/docker-dns:latest
```

## Credits

This Docker image is heavily based on https://github.com/jderusse/docker-dns-gen
Since that repository is no longer maintained, I created this repository.
