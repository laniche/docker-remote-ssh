# SSH Remote Access

Create a SSH tunnel to a remote host, in a Docker environment.

## Versions

_To be completed after deploy_

## Docker Compose Sample

In this example, we create a container that provides a connection  
to a remote MySQL server.

```
version: "2"
services:
  database:
    image: dogstudio/remote-ssh
    stdin_open: true
    tty: true
    ports:
      - "3306:3306"
    volumes:
      - ~/.ssh/id_rsa:/home/docker/.ssh-external/id_rsa:ro
    environment:
        - "remote_host=mysql.sample.com"
        - "remote_user=myusername"
```

* In the volumes, you must specify your key pass.
* And in environment, you must enter :
  * `remote_host` : hostname or IP to the server
  * `remote_user` : SSH username (default: `root`, LOL)
  * `remote_port` : SSH port (default: `22`)
  * `remote_service` : Port mapping for the SSH tunnel (default: `3306`)
