# Wragling Text Files at the Command Line

* Ex1: Viewing file contents

1.1. Viewing file content with the `cat` command
```
theia@theia-lemai0509200:~$ cat entrypoint.sh
#!/bin/bash

if [ -f "$IBMCLOUD_API_KEY_LOCATION" ]; then
  export IBMCLOUD_API_KEY=$(cat $IBMCLOUD_API_KEY_LOCATION)
fi

if [[ ! -z ${IBMCLOUD_API_KEY+x} && "${PRELAUNCH_K8S}" == "true"  ]]; then
  ibmcloud login -r us-south

  echo "Waiting for ${DOCKER_CERT_PATH}/ca.pem"
  timeout=5
  until [ -f ${DOCKER_CERT_PATH}/ca.pem ]
  do
    if [ "$timeout" == 0 ]; then
      echo "ERROR: Timeout while waiting for the file ${DOCKER_CERT_PATH}/ca.pem"
      break
    fi
    sleep 2
    echo "waiting..."
    ((timeout--))
  done

  if [ "$timeout" != 0 ]; then
    echo "${DOCKER_CERT_PATH}/ca.pem found"
    ibmcloud cr login
  fi

  # Set SN_ICR_NAMESPACE for the user
  export SN_ICR_NAMESPACE=$(ibmcloud cr namespace-list | grep sn-labs- | xargs)

  # This will upsert the "icr" secret
  kubectl create secret docker-registry icr --docker-server=us.icr.io --docker-username=iamapikey --docker-password=$IBMCLOUD_API_KEY -o yaml --save-config --dry-run=client | kubectl apply -f -

  # Set the SN context
  export SN_KUBECTL_CONTEXT=$(kubectl config current-context)

  if [ -z ${SN_ICR_NAMESPACE+x} ]; then
    echo "ERROR: SN_ICR_NAMESPACE not set"
    exit 1
  fi
fi

if [ ! -z ${DHT+x} ]; then
  DHT_DECODED=$(echo $DHT | base64 -d)
  DHT_PARTS=(${DHT_DECODED//:/ })

  docker login -u ${DHT_PARTS[0]} -p ${DHT_PARTS[1]}
  kubectl create secret docker-registry dh --docker-server=index.docker.io/v2 --docker-username=${DHT_PARTS[0]} --docker-password=${DHT_PARTS[1]}
fi

chmod go-r /etc/kube/config

export MONGO_PASSWORD="$(echo "$RANDOM-$USERNAME-$RANDOM" | base64 | cut -c1-16)"
export CASSANDRA_PASSWORD="$(echo "$RANDOM-$USERNAME-$RANDOM" | base64 | cut -c1-16)"
export MYSQL_PASSWORD="$(echo "$RANDOM-$USERNAME-$RANDOM" | base64 | cut -c1-16)"
export POSTGRES_PASSWORD="$(echo "$RANDOM-$USERNAME-$RANDOM" | base64 | cut -c1-16)"
export PGPASSWORD="$POSTGRES_PASSWORD"
export AIRFLOW_PASSWORD="$(echo "$RANDOM-$USERNAME-$RANDOM" | base64 | cut -c1-16)"
export _AIRFLOW_WWW_USER_PASSWORD="$AIRFLOW_PASSWORD"

export PATH=$PATH:/home/theia/.local/bin

sudo service cron start

yarn theia start /home/project --hostname=0.0.0.0 --port=$THEIA_LOCAL_PORT
```
1.2. Viewing file content with the `more` command
```
theia@theia-lemai0509200:~$ more entrypoint.sh
```
1.3. Scrolling through file content with the `less` command
```
theia@theia-lemai0509200:~$ less entrypoint.sh
```
* Ex2: Viewing text file contents

2.1 Display the first N lines of a file
```
theia@theia-lemai0509200:/home/project$ head -5  usdoi.txt
The unanimous Declaration of the thirteen united States of America, When in the
Course of human events, it becomes necessary for one people to dissolve the
political bands which have connected them with another, and to assume among the
powers of the earth, the separate and equal station to which the Laws of Nature
and of Nature's God entitle them, a decent respect to the opinions of mankind
```
2.2. Display the last N lines of a file
```
theia@theia-lemai0509200:/home/project$ tail -9 usdoi.txt
Colonies are, and of Right ought to be Free and Independent States; that they
are Absolved from all Allegiance to the British Crown, and that all political
connection between them and the State of Great Britain, is and ought to be
totally dissolved; and that as Free and Independent States, they have full
Power to levy War, conclude Peace, contract Alliances, establish Commerce, and
to do all other Acts and Things which Independent States may of right do. And
for the support of this Declaration, with a firm reliance on the protection of
divine Providence, we mutually pledge to each other our Lives, our Fortunes and
our sacred Honor.
```

* Ex3: Getting basic text file stats

