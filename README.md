<div align="center">
  <h1>Command Utils</h1>
  <p>Some useful commands if you are <b>not</b> that familiar with linux and just want to setup a new linux server</p>
</div>

> [!NOTE]  
> All commands are only tested on a Debian 12 machine  
> so they might not work if you are using a different operating system


# Table of contents

- [Basics](#Basics)
- [Nginx](#Nginx)
- [Certbot (For-HTTPS)](#Certbot)
- [Compress folders](#Compress-folders)
- [Upload a file to another server](#Upload-file)

# Basics

### Show running prozesses and RAM, CPU ... usage
> Is equivalent to the windows task manager
```
htop
```

### Navigate to a directory
```
cd <path>
```
> You can use `cd ..` to go to the parent diretory / go back

### Create a directory
```
mkdir <name>
```

### Delete a file
> You can use rm -r <directory> to delete a directory recursively
```
rm <file-name>
```

### View a file
```
cat <file-name>
```

### Create a file
```
touch <file-name>
```

### Copy a file/directory
```
cp -r /path/ /new/path/
```

# [Nginx](https://de.wikipedia.org/wiki/Nginx)

### Install
```
sudo apt update
sudo apt install nginx
```

### Start
```
sudo systemctl start nginx
sudo systemctl enable nginx
```

### Status
```
sudo systemctl status nginx
```

### Restart
```
sudo systemctl restart nginx
```

# Certbot
> For a https connection
### Install
```
sudo apt update
sudo apt install certbot python3-certbot-nginx
```

### Add a domain and get a certificate for it
> **Important**
> The domain must point to your root servers IP
```
sudo certbot --nginx -d yourdomain.com
```

# Compress folders
> Compress files/folders to a tar.gz file

One folder
```
tar -czvf archive.tar.gz /path/to/folder
```
Multiple folders
```
tar -czvf archive.tar.gz /path/to/folder1 /path/to/folder2 /path/to/folder3
```

### Exctract files/folders from tar.gz file
```
tar -xzf archive.tar.gz
```

# Upload file
> In this example we are using the [generated tar.gz](#Compress-folders)

> [!NOTE]   
> You need the password for the `<DestinationServerIP>` to upload the file
```
scp -r /path/archive.tar.gz root@DestinationServerIP:/path
```


# Install JDK 21
```
wget https://download.oracle.com/java/21/latest/jdk-21_linux-x64_bin.tar.gz 
tar -xvf jdk-21_linux-x64_bin.tar.gz 
mv jdk-21.0.6/ /opt/
```

```
sudo nano /etc/profile.d/jdk.sh
```

Add lines:
```
export JAVA_HOME=/opt/jdk-21.0.6
export PATH=$JAVA_HOME/bin:$PATH
```

Close & save file

```
source /etc/profile.d/jdk.sh
```

# Install JDK 25

```
wget https://download.oracle.com/java/25/archive/jdk-25.0.1_linux-x64_bin.tar.gz
tar -xvf jdk-25.0.1_linux-x64_bin.tar.gz
mv jdk-25.0.1/ /opt/
sudo nano /etc/profile.d/jdk.sh
```

Add lines:
```
export JAVA_HOME=/opt/jdk-25.0.1
export PATH=$JAVA_HOME/bin:$PATH
```
```
source /etc/profile.d/jdk.sh
```
