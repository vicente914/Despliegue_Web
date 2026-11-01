# Logs
## Goal
The goal of this practical assignment is to **locate, read, and interpret Apache's access log** on an virtual machineº of Ubuntu server, and to understand **how different types of HTTP requests (successful loads and 404 errors) are recorded** in the log.

## 1.- Finding access.log
First, we are gonna find the "__access.log__" file and list its content. It is located at the route __"/var/log/apache2/access.log"__.
```bash
#To list its content
sudo cat /var/log/apache2/access.log 
```
[access.log](img/accessLog.png)

## 2.- Test it
Now, we are gonna open the index.html of the apache server on our host machine, on the browser, we search up for the IP of the server, if we need to check the IP because we are not sure, run this command
```bash
# Run this command and search for the enp0s3 ip
ip a
```
[index.html](img/index.png)

If everything went well, if we check again the content of the access.log file, we should see new lines on its content.
```bash
#Checking again access.log content
sudo cat /var/log/apache2/access.log
```

[access.log second view](img/accessLog2.png)

As we can see, there are new lines because we visited with our host machine the site.
Among those lines, we can identify:

- **IP address:** The ip address that visited the site, **[192.168.1.131]**.
- **Date/time:** The exact time the client loaded the page **[01/Nov/2026:12:31:04 +0000]**.
- **Resource:** The resourse requested, in this case the (**/**) the root path which servers the index.html.
- **HTTP Code:** The HTTP code which is **200**, that means it loaded correctly.
- **The client:** The browser used to access the page, (**`Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/155.0.0.0 Safari/537.36`**)


## 3.- Triggering a 404 error
To continue with this documentation, now we are going to trigger a 404 error and the proceed to load the page again and see the access.log file again.
```bash
#Trigger error 404
curl http://localhost/not-exist.html
```
[Triggering error 404](img/trigger404.png)
 
 When we check the access.log file we should see a new line like this one:
 [access.log third view](img/accessLog3.png)
