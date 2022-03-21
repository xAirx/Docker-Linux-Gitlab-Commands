# Docker-Linux-Gitlab-Commands

Table of contents.

I. Commonly used commands in docker

II. Commonly used commands in docker-compose

III. Setup gitlab-runner

IV. Commonly used commands in Linux

V. How To Secure a Containerized Node.js Application

I. Commonly used commands in docker:

    Build a image.
    - docker build -t "image-name" .
    - docker build -f "Dockerfile.dev" -t "image-name" .

    Run a container.
    - docker run -it --rm --name "container-name" -p 5000:5000 "image-name"
    - docker run -it -d --rm --name "container-name" -p 5000:5000 "image-name"
    - with -d: detach -> run a container in the background.

    Stop a container.
    - docker stop "container-name"

    Stop all running containers.
    - docker stop $(docker ps -a -q)

    Show all images.
    - docker images

    Delete a image.
    - docker rmi "image-id|image-name"

    Delete all images.
    - docker rmi $(docker images -q)

    Delete all images.
    - docker rmi $(docker images -f dangling=true -q)

    Show all running containers.
    - docker ps

    Show all containers.
    - docker ps -a

    Delete a stopped container.
    - docker rm "container-name"

    Delete all stopped containers.
    - docker rm $(docker ps -a -q)

    Kill all running containers.
    - docker kill $(docker ps -q)

    List volumes.
    - docker volume ls

    Remove all unused local volumes.
    - docker volume prune

    Remove one or more volumes.
    - docker volume rm "volume-name"

    Run commands in a docker container.
    - docker exec -it "container-name" sh

    Push image to docker hub.
    - docker push "image-name:tag"

    Pull image from docker hub.
    - docker pull "image-name:tag"

II. Commonly used commands in docker-compose:

    Build and rebuild a image.
    - docker-compose up --build
    - docker-compose -f "docker-compose.dev.yml" up --build

    Run and start containers.
    - docker-compose up
    - docker-compose -f "docker-compose.dev.yml" up

    Stop and clear containers.
    - docker-compose down
    - docker-compose -f "docker-compose.dev.yml" down

    Stop and clear containers, volumes.
    - docker-compose down -v
    - docker-compose -f "docker-compose.dev.yml" down -v

III. Setup gitlab-runner:

    Download the binary for your system
    - sudo curl -L --output /usr/local/bin/gitlab-runner https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64

    Give it permissions to execute
    - sudo chmod +x /usr/local/bin/gitlab-runner

    Create a GitLab CI user
    - sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash

    Install and run as service
    - sudo gitlab-runner install --user=gitlab-runner --working-directory=/home/gitlab-runner
    - sudo gitlab-runner start

    Register a runner
    - sudo gitlab-runner register --url https://gitlab.com/ --registration-token "registration_token"

    Add gitlab-runner to the docker group
    - sudo usermod -aG docker gitlab-runner

    Grant sudo permissions to the gitlab-runner user.
    - sudo nano /etc/sudoers
    - gitlab-runner ALL=(ALL) NOPASSWD: ALL

    Fix bug.
    - sudo nano /home/gitlab-runner/.bash_logout

IV. Commonly used commands in Linux:

    cd Linux command
    The cd command is one of the most used Linux commands. The purpose of this command is to change the directory. In other words, it enables to switch between file lists. For example, if you needed to shift from the home directory to the myfile directory, you would enter the following command:

cd/myfile/application        

    ls command
    The ls command is the most common and the most used command in the Linux environment. The ls command is also called as the list command which works in the Linux terminal to display all of the important folders or directories listed under a particular file system. For instance, the command:

ls /myfiles     

    man command
    The man command is one of the best Linux commands. This command is also known as the manual command. It is used to display the manual use of the inserted command. In other words, it is the meta-command of Linux. Entering the man command will display all the information about the command. For example:

man ls         

The above command will display all the necessary information about the ls command.

    cat command
    The cat Linux command is a short form of concatenate. It lists the information of files to the Linux terminal window. This is much quicker than opening the file in an editor. If you want to read the data of .bash_log_out file, enter the following command:

cat .bash_logout         

    mkdir command
    mkdir Linux is one of the basic Linux commands in the environment. As the name suggests, this command is used to make a directory or in other words, it used to create a directory. The following command will create a new folder called a test folder. An example of the mkdir command:

mkdir testfolder           

    chmod command
    The chmod command is used to set the file permission or a flag on a folder or a file. The flags describe who can read, write into the file or a folder. This is one of the most crucial commands of the Linux environment. It is widely used by administrators. For example,

chmod -R 7 test.txt            

    rmdir command
    Just like the mkdir Linux command, rmdir is also one of the most used commands. This command allows users to remove any file or directory from a particular location. In other words, you can use this command to delete a particular directory. For example, the following command will remove the mydirectory from the system.

rmdir mydirectory             

    touch command
    The touch command is just like a mkdir command. The main difference between touch command and mkdir is that the touch command allows its users to create a text file or a .doc file. For example

touch mytestfile.txt           

    locate command
    The locate command is also called as the find command. This command is used to find or locate a particular file. This command is one of the common Linux commands. If you don’t know the exact name of the file or the exact destination of the particular file then this command is very useful. The following command will locate the file which contains the words “result”, “final” “total”

