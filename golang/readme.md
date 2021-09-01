Run simple docker container with current dir mounted as work

That DevOps Guy

https://www.youtube.com/watch?v=EdmKENqnQUw&list=PLHq1uqvAteVvqQaaIAvfIWWTL_JmmXcfg&index=2

NOTE (from https://malramsay.com/post/docker-on-fedora/):  
On an Ubuntu install this would work, however Fedora uses SELinux for security, which requires the appropriate labelling of file objects for the processes using them. By default Docker doesn't perform this labelling, however we can tell it to with the :z or :Z suffixes for the volume. The lowercase :z allows multiple containers to access the volume and the uppercase :Z allows a single container to access the volume.

```
docker run -it -v ${PWD}:/work:Z -w /work alpine:3.11 /bin/sh
```


```
docker run --privileged -it -v ${PWD}:/work -w /work alpine:3.11 /bin/sh
```


# The dockerfile
```
docker build . -t gospace

docker run -it -v ${PWD}:/work:Z -w /work gospace /bin/sh

```


