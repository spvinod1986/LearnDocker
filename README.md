# Docker
- A platform for consistently building, running and shipping applications.
- Virtual Machine: An abstraction of a machine(physical hardware).
- Virtual machine runs by using hypervisors. Hypervisors available in market - VirtualBox, VMWare, Hyper-v(Windows only).
- Problems of VM : Each VM needs a full blown OS, Slow to start and Resource intensive.
- Container: An isolated environment for running an application. Allow running multiple apps in isolation. They are lightweight. Use OS of the host. They start quickly and need less hardware resources.
- Docker uses client server architecture. It has client component which talks to server component(Docker Engine) using REST API. A container is just a process. All containers share the kernel of the host.
- A kernel of OS manages applications and hardware resources.
- Linux machine can only run linux containers. Windows can run both Windows and linux containers. Becauce windows 10 is now shipped with custom built linux kernel. Docker on mac uses light weight linux vm to run linux containers in mac.
- To dockerize an application, add a docker file to it.
- DockerFile: It is a plain text file used by Docker to package an application in to an image.
- Image: An image containes a cut down OS, run time environment, application files, third party libraries, environment variables.
- Once we have an image, we can ask docker to start container using the image. Container is just a process.
- Docker registry is a remote repository of images(like DockerHub).
- Command to build image`docker build -t hello-docker .`
- Command to view all images `docker image ls`
- Command to run the image `docker run hello-docker`
- Command to run a container in interactive mode `docker run -it ubuntu`. Running this again, will create another container.
- Command to view running processes/containers `docker ps`
- Command to view all(running/stopped) processes/containers `docker ps -a`
- Command to start container in interactive mode `docker start -i 2f7`
- Commant to start another bash session in the same container in interactive mode `docker exec -i 2f7 bash`
- Command to start another bash session with user login in the same container in interactive mode `docker exec -i -u john 2f7 bash`