locate -i *result*final**total*             

    clear command
    As the name suggests, this command is used to clear the Linux window terminal. For using this command user just has to type clear and then press enter. This is the most used command in the Linux command line environment.

clear             

    rm command
    Just like rmdir which removes the directory, rm command is used to remove the particular file. Suppose you want to remove .txt file or a .doc file then rm command is useful. For example,

rm mytestfile.txt               

    mv command
    The mv command is one of the most used commands in the Linux environment. This command enables a user to move a file to another directory. For example,

mv/myfolder/appli/myapps /myfolder/newapp/firstapp             

    curl command
    The curl command is used to extract information from Uniform Resource Locators (URLs) or IP addresses. If it is not installed in your Linux environment then, first of all, you have to use apt-get command to install curl package.

curl https://github.com/torvalds/linux         

    echo command
    The echo command is used to print the specified text on the terminal window. For example, if you want to print “Hello World” text on the terminal window then this command can be used.

echo Hello World        

    free command
    The free command is used to generate information about memory usage. It calculates for both the main Random Access Memory (RAM) and swap memory. For example

free -h          

    groups command
    The groups command is one of the most important commands of Linux environments. This command describes the membership of a particular user. In other words, it tells which user belongs to which particular group. For example,

groups devat    

groups dev     

    head command
    The head command is used to display the first 10 lines of a particular file. If you want to read fewer lines then the extension -n can be used. For example,

 head -myfile.c          

    history command
    The history command is most frequently used and one of the most important Linux commands. This command displays the list of the previously used commands. For using this command you just have to enter history.

history 

    passwd command
    The password command is one of the useful Linux commands which is used to change your own password. This command is often used by the administrator to change other users’ passwords also. For example

sudo passwd dev123           

    ping command
    The ping command is the top command in the Linux environment. This command is always used to check the network connection or to troubleshoot networking issues. To use this command all you have to do is provide an IP address after ping. For example

ping 8.8.8.8            

21.alias
The alias command tells the shell to return one string with a different string while performing the commands. When users frequently have to apply a single command many times, in those circumstances, they use something called an alias. Alias is like an alternative command that will have identical working as if they are addressing the entire command.

$ alias rm='rm -i'          

The above alias will stop unintentional deletion.

    ZIP
    ZIP is a confining and file packaging service for Linux. Each file is saved in a separate .zip file with the extension .zip. zip is used to shrink the files to decrease file size and also utilized as a file package utility. zip is free in various operating systems like Unix, Linux, Windows, etc. The program is beneficial for packaging a collection of files for sharing; for archiving files; and for maintaining disk location by provisionally reducing additional files or folders.

$zip newfile.zip name.txt                

    dd
    dd is a command-line service for Linux operating systems whose main goal is to change and copy files. This is one of the most important commands. dd can also be utilized for chores such as backing up the boot area and getting a thickened mass of temporary data. It can also perform transformations on the data as it is depicted, like byte order exchanging and change to and from the ASCII and EBCDIC.

dd if = /dev/hda of = ~/hdadisk.img            

The above command is used to create an image of a Hard Disk. The dd command can also be used to create CDROM Backup and to restore the Hard Disk image.

    chown
    The chown command enables users to modify the user and/or group control of an assigned file, directory, or representative link. In Linux, all files are connected with an owner and a collection and distributed with support access preferences for the file owner, the segments, and others. In Linux, each userhas some characteristics affiliated with them. These characteristics include a user ID and a home directory. Users can add more users into a unit or a group to make the method of controlling users more straightforwardly. In this, a stipulated user can be connected with a “default group”. It can also be a segment of other groups on the machine. In Linux, regular users can modify the group of the file only if they hold the file rights and solely to a group of which they are a branch. Managing users can modify the group control of all files.

sudo chown root myfile1.txt          

    sudo
    The sudo command lets users operate applications as a different user, by default the root. If the user uses a lot of time on the prompt then the sudo is one of the commands that users will utilize pretty often. This is the most important command. sudo is actually a “Super User DO” command in Linux. It is usually applied as a prefix of any command that the only superuser is permitted to execute. If someone prefixes “sudo” with any Linux command then that command runs with heightened rights or in other words provides a user with precise authorizations to perform a command as superuser.

sudo apt-get update             

    cal
    Cal command is one of the most widely used Linux commands. Users can fire the cal command from the Linux terminal window to view the time. Linux coders or administrators can also see the calendar of a whole year by firing the following command. It displays the calendar of the whole current year with the prevailing date displayed.

cal -y      

    bc
    bc is one more amazing and super command for Linux users as it enables Linux coders to allow a command-line calculator in the Linux terminal window. Linux programmers can do any computation in the Terminal window itself only. The following command is displaying its use:

$ x=`echo "20+7" | bc`           

    chage
    The Linux command chage is called the change age. This command can be utilized to modify the expiry data of the user’s password. This is an exceptional command for system administrators or Linux administrators. The following command is displaying its use:

chage -h                 

    df
    df is one of the most important Linux commands. With the help of this command, users can retrieve all the data of their file system just by running the df command in the Linux Terminal window.

The following command is displaying its use:

df               

    uname
    uname is one more helpful Linux command to have as it unfolds Linux system data when fired in the Linux Terminal shell. In this command,users can see all system information by typing uname -a in Terminal while

for the information related to kernel release by typing the in uname -r.

And for operating system data, simply type uname -o. The following command is displaying its use:

uname -a                   
