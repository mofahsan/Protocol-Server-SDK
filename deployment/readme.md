##

Build the container
```
docker build -t <tagname> . 
```

For running the container

```
docker run -p 80:80 <tagname>
```


nginx.conf contains http routings
nginxssl.conf contains routings with https and https, ssl certificate is required to run https
- change which .conf you want to use in Dockerfile
- host.docker.internal is used in windows and macos environment for linux replace host.docker.internal with 172.17.0.2 to point to machine localhost.

