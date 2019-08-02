# helps


[image compression](#image-compression)

[Internet speed test](#speed-test)

[Finding Public IP Addresses (GW) from terminal](#Public-IP-Addresses)

[Private IP range](#Private-IP-range)

[SSH authetication in dockerfile automatic](#Disable-hostcheck)

[Get container id within that container](#Container-ID)

[unknown terminal in dockerfile solution](#UnKnown-terminal-error)

[nfs-mounting inside a container](#nfs-mounting-container)

[java installation](#java-installation)

[nano editor keys](#nano-editor)

[sudo permission unauthenticated](#sudo-permission-unauthenticated)

[ssh passwordless authetication](#ssh-passwordless-authetication)

[ssh passwordless and userless authetication](#ssh-passwordless-userless-authetication)

[scp custom](#scp-custom)

[Tomcat Donwload](#Tomcat-donwload)

[docker env rule](#docker-env)

[ulimit](#ulimit)

[inotify watches](#inotify-watches)

[delete git repository tags](#delete-repo-tags)

[Locale configuration](#Locale-configuration)

[onlline pdf editor](#pdf-editor)

[ASCII Online Creation](#test-2-ASCII)

[Windows Server 2012 R2 -- Free product key](#windows-server-free-product-key)


## windows-server-free-product-key  [Go-Top](#helps)

Once you have installed the evaluation copy you may see that it is not activated and when you try and activate, it will ask for a product key.

If you get this instead of it automatically activating for you, then all you need to do is to run the following command from an elevated command prompt:

    slmgr.vbs -rearm

This should then automatically rearm your trial for 180 days. I have tested this several times, apparently you can rearm your trial version up to five times which will give you around 2 and a half years of Windows Server 2012 R2 .
[link](https://www.quora.com/Can-I-activate-Windows-Server-2012-R2-standard-without-the-product-key)


## test-2-ASCII
[http://patorjk.com/software/taag](http://patorjk.com/software/taag)



## pdf-editor

[https://www.sejda.com/pdf-editor](https://www.sejda.com/pdf-editor)



## Locale-configuration

```
export LANGUAGE="en_US.UTF-8"
echo 'LANGUAGE="en_US.UTF-8"' >> /etc/default/locale
echo 'LC_ALL="en_US.UTF-8"' >> /etc/default/locale      # exit and login again
dpkg-reconfigure locales
```

## image-compression

[http://jpeg-optimizer.com/](http://jpeg-optimizer.com/)


## speed-test

```
curl -s https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py | python -
```
[http://www.speedtest.net](http://www.speedtest.net)

## Public-IP-Addresses
Finding Public IP Addresses (GW) from terminal

```
dig +short myip.opendns.com @resolver1.opendns.com

curl ifconfig.me
curl icanhazip.com
curl ipecho.net/plain
curl ifconfig.co
```

[https://www.cyberciti.biz/faq/how-to-find-my-public-ip-address-from-command-line-on-a-linux/](https://www.cyberciti.biz/faq/how-to-find-my-public-ip-address-from-command-line-on-a-linux/)

## Private-IP-range

```
Class   Private Networks            Subnet Mask     Address Range
A       10.0.0.0                    255.0.0.0       10.0.0.0 - 10.255.255.255
B       172.16.0.0 - 172.31.0.0     255.240.0.0     172.16.0.0 - 172.31.255.255
C       192.168.0.0                 255.255.0.0     192.168.0.0 - 192.168.255.255
```

## Disable-hostcheck
SSH authetication in dockerfile automatic

```
echo "Host github.com\n\tStrictHostKeyChecking no\n" > /root/.ssh/config
```

## Container-ID
Get container id within that container

```
cat /proc/self/cgroup | grep "cpu:/" | sed 's/\([0-9]\):cpu:\/docker\///g'
```

## UnKnown-terminal-error
error : unknown terminal in dockerfile solution

```
export TERM=xterm
```

## nfs-mounting-container
nfs-mounting inside a container

*give privileges for docker container
"--privileged" while running the containier*



## java-installation
(java 1.8)

### oracle-java8
```
apt-get update \
&& echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections \
&& apt-get install -y python-software-properties software-properties-common \
&& add-apt-repository -y ppa:webupd8team/java \
&& apt-get -y update \
&& apt-get install -y nano wget unzip locate oracle-java8-installer \
&& update-java-alternatives --set java-8-oracle \
&& apt-get install oracle-java8-set-default && java -version
```

### OpenJDK
```
apt-get install openjdk-8-jdk -y
```

### Amazon Corretto 8
```
apt-get update
apt-get install java-common
dpkg --install java-1.8.0-amazon-corretto-jdk_8.212.04-2_amd64.deb
```

[https://docs.aws.amazon.com/corretto/latest/corretto-8-ug/generic-linux-install.html
](https://docs.aws.amazon.com/corretto/latest/corretto-8-ug/generic-linux-install.html
)

## nano-editor
for go to a particular line in nano edit

```
nano +107 filename
```
*inside >>*
```
(ctrl) + (shift) + (-)
```

## sudo-permission-unauthenticated
giving user to run sudo without password

```
1) add a user
2) add user in sudo group
3) edit sudoer file 	# nano /etc/sudoers  or  visudo
4) add this line
username ALL=(ALL) NOPASSWD: ALL
```

## ssh-passwordless-authetication
Setup SSH for Auto Login without a Password


*On server*
```
ssh-keygen                # this command will create a .ssh directory under home if it doent exist
ssh-copy-id  servername   # this will copy the public key to server with name of authorized_keys
chmod 600 authorized_keys
```

*or*

```
ssh-keygen -t rsa  # (hit return through prompts)
mv id_rsa.pub >> authorized_keys
chmod 600 authorized_keys
scp authorized_keys user@client ip:/home/ubuntu/.ssh/
check on client side and try to login from server
```
[http://www.rebol.com/docs/ssh-auto-login.html](http://www.rebol.com/docs/ssh-auto-login.html)


## ssh-passwordless-userless-authetication
Setup SSH for Auto Login without a Password and without user

```
cd .ssh
ssh-keygen -t rsa  (hit return through prompts)
mv id_rsa.pub >> authorized_keys
chmod 600 authorized_keys

scp authorized_keys user@client ip:/home/ubuntu/.ssh/
nano .ssh/config
the public key must be provided in that user's .ssh/authorized_keys
```

*Example 1 >>*
```
Host  digital 
Hostname  192.168.1.234
User ubuntu 
IdentityFile /home/ubuntu/Desktop/digital
```

``
ssh digital           # in here, login as ubuntu and private key taken from IdentityFile path
``

*Example 2 >>*
```
Host  akhil
Hostname  192.168.1.235
User root
IdentityFile /home/ubuntu/Desktop/digital
```

``
ssh akhil             # in here, login as root and private key taken from IdentityFile path
``

[http://www.beginninglinux.com/home/server-administration/openssh-keys-certificates-authentication-pem-pub-crt]( http://www.beginninglinux.com/home/server-administration/openssh-keys-certificates-authentication-pem-pub-crt)


## scp-custom
scp with particular port
```
scp -r -P 2233 -i /path/to/name.pem user@ip-address:/path/to/src  /path/to/dest
```

## Tomcat-donwload
tomcat download site

[http://www-us.apache.org/dist/tomcat/](http://www-us.apache.org/dist/tomcat/)



## docker-env

```
env MYSQL_ROOT ubuntu	>> will work 		“_”
env MYSQL-ROOT ubuntu	>> will not work 	“-”
```

## ulimit

[https://www.linkedin.com/pulse/solution-javanetsocketexception-too-many-open-files-divyang-shah](https://www.linkedin.com/pulse/solution-javanetsocketexception-too-many-open-files-divyang-shah)
[https://www.cyberciti.biz/faq/linux-increase-the-maximum-number-of-open-files/](https://www.cyberciti.biz/faq/linux-increase-the-maximum-number-of-open-files/)


## inotify-watches
The user limit on the total number of inotify watches

```
sysctl fs.inotify
echo 999999 | sudo tee -a /proc/sys/fs/inotify/max_user_watches && echo 999999 | sudo tee -a /proc/sys/fs/inotify/max_queued_events && echo 999999 | sudo tee -a /proc/sys/fs/inotify/max_user_instances && sudo sysctl -p
```
[https://github.com/facebook/watchman/issues/163
](https://github.com/facebook/watchman/issues/163
)



## delete-repo-tags
deleting tags form repos in a sec

```
git tag -l
git tag -d $(git tag -l)
git fetch
git push origin --delete $(git tag -l)                # Pushing once should be faster than multiple times.
git tag -d $(git tag -l)
git tag -l
```
