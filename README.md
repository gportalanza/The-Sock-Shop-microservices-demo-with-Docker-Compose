> Written with [StackEdit](https://stackedit.io/).

# Microservices-demo-with-Docker-Compose

This is a Linux Ubuntu implementation of the containerized web page Sock Shop (https://microservices-demo.github.io/) and its load testing.

**Prerequisites:**
1. Have both Docker and Docker Compose installed. Reference:

https://docs.docker.com/engine/install/#server (https://docs.docker.com/engine/install/#server)

**Implementation:**
1. Clone the application repository:

$ git clone [https://github.com/microservices-demo/microservices-demo](https://github.com/microservices-demo/microservices-demo)

2. Move to the directory microservices-demo:

$ cd microservices-demo

3. Start the application using Docker Compose:

$ docker-compose -f deploy/docker-compose/docker-compose.yml up -d

Once the command exits the Sock Shop application should be up and running. Test it browsing to:

[http://localhost/](http://localhost/)

Once your testing ends, shut the application down:

$ docker-compose -f deploy/docker-compose/docker-compose.yml down

#### Load test

The load test packages a test script in a container for Locust that simulates user traffic to the Sock Shop webpage

It should be run against the front-end service. The address and port of the frontend will depend on the platform.

$ docker run --net=host weaveworksdemos/load-test -h $frontend-ip[:$port] -r 100 -c 2

The help command provides more details about the parameters.

$ docker run weaveworksdemos/load-test --help

For the $frontend-ip and $port above, use the docker inspect command and check the "NetworkSettings" section:

$ docker inspect $frontend_container_ID

If your machine gets overloaded you can change the '-r 100' parameter above, as this is just for experimenting purposes. At first my laptop got overwhelmed by the number of requests, then I changed '-r 100' to '-r 10' and it worked fine.

## About

Linux local implementation of the open source web demo Sock Shop

### Topics

### Resources

[Readme](https://github.com/gportalanza/The-Sock-Shop-microservices-demo-with-Docker-Compose#readme)

## [Releases](https://github.com/gportalanza/The-Sock-Shop-microservices-demo-with-Docker-Compose/releases)

No releases published

[Create a new release](https://github.com/gportalanza/The-Sock-Shop-microservices-demo-with-Docker-Compose/releases/new)

## [Packages](https://github.com/gportalanza/The-Sock-Shop-microservices-demo-with-Docker-Compose/packages)

No packages published  
[Publish your first package](https://github.com/gportalanza/The-Sock-Shop-microservices-demo-with-Docker-Compose/packages)

-   © 2020 GitHub, Inc.
-   [Terms](https://github.com/site/terms)
-   [Privacy](https://github.com/site/privacy)
-   [Security](https://github.com/security)
-   [Status](https://githubstatus.com/)
-   [Help](https://docs.github.com)

[](https://github.com "GitHub")

-   [Contact GitHub](https://github.com/contact)
-   [Pricing](https://github.com/pricing)
-   [API](https://docs.github.com)
-   [Training](https://training.github.com)
-   [Blog](https://github.blog)
-   [About](https://github.com/about)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzgwMjc5NjUwLDMyODU1NzcyMywtNjU2MD
gzOTU1LDM4MDI3OTY1MCw1MTUyNTYyNTQsLTIxMDk3NTk2MDIs
LTEzMDc3ODUzMzVdfQ==
-->