## Linux Command Line
- Distros/Distributions : Ubuntu, Debian, Alpine, Fedora, CentOS
- root user has highest privilages. / (or) forward slash is the root directory. # means root user and has highest privilages. $ means normal user without highest privilages.
- Windows uses backward slash and linux uses forward slash. Linux is case sensitive OS.
- `echo hello` prints hello, `whoami` prints the user name, `echo$0` prints the current execution program directory, `history` prints the history of commands typed.
- `apt` is Ubuntu's package manager. Advanced Package tool. `apt` command gives you the list of mostly used `apt` commands. `apt-get` is the old package manager tool.
- `apt list` gives list of all packages in the local database. `apt update` will update the local database with list of new packages available in remote repo.
- `nano` is basic text editor for linux. `apt install nano` installs nano. `apt remove nano` removes nano.
- Linux just like windows, files and directories are organized in trees/hierarchual structures.
- Windows : `C:` drive is top of hierarchy followed by `windows` and `programfiles`.
- Linux: `/` is root directory on top of hierarchy, followed by `bin` - binaries and programs , `boot` - all files related to booting,`dev` - shortcut for devices ,`etc` - shortcut for editable text configuration,`home` - home directory of users,`root` - home directory of root user, only root user can access this directory,`lib` - library files like software library dependencies,`var` - variable files which are updated frequently like lockfiles, application data and so on, `proc` - files that represent running processes. In Linux, everything is a file.
- `pwd` prints working directory, `ls` prints list of files and directories in current directory, `ls -1` to show one file in one line, `ls -l` to include more details like permissions etc.
- `cd` is used to change directory. You can enter relative or absolute path. absolute path always starts with root directory `/`. `cd ..`To go back to previous directory with one level up. `cd ../..` to go 2 levels up. `cd ~` takes you to home directory.
- `mkdir test` to create a directory called test, `mv test docker` rename directory to docker, `touch hello.txt` to create new file, `touch file1.txt file2.txt file3.txt` to create multiple files in one go, `mv hello.txt hello-docker.txt` renames file, `rm file1.txt file2.txt file3.txt` to remove one or more files, `rm file*` remove files with pattern, `rm -r docker/` to remove directory which requires recursive.
- `nano file.txt` opens a file in text editor. `cat` useful to concatenate multiple files, this can be used to view text of smaller files which fits on one page.`more` should be used to view contents of large files, use space go page by page, use enter to go one line at a time but you cannot scroll down you can just scroll up using `more`. `less` is newer command to replace more, you can use up and down to scroll up and down, space to go page by page, enter to go line by line. `head -n 5` to show first 5 lines of a file. `tail -n 5` to show last 5 lines of a file.
- One of the main concepts in Linux is the concept of standard input and output. Standard input is the keyboard and standard output is the string. You can always change the source of input and output and this is called redirection. `cat file1.txt` reads content of file and prints it in standard output which is the string in console.`>` is redirection output operation and `<` is redirection input operator. `cat file1.txt > file2.txt` reads content from file1.txt and redirects output to new file file2.txt. `cat file1.txt file2.txt` reads content from both the files and prints it in terminal. `cat file1.txt file2.txt > file3.txt` reads content from both the files and redirects and creates a new file3.txt. Redirection can be used with any command. `echo helloworld > hello.txt` prints helloworld in new file hello.txt.
- `grep` global regular expression print is used for searching text in files. This search is case sensitive. `grep hello file1.txt` searches for hello in file1 and prints it. `grep -i hello file1.txt` is used to remove case sensitive in search. `grep -i hello file1.txt file2.txt` to search in multiple files. `grep -i hello file*` to search in multiple files using regular expression. `grep -i -r hello .` to search in current directory. `grep -i -r hello /etc` to search in a directory, recursive flag is required to search in directories. In linux, you can combine options, so instead of `grep -i -r hello /etc`, you can do `grep -ir hello /etc`.
- By default `ls` does not show hidden files and directories. `ls -a` shows hidden files and directories. `find` for finding files and directory, executing this without any argument finds all files and directories in current directory recursively. `find /etc` searches in etc directory. `find -type d` to find only the directories.`find -type f` to find only the files. `find -type f -name "f*"` finds all the files whose name starts with f. This is case sensitive. `find -type f -iname "F*"` to make it case insensitive.
- `mkdir test; cd test; echo done` executes multiple commands in one go. In this command, even if one command fails the others will excute. `mkdir test && cd test && echo done` executes multiple commands in one go but fails even if one command fails. `mkdir test || cd test || echo done` executes atleast one of the query. `ls /bin | less` to chain command output to another command. `mkdir test;\ cd test;\ echo done` to type multiple commands in multiple lines use backslash.
- In linux, we can use environment variables to store configuration settings for our applications. `printenv` will print all environment variables in this machine. `printenv PATH` to print value of specific variable. `echo $PATH` also prints value of specific environment variable. `export DB_USER=vinod` creates an environment variable just for current session. To get the environment variable persistent between sessions then it should be written in `.bashrc` file which is users personal startup file. Everytime a user logs in, linux loads this file from users personal home directory. `echo DB_USER = vinod > .bashrc` will overwrite entire bashrc file. `echo DB_USER = vinod >> .bashrc` will append the permanent environment variable to bashrc file. The changes to `.bashrc` file is only effective in the next terminal session, if you want to reload the file in the same session by executing this command from source directory `source .bashrc`.
- A process is an instance of running program. `ps` lists all running processes. `sleep 3` creates a process which sleeps for 3 seconds. `sleep 3 &` creates the same process as background process. `kill 38` will kill process with ProcessID 38.
- `useradd` is used to add user, `usermod` to update an user and `userdel` to delete an user. `useradd -m john` creates the user and saves the user account info in /etc/passwd. `usermod -s /bin/bash john` modifies the user to use new bash instead of old shell. `cat /etc/shadow` is the file where passwords of users are stored in encrypted format. This file is accessible only for root users. `userdel john` will delete user John. `adduser` is newer command which uses `useradd` in the background, this is more interactive than the old command.
- `groupadd` to add new group, `groupmod` to modify group and `groupdel` to delete a group. Group is used so that all users in same group has same permissions. `cat /etc/group` is the file which stores all group information. Every Linux user has one primary group and 0 or more secondary groups. Primary group is automatically created when we create a new user and it may have same name as the user. `usermod -G developers john` adds john to secondary group developers.
- Filepermissions are usually represented as `drwxr-xr-x` or `-rw-r--r--`. The first letter `d` means directory, `-` means file. The remaining 9 characters are divided in to 3 groups. The first group represents the permission for the user who owns this file. The second group represents the permission for the group that owns this file. The third group represents the permission for everyone else. `r` means read, `w` means write and `x` means execute. `chmod` is the command used to change permissions of the user. `chmod u+x deploy.sh` adds execute permission. `chmod u-x deploy.sh` removes execute permission for the user. `chmod o+x deploy.sh` adds execute permission for other users. `chmod og+x+w-r deploy.sh file.txt` add execute, write and remove read permission for 2 files for other users and group that owns those file.

