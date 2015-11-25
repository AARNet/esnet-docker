## perfSONAR Light docker container

The docker container runs all perfSONAR light services.
See: https://code.google.com/p/perfsonar-ps/wiki/Level1and2Install 
This can be used to run perfSONAR RPMs on a Docker capable system. 

This container is set to always run until manually stopped.

### Requirements

* docker 1.5 or later
* docker-compose ( https://docs.docker.com/compose/install/ ) 

## Build

First, edit ls_registration_daemon.conf with the information for your site.

Next, build the container (in the directory containing 'Dockerfile')

```
$ docker-compose build 
```

Run the container

```
$ docker-compose up -d
```

## Testing

test perfSONAR tools from another host with owamp and bwctl installed:

```
$ owping hostname
$ bwctl -T iperf3 -c hostname
```

##Notes:

The hostname is assume to be the same is the base host. That can be changed.
See: https://docs.docker.com/articles/networking/

## Security:
make sure the following ports are allowed by the base host:
* bwctl
 * 4823
 * 5001-5900
 * 6001-6200 
* owamp
 * 861
 * 8760-9960
* lookup service
 * 8090
 * 8096

See: http://www.perfsonar.net/deploy/security-considerations/

