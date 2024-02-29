## clone the repo

```bash
git clone https://gitlab.engeem.com/isrboka/openmetadata
cd openmetadata
```

## Prerequisites

- [Docker 20 or higher](https://docs.docker.com/engine/install/)
- [Java JDK 17](https://docs.oracle.com/en/java/javase/17/install/overview-jdk-installation.html)
- [Antlr 4.9.2](https://www.antlr.org/) - `sudo make install_antlr_cli`
- [JQ](https://jqlang.github.io/jq/) `apt-get install jq` (Ubuntu)
- [Maven 3.5.x or higher](https://maven.apache.org/install.html) 
- [Python 3.7, 3.8 or 3.9](https://www.python.org/downloads/)
- [Node >=16.0.0 & Node <= 18.0.0](https://nodejs.org/en/download/)
- [Yarn ^1.22.0](https://classic.yarnpkg.com/lang/en/docs/install/)

## Generate the db and the elastic search

```bash
docker compose -f docker/development/docker-compose.yml up mysql elasticsearch --build -d
```
## Build the whole app

do the 
```bash
mvn clean install -DskipTests
```

do this to go where the generated tar file is :

```bash
cd openmetadata-dist/target
```

do this to extract the generated tar file : 
```bash
tar -xzvf openmetadata-1.4.0-SNAPSHOT.tar.gz
```

cd into the folder :

```shell
cd  openmetadata-1.4.0-SNAPSHOT
```

generate the mysql : 
```shell
sh bootstrap/bootstrap_storage.sh drop-create-all
```

- write `DELETE` and enter

execute the app : 

```shell
sh bin/openmetadata-server-start.sh conf/openmetadata.yaml
```

## To modify the UI
## build the ui :
make sure this is installed : 

```shell
sudo make install_antlr_cli
```

Install the dependecies : 

```bash
make yarn_install_cache
```

run the frontend : 

```bash
make yarn_start_dev_ui
```


