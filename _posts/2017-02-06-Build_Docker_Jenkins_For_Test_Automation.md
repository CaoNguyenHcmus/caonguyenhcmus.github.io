---
layout: post
title:  "Build Docker Jenkins For Test Automation Environment"
date:   2017-02-06
categories: Docker, Jenkins, Test Automation
---
SETUP DOCKER
==================================================


	# Add $USER to docker group to omit 'sudo' from docker command
	$ sudo gpasswd -a $USER docker
BUILD JENKINS
==================================================
`/docker/Dockerfile` is the jenkins recipe for R-Car
QNX test automation. To Build the jenkins image, execute below
commands.

	# Build jenkins image for Docker
	$ cd /docker
	$ docker build -t _jenkins .   # may this take a while

	# after the build, you will see jenkins image created
	$ docker images
	REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
	...
	_jenkins         latest              xxxxxxxxxxxx        xxxxxxx             xxxxx MB
	...
Note: Run only one time
Start Jenkins with some port and shared directories settings.

	$ docker run --name jenkins_image -p 8080:8080 \
		-v jenkins_home:/var/jenkins_home \
                -Dfile.encoding=UTF-8 -Dsun.jnu.encoding=UTF-8' \
                _jenkins &

After starting Jenkins, you can access to Jenkins via a browser as
`http://<Host PC IP address>:8080`.

$ docker run -p 8080:8080 -p 50000:50000 jenkins
