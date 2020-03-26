# Add remote Porteiner Agent

## Sumary

- Enable DOKER Api communication

## 1 - Enable DOKER Api communication.

### Insecure way:
Just enable external comunication to dockerd:

Edit `sudo vi /lib/systemd/system/docker.service` and add `-H=tcp://0.0.0.0:2375` at the end of `ExecStart`.

```bash
#/lib/systemd/system/docker.service
- ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
+ ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock -H=tcp://0.0.0.0:2375
```

Then run `sudo systemctl daemon-reload` to reload configurations.
The last step is to restart docker to apply confs: `sudo service docker restart`.

*Impottant!!! Remember to open Docker API port `275` or any other that was used in the configuration step.*

### Secure way
View: [Protect the Docker daemon socket](https://docs.docker.com/engine/security/https/)

## 2 - Enable DOKER Api communication.
 
 Add endpoint to Portainer


REFERENCES:

[Protect the Docker daemon socket](https://docs.docker.com/engine/security/https/)