3.1. Count lines, words, or characters from a text file
```
theia@theia-lemai0509200:/home/project$ wc usdoi.txt
 152 1330 8121 usdoi.txt
theia@theia-lemai0509200:/home/project$ wc -l usdoi.txt
152 usdoi.txt
theia@theia-lemai0509200:/home/project$ wc -w usdoi.txt
1330 usdoi.txt
theia@theia-lemai0509200:/home/project$ wc -c usdoi.txt
8121 usdoi.txt
```
* Ex4: Basic text wrangling: sorting lines and dropping duplicates

4.1. Sort and display lines of file alphanumerically
```
theia@theia-lemai0509200:/home/project$ sort usdoi.txt
```

4.2. Drop consecutive duplicated lines and display result
```
theia@theia-lemai0509200:/home/project$ cat zoo.txt
zebra
zebra
lion
lion
anaconda
zebra
zebra
lion
zebra
theia@theia-lemai0509200:/home/project$ uniq zoo.txt
zebra
lion
anaconda
zebra
lion
zebra
```
* Ex5: Basic text wrangling: extracting lines and fields

5.1. Extract lines matching a specified criterion
```
theia@theia-lemai0509200:/home/project$ grep people usdoi.txt
Course of human events, it becomes necessary for one `people` to dissolve the
`people`, unless those `people` would relinquish the right of Representation in the
firmness his invasions on the rights of the `people`.
to harrass our `people`, and eat out their substance.
the lives of our `people`.
Tyrant, is unfit to be the ruler of a free `people`.
```

5.2. Extract fields from lines of text
```
theia@theia-lemai0509200:/home/project$ cut -c -2 zoo.txt
ze
ze
li
li
an
ze
ze
li
ze

theia@theia-lemai0509200:/home/project$ cat names_and_numbers.csv
John Fogerty, 555-1212
Jane Doe, 555-1312
theia@theia-lemai0509200:/home/project$ cut -d "," -f2 names_and_numbers.csv
 555-1212
 555-1312
```
* Ex6: Basic text wrangling: merging lines as fields

6.1. Merge text files line-by-line, aligned as columns
```
theia@theia-lemai0509200:/home/project$ paste zoo.txt zoo_ages.txt
zebra   17
zebra   12
lion    7
lion    4
anaconda        3
zebra   4
zebra   1
lion    0
zebra   1
```
* Practice exercises
1. Display the number of lines in the `/etc/passwd file`.
```
theia@theia-lemai0509200:~$ wc -l /etc/passwd
25 /etc/passwd
```

2. Display the lines that contain the string `"not installed"` in `/var/log/bootstrap.log`.
```
theia@theia-lemai0509200:~$ grep "not installed" /var/log/bootstrap.log
  Package libc6 is not installed.
  Package libdebconfclient0 is not installed.
  awk is not installed.
  Package awk is not installed.
  libbz2-1.0 is not installed.
  libc6 is not installed.
  liblzma5 is not installed.
  libselinux1 is not installed.
  libzstd1 is not installed.
  zlib1g is not installed.
  Package libbz2-1.0 is not installed.
  Package libc6 is not installed.
  Package liblzma5 is not installed.
  Package libselinux1 is not installed.
  Package libzstd1 is not installed.
  Package zlib1g is not installed.
  Package tar is not installed.
  Package libgcc1 is not installed.
  libtinfo5 is not installed.
  libsystemd0 is not installed.
  libacl1 is not installed.
  libattr1 is not installed.
  libselinux1 is not installed.
  libbz2-1.0 is not installed.
  liblzma5 is not installed.
  libselinux1 is not installed.
  libzstd1 is not installed.
  zlib1g is not installed.
  libblkid1 is not installed.
  libcom-err2 is not installed.
  libext2fs2 is not installed.
  libss2 is not installed.
  libuuid1 is not installed.
  libselinux1 is not installed.
  libpcre3 is not installed.
  libpam0g is not installed.
  libselinux1 is not installed.
  libpam-modules-bin is not installed.
  zlib1g is not installed.
```
3. The text file at `https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0250EN-SkillsNetwork/labs/Bash%20Scripting/top-sites.txt` contains a list of popular websites. Find all the websites on the list that have the word `"org"` in them.
```
theia@theia-lemai0509200:~$ wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0250EN-SkillsNetwork/labs/Bash%20Scripting/top-sites.txt--2023-09-07 05:38:33--  https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0250EN-SkillsNetwork/labs/Bash%20Scripting/top-sites.txt
Resolving cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud (cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud)... 169.63.118.104
Connecting to cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud (cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud)|169.63.118.104|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1311 (1.3K) [text/plain]
Saving to: ‘top-sites.txt’

top-sites.txt        100%[===================>]   1.28K  --.-KB/s    in 0s      

2023-09-07 05:38:33 (171 MB/s) - ‘top-sites.txt’ saved [1311/1311]

theia@theia-lemai0509200:~$ grep "org" top-sites.txt
en.wikipedia.org
wordpress.org
mozilla.org
pt.wikipedia.org
es.wikipedia.org
w3.org
wikimedia.org
creativecommons.org
fr.wikipedia.org
apache.org
id.wikipedia.org
de.wikipedia.org
```
4. Print the first seven lines of `top-sites.txt`
```
theia@theia-lemai0509200:~$ head -7 top-sites.txt
youtube.com
www.google.com
apple.com
microsoft.com
cloudflare.com
play.google.com
support.google.com
```

