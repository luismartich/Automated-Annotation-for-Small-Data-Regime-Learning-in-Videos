# **Milestone 1**

Windows 10 Install WSL2 (Windows subsystem for Linux) refer to this official guide. WSL2 requires Windows 10, version 2004 or higher. Note: You may not have to install a Linux distribution unless needed.

Download and install Docker Desktop for Windows. Double-click Docker for Windows Installer to run the installer. More instructions can be found here. Official guide for docker WSL2 backend can be found here. Note: Check that you are specifically using WSL2 backend for Docker.

Download and install Git for Windows. When installing the package please keep all options by default. More information about the package can be found here.

Download and install Google Chrome. It is the only browser which is supported by CVAT.

Go to windows menu, find Git Bash application and run it. You should see a terminal window.

Clone CVAT source code from the GitHub repository.

The following command will clone the latest develop branch:

git clone https://github.com/opencv/cvat cd cvat See alternatives if you want to download one of the release versions.

Run docker containers. It will take some time to download the latest CVAT release and other required images like postgres, redis, etc. from DockerHub and create containers.

docker-compose up -d (Optional) Use CVAT_VERSION environment variable to specify the version of CVAT you want to install specific version (e.g v2.1.0, dev). Default behavior: dev images will be pulled for develop branch, and corresponding release images for release versions.

CVAT_VERSION=dev docker-compose up -d Alternative: if you want to build the images locally with unreleased changes see How to pull/build/update CVAT images section

You can register a user but by default it will not have rights even to view list of tasks. Thus you should create a superuser. A superuser can use an admin panel to assign correct groups to other users. Please use the command below:

winpty docker exec -it cvat_server bash -ic 'python3 ~/manage.py createsuperuser' If you don’t have winpty installed or the above command does not work, you may also try the following:

enter docker image first
docker exec -it cvat_server /bin/bash

then run
python3 ~/manage.py createsuperuser Choose a username and a password for your admin account. For more information please read Django documentation.

Open the installed Google Chrome browser and go to localhost:8080. Type your login/password for the superuser on the login page and press the Login button. Now you should be able to create a new annotation task. Please read the CVAT manual for more details.
