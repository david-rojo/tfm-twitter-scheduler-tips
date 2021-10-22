# Run app container with docker

```
docker run --name twitter-scheduler -p 8080:8080 -it --rm drojo/twitter-scheduler:0.0.1-SNAPSHOT
```

Arguments used:

--name: name of the container

-p: expose specified port of the container

-it: instructs Docker to allocate a pseudo-TTY connected to the container’s stdin; creating an interactive bash shell in the container

--rm: delete the container immediately after it exits