## Building Images:
- Each container is an isolated environments for executing an application.
- A docker file contains instructions for building an image.
- `FROM` specifies base image, `WORKDIR` specifies working directory, once this is set all following commands will execute in that directory, `COPY` and `ADD` for copying and adding files and directories, `RUN` for executing operating system commands, `ENV` for setting environment variables, `EXPOSE` for setting port, `USER` to specify user that should run the application, `CMD` and `ENTRYPOINT` to specify the command to be executed when we start the container.
- `.dockerignore` file is used to specify files to be excluded.
- An image is a collection of layers. `docker history image-name` should give the list of layers. This list should be read from bottom to top. Docker has optimization technique built in to reduce image build time. If there is no change in instruction, then docker will try to reuse the layer from cache instead of rebuilding all the layers of image.
- To optimised your build, the dockerfile should be created in sucha way that the instructions that don's change too often(stable instructions) should be on top followed by changing instructions.
- `docker image prune` will delete all dangling images. Dangling images are those which are created earlier for some app by docker but not related to any images currently in the machine. `docker container prune` will remove all stopped containers. `docker image rm image-name` to remove image.
- We can tag a image when building it `docker build -t react-app:tagnumber` or using `docker image tag react-app:latest react-app:1`
- `docker login` command is used to login to docker hub. `docker push tagname` to push a image to remote repository.
- `docker image save -o react-app.tar react-app:3` can be used to compress and save the image file in local machine. tar file is similar to zip file for linux. `docker image load -i react-app.tar` can be used to load the image back.

## Working with Containers:
- `docker run -d react-app` runs the container in detached mode/background so you can continue working on terminal.
- `docker logs 655` shows logs of container Id 655.
- `docker run -d -p 80:3000 react-app` maps port 80 of the host to port 3000 of the container.
- `docker exec` is used to run a command in a running container. Where as `docker run` will start a new container.
- `docker stop 655` stops container, `docker start 655` starts container. Starts and stops same container.
- `docker container rm 655` or `docker rm 655` to remove container. You cannot remove running container. To remove running container you will need to either stop it and remove or use force command `docker rm -f 655`.
- Each containers has its own file system which is invisible to other containers. Hence you should not store data in containers file system. A `volume` is a storage outside of containers. It could be directory on host or in cloud. It can be used to shared data between multiple containers. `docker volume` is the command used to work with volumes. `docker volume create app-data` creates a new volume. `docker volume inspect app-data` to work with volume. `docker run -d -p 4000:3000 -v app-data:/app/data react-app` will create volume and map the volume to app/data folder in container filesystem.
- `docker cp 904:/app/log.txt .` is used to copy files from container to the host. `docker cp hello.txt 904:/app` to copy file from host to the container.
- For production, always build a new image. For development, you can create a mapping/binding between host and container and hence any changes in host will immediately be seen in the container. `docker run -d -p 5001:3000 -v $(pwd):/app react-app` will map working directory to container app directory.

## Running multi container applications:
- Docker compose is a tool build on top of docker engine. It is an incredible tool to work with multiple containers.
- `docker image rm $(docker image ls -q)` removes all images in your machine. `docker image rm -f $(docker image ls -q)` removes all stopped containers in your machine. You can also use GUI tool Docker desktop for mac to purge and delete data.
- JSON vs YAML : JSON is human readable language to represent data with key value pair representation. Array is defined using square brackets. Extension for Json file is `.json`. YAML is another language representing data and is less cluttered than JSON. Extension can be `.yaml` or `.yml`. Yaml does not require braces or comma and hyphen is used to represent array. Intendations are used to represent objects. Parsing YAML is slower than JSON.
- `docker-compose build` builds all the images for all the apps listed in Docker Compose file.
- `docker-compose up` runs all the images if the images is already build, if not it will build and run the images.
- `docker-compose up -d` to run the images in detached mode.
- `docker-compose ps` lists all the containers relevant to the application.
- `docker-compose down` will stop and remove the containers but the images will still exist.
- Every docker installation will have 3 networks: host, bridge and none. `docker network ls` shows list of network created in your machine.
- Docker comes with embedded DNS server and each container contains DNS resolver. Each container has ip address and is part of a network.
- `docker-compose logs` list logs of all containers in an application in one place.
- In Dev environment, changes in dev can be published by mapping volumes from container app directory to the local source repo in the docker-compose file.
- You can run db migration before starting a container, run tests etc by using `command` in docker-compose.

## Deploying Applications:
- Deployment has 2 options: Single host and Cluster deployment. Single host is easy as there is only one server but less availability. Cluster includes deploying to group of servers.
- Docker has its own orchestrator solution called docker swarm.
- Docker machine is used and it has drivers for different clud platforms.
