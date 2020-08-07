# The-Sock-Shop-microservices-demo-with-Docker-Compose
# This is a Linux Ubuntu implementation
# If after loading the local 
# Prerequisites:
# 1. Have both Docker and Docker Compose installed. Reference:
# https://docs.docker.com/engine/install/#server

# Implementation:
# 1. Clone the application repository:

$ git clone https://github.com/microservices-demo/microservices-demo

# 2. Move to the directory microservices-demo:
$ cd microservices-demo

# 3. Start the application using Docker Compose
$ docker-compose -f deploy/docker-compose/docker-compose.yml up -d

# Once the command exits the Sock Shop application should be up and running. Test it browsing:

http://localhost/

# Once your testing ends, shut the application down:
$ docker-compose -f deploy/docker-compose/docker-compose.yml down

# Load test
# The load test packages a test script in a container for Locust that simulates user traffic to the Sock Shop webpage
# It should be run against the front-end service. The address and port of the frontend will depend on the platform.

$ docker run --net=host weaveworksdemos/load-test -h $frontend-ip[:$port] -r 100 -c 2

# The help command provides more details about the parameters. 
$ docker run weaveworksdemos/load-test --help

# For the $frontend-ip and $port above, use the docker inspect command and check the "NetworkSettings" section:

$ docker inspect $frontend_container_ID

# If your  machine gets overloaded you can change the '-r 100' parameter above,
# as this is just for experimenting purposes. At first my laptop got overwhelmed, then I changed '-r 100' to '-r 10' and it worked fine.
