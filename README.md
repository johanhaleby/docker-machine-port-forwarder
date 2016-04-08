# Docker Machine Port Forwarding

A small bash script that makes it easier to expose ports between VirtualBox and the host when using [docker-machine](https://docs.docker.com/machine/) on Mac OSX.

## Usage

	$ pf 8080

Forwards port 8080 in the container to port 8080 on the host in docker-machine environment `default` by opening an SSH connection to VirtualBox in the background.

If you run into this error:

```bash
Host does not exist: "default"
```

you'll need to specify the name of your docker-machine environment. For example:

	$ pf 8080 -e dev

This will use the `dev` docker-machine environment.

### Stopping the port forwarding

If you've started port forwarding in the background (default) you can easily stop it using:

	$ pf 8080 -s

Note that you don't need to specify an environment (`-e`) for this to work.

### Port Mapping

You can map the docker port to another port on the host like this:

	$ pf 8090:8080

This will map port 8090 on the host to port 8080 running in the container.

### Foreground

You can also start the port forwarding process in the foreground:

	$ pf 8080 -f

If you do this you'll see the docker-machine and once it's shutdown the port forwarding is also stopped automatically (i.e. no need to run `pf <port> -s`).

### Help

Run `pf -h` to for more options

### Advanced

If you need more advanced options just use the vanilla `docker-machine` command. The purpose of `pf` is to make it really easy to do the most basic things.