5. Print the last seven lines of `top-sites.txt.`
```
theia@theia-lemai0509200:~$ tail -7 top-sites.txt
id.wikipedia.org
rakuten.co.jp
tinyurl.com
amazon.co.jp
de.wikipedia.org
tools.google.com
buydomains.com
```
6. Print the first three characters of each line from `top-sites.txt.`
```
theia@theia-lemai0509200:~$ cut -c -3 top-sites.txt
you
www
app
mic
clo
pla
...
```
7. Extract and view only the names, without their phone numbers, from the file `names_and_numbers.csv.`
```
theia@theia-lemai0509200:~$ cd /home/project
theia@theia-lemai0509200:/home/project$ cut -d "," -f 1 names_and_numbers.csv
John Fogerty
Jane Doe
```
# Working with network commands

* Ex1: View configuration info about your network

1.1. Display your system's hostname and IP address
```
theia@theia-lemai0509200:/home/project$ hostname
theia-lemai0509200
theia@theia-lemai0509200:/home/project$ hostname -i
172.22.180.113
```
1.2. Display network interface configuration
```
theia@theia-lemai0509200:/home/project$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1480
        inet 172.22.180.113  netmask 255.255.255.255  broadcast 0.0.0.0
        inet6 fe80::18ba:78ff:fed8:10ca  prefixlen 64  scopeid 0x20<link>
        ether 1a:ba:78:d8:10:ca  txqueuelen 0  (Ethernet)
        RX packets 16853  bytes 28473758 (28.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 13550  bytes 26345169 (26.3 MB)
        TX errors 0  dropped 1 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 32979  bytes 97386263 (97.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 32979  bytes 97386263 (97.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
* Ex2: Test network connectivity

2.1. Test connectivity to a host
```
theia@theia-lemai0509200:/home/project$ ping -c 5 www.google.com
PING www.google.com (142.251.16.105): 56 data bytes
64 bytes from 142.251.16.105: icmp_seq=0 ttl=105 time=1.248 ms
64 bytes from 142.251.16.105: icmp_seq=1 ttl=105 time=1.236 ms
64 bytes from 142.251.16.105: icmp_seq=2 ttl=105 time=1.228 ms
64 bytes from 142.251.16.105: icmp_seq=3 ttl=105 time=1.225 ms
64 bytes from 142.251.16.105: icmp_seq=4 ttl=105 time=1.315 ms
--- www.google.com ping statistics ---
5 packets transmitted, 5 packets received, 0% packet loss
round-trip min/avg/max/stddev = 1.225/1.250/1.315/0.033 ms
```
* Ex3: View or download data from a server

3.1. Transfer data from a server
```
theia@theia-lemai0509200:/home/project$ curl https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0250EN-SkillsNetwork/labs/Bash%20Scripting/usdoi.txt
```

3.2 Download file(s) from a URL
```
theia@theia-lemai0509200:/home/project$ rm usdoi.txt
theia@theia-lemai0509200:/home/project$ wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0250EN-SkillsNetwork/labs/Bash%20Scripting/usdoi.txt
--2023-09-07 05:56:34--  https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0250EN-SkillsNetwork/labs/Bash%20Scripting/usdoi.txt
Resolving cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud (cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud)... 169.63.118.104
Connecting to cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud (cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud)|169.63.118.104|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8121 (7.9K) [text/plain]
Saving to: ‘usdoi.txt’

usdoi.txt            100%[===================>]   7.93K  --.-KB/s    in 0s      

