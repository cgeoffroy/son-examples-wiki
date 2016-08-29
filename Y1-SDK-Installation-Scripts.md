## `son-cli`

Video: TBD

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D0DF34A30A4FE3F8
echo "deb http://registry.sonata-nfv.eu:8080 ubuntu-trusty main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install sonata-cli
```

## `son-sdk-catalogues`

Video: TBD

```bash
docker pull registry.sonata-nfv.eu:5000/sdk-catalogue
git clone git@github.com:sonata-nfv/son-catalogue.git
cd son-sdk-catalogue
docker-compose down
docker-compose up -d
```


## `son-emu`

Video: https://www.youtube.com/watch?v=PP7G44yQKTI

```bash
git clone git@github.com:sonata-nfv/son-emu.git
cd son-emu
vagrant up
vagrant ssh
```



## `son-analyze`

Video: TBD

Warning: the initial `boostrap` command takes some time and bandwithi. If every is already in cache, then the command is immediate.


```bash
docker pull registry.sonata-nfv.eu:5000/son-analyze:latest
docker run -it --rm=true -v "/var/run/docker.sock:/var/run/docker.sock" registry.sonata-nfv.eu:5000/son-analyze bootstrap
docker run -it --rm=true -v "/var/run/docker.sock:/var/run/docker.sock" -v "$(pwd)/outputs:/son-analyze/outputs" registry.sonata-nfv.eu:5000/son-analyze run

```
