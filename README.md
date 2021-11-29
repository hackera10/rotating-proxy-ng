# rotating-proxy-ng

This is the fork of the original repo https://github.com/mattes/rotating-proxy. The original repo has old dependencies and unable to built the docker container due to that. This repo fixes some of the immediate issues while building containers, moved to alpine, and added a `torrc` file. The dependency [polipo](https://github.com/jech/polipo) is archived and due to this, the dependency is built within the docker file.

The tor settings can be configure using `torrc` file as well. The ng stands for next generation compared to the original repo.

## Usage

```bash
# build the docker container
docker build -t hackera10/rotating-proxy-ng:latest .

# start the docker container
docker run -d -p 5566:5566 -p 4444:4444 --env tors=10 -v "$(pwd)/torrc:/etc/tor/torrc" hackera10/rotating-proxy-ng

# test with ...
curl --proxy 127.0.0.1:5566 http://ip.jsontest.com/

# monitor
http://127.0.0.1:4444/haproxy?stats
```