2023-09-07 05:56:34 (978 MB/s) - ‘usdoi.txt’ saved [8121/8121]
```
* Practice exercises

1. Display your host's IP address.
```
theia@theia-lemai0509200:/home/project$ hostname -i
172.22.180.113
```
2. Get connectivity stats on your connection to `www.google.com.`
```
theia@theia-lemai0509200:/home/project$ ping -c 2 www.google.com
PING www.google.com (172.253.115.147): 56 data bytes
64 bytes from 172.253.115.147: icmp_seq=0 ttl=105 time=1.739 ms
64 bytes from 172.253.115.147: icmp_seq=1 ttl=105 time=1.795 ms
--- www.google.com ping statistics ---
2 packets transmitted, 2 packets received, 0% packet loss
round-trip min/avg/max/stddev = 1.739/1.767/1.795/0.028 ms
```
3. View info about your ethernet adapter `eth0`.
```
theia@theia-lemai0509200:/home/project$ ifconfig eth0
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1480
        inet 172.22.180.113  netmask 255.255.255.255  broadcast 0.0.0.0
        inet6 fe80::18ba:78ff:fed8:10ca  prefixlen 64  scopeid 0x20<link>
        ether 1a:ba:78:d8:10:ca  txqueuelen 0  (Ethernet)
        RX packets 18745  bytes 28827941 (28.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 15180  bytes 26689226 (26.6 MB)
        TX errors 0  dropped 1 overruns 0  carrier 0  collisions 0
```
4. View the HTML code for `www.google.com`'s landing page.
```
theia@theia-lemai0509200:/home/project$ curl www.google.com
```
5. Download the HTML code for www.google.com's landing page.
```
theia@theia-lemai0509200:/home/project$ wget www.google.com
--2023-09-07 06:01:45--  http://www.google.com/
Resolving www.google.com (www.google.com)... 142.251.16.106, 142.251.16.147, 142.251.16.105, ...
Connecting to www.google.com (www.google.com)|142.251.16.106|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: ‘index.html’

index.html               [ <=>                ]  18.20K  --.-KB/s    in 0.001s  

2023-09-07 06:01:45 (35.3 MB/s) - ‘index.html’ saved [18639]

theia@theia-lemai0509200:/home/project$ ls -l
total 40
-rw-r--r-- 1 theia users 18639 Sep  7 06:01 index.html
-rw-r--r-- 1 theia users    42 May 15 14:56 names_and_numbers.csv
-rw-r--r-- 1 theia users  8121 Sep 21  2022 usdoi.txt
-rw-r--r-- 1 theia users    20 Sep 28  2022 zoo_ages.txt
-rw-r--r-- 1 theia users    54 Sep 28  2022 zoo.txt
```
# Archiving and compressing files

* Ex 1: File and folder archiving and compression

1.1. Create and manage file archives
```
theia@theia-lemai0509200:/home/project$ tar -cvf bin.tar /bin
tar: Removing leading `/' from member names
/bin/
/bin/zdiff
/bin/su
/bin/more
/bin/mountpoint
/bin/uname
/bin/uncompress
/bin/which
/bin/gzip
/bin/domainname
/bin/run-parts
/bin/mknod
/bin/znew
/bin/dmesg
/bin/wdctl
/bin/bzexe
/bin/bzegrep
/bin/kill
/bin/false
/bin/echo
/bin/rbash
/bin/bzcmp
/bin/bunzip2
/bin/zcmp
/bin/stty
/bin/ypdomainname
/bin/bzless
tar: Removing leading `/' from hard link targets
/bin/bzip2
/bin/mktemp
/bin/cp
/bin/tar
/bin/readlink
/bin/nisdomainname
/bin/dnsdomainname
/bin/ls
/bin/login
/bin/zcat
/bin/egrep
/bin/umount
/bin/bash
/bin/sh.distrib
/bin/tempfile
/bin/bzcat
/bin/dash
/bin/ps
/bin/bzfgrep
/bin/chmod
/bin/zgrep
/bin/findmnt
/bin/gunzip
/bin/pwd
/bin/bzip2recover
/bin/zmore
/bin/pidof
/bin/lsblk
/bin/gzexe
/bin/vdir
/bin/dir
/bin/bzdiff
/bin/bzgrep
/bin/chgrp
/bin/zfgrep
/bin/cat
/bin/sleep
/bin/sed
/bin/fgrep
/bin/mount
/bin/chown
/bin/hostname
/bin/bzmore
/bin/sh
/bin/mv
/bin/date
/bin/ln
/bin/rmdir
/bin/true
/bin/zless
/bin/df
/bin/zegrep
/bin/zforce
/bin/mkdir
/bin/sync
/bin/touch
/bin/grep
/bin/rm
/bin/dd
/bin/ping6
/bin/ping
/bin/rnano
/bin/netstat
/bin/nano
/bin/fuser
/bin/lesspipe
/bin/less
/bin/lesskey
/bin/lessfile
/bin/lessecho
theia@theia-lemai0509200:/home/project$ tar -tvf bin.tar
drwxr-xr-x root/root         0 2023-02-27 12:29 bin/
-rwxr-xr-x root/root      5782 2022-04-08 07:12 bin/zdiff
-rwsr-xr-x root/root     44664 2022-11-29 07:25 bin/su
-rwxr-xr-x root/root     38952 2020-09-16 14:43 bin/more
-rwxr-xr-x root/root     14408 2020-09-16 14:43 bin/mountpoint
-rwxr-xr-x root/root     35032 2018-01-18 04:43 bin/uname
-rwxr-xr-x root/root      2301 2022-04-08 07:12 bin/uncompress
-rwxr-xr-x root/root       946 2017-12-30 13:15 bin/which
-rwxr-xr-x root/root    101560 2022-04-08 07:12 bin/gzip
lrwxrwxrwx root/root         0 2018-01-31 07:08 bin/domainname -> hostname
-rwxr-xr-x root/root     18760 2017-12-30 13:15 bin/run-parts
-rwxr-xr-x root/root     67768 2018-01-18 04:43 bin/mknod
-rwxr-xr-x root/root      5071 2022-04-08 07:12 bin/znew
-rwxr-xr-x root/root     72000 2020-09-16 14:43 bin/dmesg
-rwxr-xr-x root/root     30800 2020-09-16 14:43 bin/wdctl
-rwxr-xr-x root/root      4877 2019-07-04 08:35 bin/bzexe
lrwxrwxrwx root/root         0 2019-07-04 08:35 bin/bzegrep -> bzgrep
-rwxr-xr-x root/root     26704 2019-08-09 11:37 bin/kill
-rwxr-xr-x root/root     30904 2018-01-18 04:43 bin/false
-rwxr-xr-x root/root     35000 2018-01-18 04:43 bin/echo
lrwxrwxrwx root/root         0 2022-04-18 11:08 bin/rbash -> bash
lrwxrwxrwx root/root         0 2019-07-04 08:35 bin/bzcmp -> bzdiff
-rwxr-xr-x root/root     34888 2019-07-04 08:35 bin/bunzip2
-rwxr-xr-x root/root      1777 2022-04-08 07:12 bin/zcmp
-rwxr-xr-x root/root     75992 2018-01-18 04:43 bin/stty
lrwxrwxrwx root/root         0 2018-01-31 07:08 bin/ypdomainname -> hostname
lrwxrwxrwx root/root         0 2019-07-04 08:35 bin/bzless -> bzmore
hrwxr-xr-x root/root         0 2019-07-04 08:35 bin/bzip2 link to bin/bunzip2
-rwxr-xr-x root/root     43192 2018-01-18 04:43 bin/mktemp
-rwxr-xr-x root/root    141528 2018-01-18 04:43 bin/cp
-rwxr-xr-x root/root    423312 2022-03-15 08:58 bin/tar
-rwxr-xr-x root/root     43192 2018-01-18 04:43 bin/readlink
lrwxrwxrwx root/root         0 2018-01-31 07:08 bin/nisdomainname -> hostname
lrwxrwxrwx root/root         0 2018-01-31 07:08 bin/dnsdomainname -> hostname
-rwxr-xr-x root/root    133792 2018-01-18 04:43 bin/ls
-rwxr-xr-x root/root     52664 2022-11-29 07:25 bin/login
-rwxr-xr-x root/root      1937 2022-04-08 07:12 bin/zcat
-rwxr-xr-x root/root        28 2019-09-18 11:00 bin/egrep
-rwsr-xr-x root/root     26696 2020-09-16 14:43 bin/umount
-rwxr-xr-x root/root   1113504 2022-04-18 11:08 bin/bash
lrwxrwxrwx root/root         0 2023-01-26 03:31 bin/sh.distrib -> dash
-rwxr-xr-x root/root     10104 2017-12-30 13:15 bin/tempfile
hrwxr-xr-x root/root         0 2019-07-04 08:35 bin/bzcat link to bin/bunzip2
-rwxr-xr-x root/root    121432 2018-01-25 02:14 bin/dash
-rwxr-xr-x root/root    133432 2019-08-09 11:37 bin/ps
lrwxrwxrwx root/root         0 2019-07-04 08:35 bin/bzfgrep -> bzgrep
-rwxr-xr-x root/root     59608 2018-01-18 04:43 bin/chmod
-rwxr-xr-x root/root      6456 2022-04-08 07:12 bin/zgrep
-rwxr-xr-x root/root     64784 2020-09-16 14:43 bin/findmnt
hrwxr-xr-x root/root         0 2022-04-08 07:12 bin/gunzip link to bin/uncompress
-rwxr-xr-x root/root     35000 2018-01-18 04:43 bin/pwd
-rwxr-xr-x root/root     14328 2019-07-04 08:35 bin/bzip2recover
-rwxr-xr-x root/root      1910 2022-04-08 07:12 bin/zmore
lrwxrwxrwx root/root         0 2017-11-01 17:00 bin/pidof -> /sbin/killall5
-rwxr-xr-x root/root     84048 2020-09-16 14:43 bin/lsblk
-rwxr-xr-x root/root      5998 2022-04-08 07:12 bin/gzexe
-rwxr-xr-x root/root    133792 2018-01-18 04:43 bin/vdir
-rwxr-xr-x root/root    133792 2018-01-18 04:43 bin/dir
-rwxr-xr-x root/root      2140 2019-07-04 08:35 bin/bzdiff
-rwxr-xr-x root/root      3642 2019-07-04 08:35 bin/bzgrep
-rwxr-xr-x root/root     63672 2018-01-18 04:43 bin/chgrp
-rwxr-xr-x root/root       140 2022-04-08 07:12 bin/zfgrep
-rwxr-xr-x root/root     35064 2018-01-18 04:43 bin/cat
-rwxr-xr-x root/root     35000 2018-01-18 04:43 bin/sleep
-rwxr-xr-x root/root    109000 2018-01-29 21:49 bin/sed
-rwxr-xr-x root/root        28 2019-09-18 11:00 bin/fgrep
-rwsr-xr-x root/root     43088 2020-09-16 14:43 bin/mount
-rwxr-xr-x root/root     67768 2018-01-18 04:43 bin/chown
-rwxr-xr-x root/root     18504 2018-01-31 07:08 bin/hostname
-rwxr-xr-x root/root      1297 2019-07-04 08:35 bin/bzmore
lrwxrwxrwx root/root         0 2023-01-26 03:31 bin/sh -> dash
-rwxr-xr-x root/root    137440 2018-01-18 04:43 bin/mv
-rwxr-xr-x root/root    100568 2018-01-18 04:43 bin/date
-rwxr-xr-x root/root     67808 2018-01-18 04:43 bin/ln
-rwxr-xr-x root/root     43192 2018-01-18 04:43 bin/rmdir
-rwxr-xr-x root/root     30904 2018-01-18 04:43 bin/true
-rwxr-xr-x root/root      2037 2022-04-08 07:12 bin/zless
-rwxr-xr-x root/root     84776 2018-01-18 04:43 bin/df
-rwxr-xr-x root/root       140 2022-04-08 07:12 bin/zegrep
-rwxr-xr-x root/root      2131 2022-04-08 07:12 bin/zforce
-rwxr-xr-x root/root     80056 2018-01-18 04:43 bin/mkdir
-rwxr-xr-x root/root     35000 2018-01-18 04:43 bin/sync
-rwxr-xr-x root/root     88280 2018-01-18 04:43 bin/touch
-rwxr-xr-x root/root    219456 2019-09-18 11:00 bin/grep
-rwxr-xr-x root/root     63704 2018-01-18 04:43 bin/rm
-rwxr-xr-x root/root     76000 2018-01-18 04:43 bin/dd
-rwsr-xr-x root/root     64888 2021-08-16 09:37 bin/ping6
-rwsr-xr-x root/root     74072 2021-08-16 09:37 bin/ping
lrwxrwxrwx root/root         0 2018-03-06 09:46 bin/rnano -> nano
-rwxr-xr-x root/root    154192 2017-01-09 23:25 bin/netstat
-rwxr-xr-x root/root    245872 2018-03-06 09:46 bin/nano
-rwxr-xr-x root/root     35928 2018-12-11 10:46 bin/fuser
-rwxr-xr-x root/root      8564 2017-11-30 23:11 bin/lesspipe
-rwxr-xr-x root/root    170760 2017-11-30 23:11 bin/less
-rwxr-xr-x root/root     19856 2017-11-30 23:11 bin/lesskey
lrwxrwxrwx root/root         0 2017-11-30 23:11 bin/lessfile -> lesspipe
-rwxr-xr-x root/root     10256 2017-11-30 23:11 bin/lessecho
theia@theia-lemai0509200:/home/project$ tar -xvf bin.tar
bin/
bin/zdiff
bin/su
bin/more
bin/mountpoint
bin/uname
bin/uncompress
bin/which
bin/gzip
bin/domainname
bin/run-parts
bin/mknod
bin/znew
bin/dmesg
bin/wdctl
bin/bzexe
bin/bzegrep
bin/kill
bin/false
bin/echo
bin/rbash
bin/bzcmp
bin/bunzip2
bin/zcmp
bin/stty
bin/ypdomainname
bin/bzless
bin/bzip2
bin/mktemp
bin/cp
bin/tar
bin/readlink
bin/nisdomainname
bin/dnsdomainname
bin/ls
bin/login
bin/zcat
bin/egrep
bin/umount
bin/bash
bin/sh.distrib
bin/tempfile
bin/bzcat
bin/dash
bin/ps
bin/bzfgrep
bin/chmod
bin/zgrep
bin/findmnt
bin/gunzip
bin/pwd
bin/bzip2recover
bin/zmore
bin/pidof
bin/lsblk
bin/gzexe
bin/vdir
bin/dir
bin/bzdiff
bin/bzgrep
bin/chgrp
bin/zfgrep
bin/cat
bin/sleep
bin/sed
bin/fgrep
bin/mount
bin/chown
bin/hostname
bin/bzmore
bin/sh
bin/mv
bin/date
bin/ln
bin/rmdir
bin/true
bin/zless
bin/df
bin/zegrep
bin/zforce
bin/mkdir
bin/sync
bin/touch
bin/grep
bin/rm
bin/dd
bin/ping6
bin/ping
bin/rnano
bin/netstat
bin/nano
bin/fuser
bin/lesspipe
bin/less
bin/lesskey
bin/lessfile
bin/lessecho
theia@theia-lemai0509200:/home/project$ ls -l
total 5616
drwxr-sr-x 2 theia users    4096 Feb 27  2023 bin
-rw-r--r-- 1 theia users 5703680 Sep  7 06:08 bin.tar
-rw-r--r-- 1 theia users   18639 Sep  7 06:01 index.html
-rw-r--r-- 1 theia users      42 May 15 14:56 names_and_numbers.csv
-rw-r--r-- 1 theia users    8121 Sep 21  2022 usdoi.txt
-rw-r--r-- 1 theia users      20 Sep 28  2022 zoo_ages.txt
-rw-r--r-- 1 theia users      54 Sep 28  2022 zoo.txt
```
1.2. Package and compress archive files
```
theia@theia-lemai0509200:/home/project$ zip config.zip /etc/*.conf
  adding: etc/adduser.conf (deflated 55%)
  adding: etc/ca-certificates.conf (deflated 74%)
  adding: etc/debconf.conf (deflated 56%)
  adding: etc/deluser.conf (deflated 40%)
  adding: etc/gai.conf (deflated 57%)
  adding: etc/host.conf (deflated 13%)
  adding: etc/ld.so.conf (deflated 6%)
  adding: etc/libaudit.conf (deflated 34%)
  adding: etc/logrotate.conf (deflated 50%)
  adding: etc/mke2fs.conf (deflated 58%)
  adding: etc/mongodb.conf (deflated 52%)
  adding: etc/nsswitch.conf (deflated 49%)
  adding: etc/ntp.conf (deflated 52%)
  adding: etc/pam.conf (deflated 62%)
  adding: etc/resolv.conf (deflated 27%)
  adding: etc/sensors3.conf (deflated 82%)
  adding: etc/sysctl.conf (deflated 61%)
  adding: etc/ucf.conf (deflated 61%)
theia@theia-lemai0509200:/home/project$ zip -r bin.zip /bin
  adding: bin/ (stored 0%)
  adding: bin/zdiff (deflated 66%)
  adding: bin/su (deflated 61%)
  adding: bin/more (deflated 52%)
  adding: bin/mountpoint (deflated 68%)
  adding: bin/uname (deflated 58%)
  adding: bin/uncompress (deflated 50%)
  adding: bin/which (deflated 51%)
  adding: bin/gzip (deflated 48%)
  adding: bin/domainname (deflated 67%)
  adding: bin/run-parts (deflated 58%)
  adding: bin/mknod (deflated 53%)
  adding: bin/znew (deflated 59%)
  adding: bin/dmesg (deflated 60%)
  adding: bin/wdctl (deflated 55%)
  adding: bin/bzexe (deflated 59%)
  adding: bin/bzegrep (deflated 56%)
  adding: bin/kill (deflated 61%)
  adding: bin/false (deflated 57%)
  adding: bin/echo (deflated 58%)
  adding: bin/rbash (deflated 52%)
  adding: bin/bzcmp (deflated 58%)
  adding: bin/bunzip2 (deflated 56%)
  adding: bin/zcmp (deflated 49%)
  adding: bin/stty (deflated 58%)
  adding: bin/ypdomainname (deflated 67%)
  adding: bin/bzless (deflated 50%)
  adding: bin/bzip2 (deflated 56%)
  adding: bin/mktemp (deflated 56%)
  adding: bin/cp (deflated 53%)
  adding: bin/tar (deflated 53%)
  adding: bin/readlink (deflated 54%)
  adding: bin/nisdomainname (deflated 67%)
  adding: bin/dnsdomainname (deflated 67%)
  adding: bin/ls (deflated 54%)
  adding: bin/login (deflated 58%)
  adding: bin/zcat (deflated 49%)
  adding: bin/egrep (stored 0%)
  adding: bin/umount (deflated 60%)
  adding: bin/bash (deflated 52%)
  adding: bin/sh.distrib (deflated 51%)
  adding: bin/tempfile (deflated 66%)
  adding: bin/bzcat (deflated 56%)
  adding: bin/dash (deflated 51%)
  adding: bin/ps (deflated 65%)
  adding: bin/bzfgrep (deflated 56%)
  adding: bin/chmod (deflated 52%)
  adding: bin/zgrep (deflated 61%)
  adding: bin/findmnt (deflated 59%)
  adding: bin/gunzip (deflated 50%)
  adding: bin/pwd (deflated 56%)
  adding: bin/bzip2recover (deflated 64%)
  adding: bin/zmore (deflated 49%)
  adding: bin/pidof (deflated 61%)
  adding: bin/lsblk (deflated 58%)
  adding: bin/gzexe (deflated 61%)
  adding: bin/vdir (deflated 54%)
  adding: bin/dir (deflated 54%)
  adding: bin/bzdiff (deflated 58%)
  adding: bin/bzgrep (deflated 56%)
  adding: bin/chgrp (deflated 53%)
  adding: bin/zfgrep (deflated 27%)
  adding: bin/cat (deflated 54%)
  adding: bin/sleep (deflated 58%)
  adding: bin/sed (deflated 51%)
  adding: bin/fgrep (stored 0%)
  adding: bin/mount (deflated 59%)
  adding: bin/chown (deflated 54%)
  adding: bin/hostname (deflated 67%)
  adding: bin/bzmore (deflated 50%)
  adding: bin/sh (deflated 51%)
  adding: bin/mv (deflated 52%)
  adding: bin/date (deflated 52%)
  adding: bin/ln (deflated 54%)
  adding: bin/rmdir (deflated 55%)
  adding: bin/true (deflated 57%)
  adding: bin/zless (deflated 47%)
  adding: bin/df (deflated 51%)
  adding: bin/zegrep (deflated 27%)
  adding: bin/zforce (deflated 48%)
  adding: bin/mkdir (deflated 52%)
  adding: bin/sync (deflated 59%)
  adding: bin/touch (deflated 52%)
  adding: bin/grep (deflated 53%)
  adding: bin/rm (deflated 52%)
  adding: bin/dd (deflated 53%)
  adding: bin/ping6 (deflated 50%)
  adding: bin/ping (deflated 50%)
  adding: bin/rnano (deflated 51%)
  adding: bin/netstat (deflated 61%)
  adding: bin/nano (deflated 51%)
  adding: bin/fuser (deflated 57%)
  adding: bin/lesspipe (deflated 68%)
  adding: bin/less (deflated 54%)
  adding: bin/lesskey (deflated 64%)
  adding: bin/lessfile (deflated 68%)
  adding: bin/lessecho (deflated 68%)
```
1.3. Extract, list, or test compressed files in a ZIP archive
```
theia@theia-lemai0509200:/home/project$ unzip -l config.zip
Archive:  config.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
     3028  2023-01-26 03:31   etc/adduser.conf
     5432  2023-02-27 12:12   etc/ca-certificates.conf
     2969  2018-02-28 04:50   etc/debconf.conf
      604  2017-08-13 14:17   etc/deluser.conf
     2584  2018-02-01 11:17   etc/gai.conf
       92  2018-04-09 07:10   etc/host.conf
       34  2016-01-27 09:17   etc/ld.so.conf
      191  2018-02-07 18:59   etc/libaudit.conf
      703  2017-08-21 13:38   etc/logrotate.conf
      812  2018-03-24 15:13   etc/mke2fs.conf
     2154  2019-03-22 09:34   etc/mongodb.conf
      497  2016-10-05 15:57   etc/nsswitch.conf
     2517  2020-08-17 21:58   etc/ntp.conf
      552  2018-04-04 17:56   etc/pam.conf
      115  2023-09-07 05:17   etc/resolv.conf
    10368  2022-03-31 16:53   etc/sensors3.conf
     2683  2018-01-17 17:35   etc/sysctl.conf
     1260  2018-02-25 19:58   etc/ucf.conf
---------                     -------
    36595                     18 files

theia@theia-lemai0509200:/home/project$ unzip bin.zip
Archive:  bin.zip
replace bin/zdiff? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: bin/zdiff               
replace bin/su? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
  inflating: bin/su                  
  inflating: bin/more                
  inflating: bin/mountpoint          
  inflating: bin/uname               
  inflating: bin/uncompress          
  inflating: bin/which               
  inflating: bin/gzip                
  inflating: bin/domainname          
  inflating: bin/run-parts           
  inflating: bin/mknod               
  inflating: bin/znew                
  inflating: bin/dmesg               
  inflating: bin/wdctl               
  inflating: bin/bzexe               
  inflating: bin/bzegrep             
  inflating: bin/kill                
  inflating: bin/false               
  inflating: bin/echo                
  inflating: bin/rbash               
  inflating: bin/bzcmp               
  inflating: bin/bunzip2             
  inflating: bin/zcmp                
  inflating: bin/stty                
  inflating: bin/ypdomainname        
  inflating: bin/bzless              
  inflating: bin/bzip2               
  inflating: bin/mktemp              
  inflating: bin/cp                  
  inflating: bin/tar                 
  inflating: bin/readlink            
  inflating: bin/nisdomainname       
  inflating: bin/dnsdomainname       
  inflating: bin/ls                  
  inflating: bin/login               
  inflating: bin/zcat                
 extracting: bin/egrep               
  inflating: bin/umount              
  inflating: bin/bash                
  inflating: bin/sh.distrib          
  inflating: bin/tempfile            
  inflating: bin/bzcat               
  inflating: bin/dash                
  inflating: bin/ps                  
  inflating: bin/bzfgrep             
  inflating: bin/chmod               
  inflating: bin/zgrep               
  inflating: bin/findmnt             
  inflating: bin/gunzip              
  inflating: bin/pwd                 
  inflating: bin/bzip2recover        
  inflating: bin/zmore               
  inflating: bin/pidof               
  inflating: bin/lsblk               
  inflating: bin/gzexe               
  inflating: bin/vdir                
  inflating: bin/dir                 
  inflating: bin/bzdiff              
  inflating: bin/bzgrep              
  inflating: bin/chgrp               
  inflating: bin/zfgrep              
  inflating: bin/cat                 
  inflating: bin/sleep               
  inflating: bin/sed                 
 extracting: bin/fgrep               
  inflating: bin/mount               
  inflating: bin/chown               
  inflating: bin/hostname            
  inflating: bin/bzmore              
  inflating: bin/sh                  
  inflating: bin/mv                  
  inflating: bin/date                
  inflating: bin/ln                  
  inflating: bin/rmdir               
  inflating: bin/true                
  inflating: bin/zless               
  inflating: bin/df                  
  inflating: bin/zegrep              
  inflating: bin/zforce              
  inflating: bin/mkdir               
  inflating: bin/sync                
  inflating: bin/touch               
  inflating: bin/grep                
  inflating: bin/rm                  
  inflating: bin/dd                  
  inflating: bin/ping6               
  inflating: bin/ping                
  inflating: bin/rnano               
  inflating: bin/netstat             
  inflating: bin/nano                
  inflating: bin/fuser               
  inflating: bin/lesspipe            
  inflating: bin/less                
  inflating: bin/lesskey             
  inflating: bin/lessfile            
  inflating: bin/lessecho       
```