# Enable Tomat JMX

if you want to enable the JMX feature of the tomcat8, to monitor <b>Heap Memory, Threads, CPU Usage, Classes, and configure various MBeans</b>.

## install tomat8

## setenv.sh

* go to path where you have tomcat installed
* go to bin folder
* create a file as "setenv.sh"
* modify file

```bash
CATALINA_OPTS="-Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9000 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false"
```
* change file permission as executable

```
chmod 755 setenv.sh
```

## verify
```
systemctl restart tomcat8
netstat -anlp | grep 9000
```
it should show:

```
[root@localhost ~]# netstat -anlp |grep 9000
tcp6       0     0 :::9000                 :::*                   LISTEN     9372/java
[root@localhost ~]#
```

## connect tomcat JMX using JConsole
```
[root@localhost ~]# jmc
```
connect JMX by localhost:9000