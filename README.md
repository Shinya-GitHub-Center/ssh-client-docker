# About
Docker version's ssh client, intended for use to connect with the major cloud vendor's remote virtual machines

## How to use
1. Download the source of the latest commit or latest release of this repository, then unzip and rename the root folder's name to your favorite name - something like `myAWS_ssh-client_CTNR`
2. Locate your key files into the `./ssh-cli/.ssh/keyfiles` folder
3. Modify `./ssh-cli/.ssh/config` file (path to the key files has to be full path)
4. On your linux environment, go to the directory where this project's `docker-compose.yml` file exists, then run the following command:
```
docker compose up -d
```
5. Enter the docker container, the command for instance:
```
docker exec -it <created docker container name> bash
```
6. Change the permission with all key files in the `~/.ssh/keyfiles` folder, for instance:
```
chmod 600 ~/.ssh/keyfiles/veryhappy.pem
```
7. Run the ssh command with Host attribute - which is written in the config file, for instance:
```
ssh myhappyweb
```
8. At the time of first connection, you may be asked for a connection confirmation, of course say `yes`
9. If you want to finish your remote connection, type `exit` to go back to your local docker machine
10. You can store any files in the workdir directory and transfer them to or from your remote virtural machines, for instance:
```
scp ./index.html myhappyweb:/var/www/html/
scp myhappyweb:/var/www/html/index.html ./
```

## Please
* Do not delete any key files inside `./ssh-cli/.ssh/keyfiles` folder. They are not supposed to be issued again due to the cloud vendor's strict rules, and keep the keyfiles secret - do not upload or share to any public places
* If you want to use another UID & GID inside the docker container, in order to match your host's UID & GID, please change the Dockerfile's `ARG UID=1000` & `ARG GID=1000` to your desired number
