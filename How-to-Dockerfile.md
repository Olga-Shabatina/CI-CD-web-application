# Containerize a web application using Docker and DockerHub
## Step 1.1. Install Docker Desktop on Windows:
1. Go to the website https://docs.docker.com/docker-for-windows/install/ and download the docker file.
   > Note: A 64-bit processor and 4GB system RAM are the hardware prerequisites required to successfully run Docker on Windows 10.
2.  Double-click on the Docker Desktop Installer.exe to run the installer.

3. Once you start the installation process, always enable Hyper-V Windows Feature on the Configuration page.

4. Follow the installation process to allow the installer and wait till the process is done.

5. After completion of the installation process, click Close and restart. 
## Step 1.2. Install Docker Engine  on Ubuntu:
Follow the official guide: https://docs.docker.com/engine/install/ubuntu/
> To install Docker Engine, you need the 64-bit version of one of these Ubuntu versions:
> 
> - Ubuntu Impish 21.10
> - Ubuntu Hirsute 21.04
> - Ubuntu Focal 20.04 (LTS)
> - Ubuntu Bionic 18.04 (LTS)

Run following commands.

Uninstall old versions:

    $ sudo apt-get remove docker docker-engine docker.io containerd runc
Set up the repository:
```
$ sudo apt-get update
$ sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
Install Docker Engine:

    $ sudo apt-get update
    $ sudo apt-get install docker-ce docker-ce-cli containerd.io

Verify that Docker Engine is installed correctly by running the hello-world image:

    $  sudo docker run hello-world


##Step 2. Create a Dockerfile:
To containerize we need a Dockerfile which is a text document that contains all the commands a user could call on the command line to assemble an image.

The `FROM` instruction sets the Base Image for subsequent instructions. As such, a valid Dockerfile must have FROM as its first instruction. The image can be any valid image – it is especially easy to start by pulling an image from the Public Repositories.

The `ADD` instruction add's the local files into the containers specified path.

The `EXPOSE` instruction informs Docker that the container listens on the specified network ports at runtime.

The `CMD` instruction should be used to run the software contained by your image, along with any arguments. We use this to start our tomcat inside the image.

    FROM tomcat:8.0.43-jre8
    ADD sample.war /usr/local/tomcat/webapps/
    ADD server.xml /usr/local/tomcat/conf/
    EXPOSE 8080
    CMD chmod +x /usr/local/tomcat/bin/catalina.sh
    CMD ["catalina.sh", "run"]