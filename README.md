## Supported tags and respective `Dockerfile` links
### Luna
- [`luna-openjdk7` (*luna/openjdk7/Dockerfile*)](https://github.com/kostasns/eclipse-docker/blob/master/luna/openjdk7/Dockerfile)
- [`luna-openjdk8` (*luna/openjdk8/Dockerfile*)](https://github.com/kostasns/eclipse-docker/blob/master/luna/openjdk8/Dockerfile)
- [`luna-sunjdk7` (*luna/sunjdk7/Dockerfile*)](https://github.com/kostasns/eclipse-docker/blob/master/luna/sunjdk7/Dockerfile)
- [`luna-sunjdk8` (*luna/sunjdk8/Dockerfile*)](https://github.com/kostasns/eclipse-docker/blob/master/luna/sunjdk8/Dockerfile)

### Kepler
- [`kepler-sunjdk7` (*kepler/sunjdk7/Dockerfile*)](https://github.com/kostasns/eclipse-docker/blob/master/kepler/sunjdk7/Dockerfile)
- [`kepler-sunjdk8` (*kepler/sunjdk8/Dockerfile*)](https://github.com/kostasns/eclipse-docker/blob/master/kepler/sunjdk8/Dockerfile)

## How to use this image
### Prerequisites for running on Windows
#### Software 
- X11 Server (Tested with XMing)
- Docker toolbox __*or*__ Docker for Windows
- Git for Windows (Installed by Docker Toolbox as well)

#### Configuration steps
- Launch `Docker Quickstart Terminal` __*or*__ `bash`
- Launch Xming (or X11 server with your choice)
- Either set Xming to _No Access Control_ or enter your ip address into `X0.hosts` file located in `XMING_HOME`
- Run `export DISPLAY=IP_ADDRESS:0.0` where IP_ADDRESS is the IP of your machine (i.e. `export DISPLAY=192.168.100.24:0.0`)

### Launching the container
```
$ docker run --rm -e DISPLAY=$DISPLAY kostasns/eclipse:<required_tag>
```
