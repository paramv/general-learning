 * Linking ports across containers 
 `docker run -d --name=link-test myrepo/fedora-httpd`
 `docker run -it --link=link-test:lt --name=linked fedora:22 bash`
* Any time you add an argument to the end of a docker run command, the CMD instruction inside the container is ignored. 
* Using the ENTRYPOINT Instruction
	* The ENTRYPOINT instruction lets you define the command executed when you run the container image. It does this in a way that is not overridden by arguments you put at the end of a docker run line. If your Dockerfile includes an ENTRYPOINT instruction and there is also a CMD instruction, any arguments on the CMD instruction line are passed to the command defined in the ENTRYPOINT line
* You can use the ADD instruction to add selected files into the container at build time. When you use ADD to add files and directories to your image, docker build uses the directory containing the Dockerfile on your host system as both the root directory (/) and the current directory.
* Some docker commands
	* `docker build --force-rm=true . `
	* `docker build --no-cache=true . `
	* `docker build -f ~/Myweb/Dockerfile01 ~ `
	* `docker build --pull=true `
* You can exclude files from the build directory structure by adding a .dockerignore file to the build directory and putting files in it that you want the build to ignore.

## Linking Containers
* To link containers start each container individually, with proper names
`docker run -d --name mongoserver mongo`
* Next link the container as follows
`docker run -it --link <linked-container-name>:<linked-container-alias> --name <container> <image>`
Example
`docker run -it --link mongoserver:db --name app-server app`

## Docker Compose
* Installation
	curl -L https://github.com/docker/compose/releases/download/1.6.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
	sudo chmod +x /usr/local/bin/docker-compose
* Code completion
	curl -L https://raw.githubusercontent.com/docker/compose/$(docker-compose version --short)/contrib/completion/bash/docker-compose > /etc/bash_completion.d/docker-compose

### Docker Compose Usage
* Create a docker-compose.yml file