# How to migrate VOI network from testnet to mainnet

## Stop previous services (if exists)
Stop all the previous voi services already set on the machine \ 
To know if there is a previuos active service: `systemctl status voi` \
To stop previous service: `systemctl stop voi`

## Install new service
As said in [this official guide](https://voinetwork.github.io/voi-swarm/updating/migrating-network/) 
```
export VOINETWORK_NETWORK=mainnet
/bin/bash -c "$(curl -fsSL https://get.voi.network/swarm)"
```
Then let it do its work until it finish or give you an error

## Troubleshoot
I don't know why but it could happen (to me it happend all the time) that the procedure return this error: \
`permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: ...` \
The problem here is that docker is not properly installed, so you by following [this guide](https://www.digitalocean.com/community/questions/how-to-fix-docker-got-permission-denied-while-trying-to-connect-to-the-docker-daemon-socket) it turns out that you need to execute \
`sudo groupadd docker` \
`sudo usermod -aG docker ${USER}` \
NOTE! Restart your console before move forward (logout + login) \
\
To check if it's ok you can do some checks: \
`sudo docker container ls` This sould return nothing (but not an error) \
or \
`sudo docker run hello-world` This should return some "Hello World" message 

## Finish the procedure
Now that everithing is working exegute the first command again and the procedure should keep going until the end \ 
```
export VOINETWORK_NETWORK=mainnet
/bin/bash -c "$(curl -fsSL https://get.voi.network/swarm)"
```
