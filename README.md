# rst-docker-files

Docker is a virtualization program that utilizes [containers](https://www.docker.com/what-docker) instead of classic virtual machines. Docker allows us to use a base image for an OS and then add all the dependencies needed for the project. This way we can easily start with a fresh environment every time, but still have everything we need installed. After you install Docker for your platform, here is a brief example on how to use the Docker files that are set up for RST.

##Ubuntu 14.04 example

Pull the base image from Dockerhub
```bash
docker pull ubuntu:14.04
```

Then we can move into our directory and build our custom image
```bash
cd ubuntu-14.04_docker
docker build -t ubuntu-14.04-rst-docker
```

Our image will take awhile to build, but once completed, everytime the image is run there will be a fresh install of RST and all it's dependencies. We can `git checkout` any branches to test and compile. We can start a pseudo-tty in the image and execute a shell to run commands like so:

```bash
docker run -it ubuntu-14.04-rst-docker /bin/bash
```

When we are finished, we clean up our Docker containers with 
```bash
docker rm $(docker ps -a -q -f status=exited)
```

***Some systems require you to be root to run any Docker commands***

More info on Docker can be found [here](https://prakhar.me/docker-curriculum/) and [here](https://docs.docker.com/engine/getstarted/step_four/).
