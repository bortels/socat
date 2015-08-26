docker-expose and socat
=======================

This repository contains two items; a Docker container named "socat", and a script named "docker-expose"

Have you ever had a running container with a port EXPOSEd, but not mounted - and you wanted to get to it? Maybe you
need to do a temporary connection, maybe you used --link and now need to get to that port from elsewhere? You can
always stop the container, and restart it mounting that port - but stopping the container is not always viable.

Enter docker-expose. This is a small script that runs a new socat container, --linking the original container, and
exposing that port to the world. Run this, do what you need, and kill the new container when you are done. Easy Peasy. 

Both the Dockerfile and the script are nearly trivial - the wise will spend 30 seconds looking to ensure they are what I say.

socat
-----

The "socat" container is simply Alpine Linux 3.2 running socat. It is provided as a trusted build image for convenience.

docker-expose
-------------

Exposes a port on a pre-existing docker container. The container must EXPOSE the ports internally.

This script uses a "socat" container, which is simply alpine linux running socat.

The new container will be named for the port and container being EXPOSEd. Kill it to
un-expose the port.

Disclaimer: docker-expose is not an official Docker Inc. bit of code, despite "docker" being in the name.
I named it as I did purely to match it conceptually with the rest of the docker-dash commands.
Having said that, they are welcome to any or all of it; in particular, a "socat" library container seems useful.

Mad props to the kids at Docker - thank you for sharing. 

PS. This basic scheme is/was not my idea; it was proposed online in a stackexchange response. I simply extended it to arbitrary
containers and ports, and put it up to use. We stand on the shoulders of giants.
