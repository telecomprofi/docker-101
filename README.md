# docker-101


### Install docker
* [Link to official docs](https://docs.docker.com/engine/install/ubuntu/)
* [Link to bashscript (for ubuntu 20.x) that isntall docker-ce, creates user, adds it to group](https://github.com/telecomprofi/exadel-DevOps-internship-21/blob/main/task3/docker-ce-install.sh)

### First steps
```
docker run hello-world
```
or 
```
alias figlet='docker run -i --rm mwendler/figlet'
figlet test
```

### Dockerfile key words
![image](https://user-images.githubusercontent.com/17558124/138663905-dbeaac4e-a856-44fe-84ee-ca941e55231d.png)


### COPY or ADD ?
* TL:DR - always use COPY, avoid using ADD. use ADD only when need to extract local fs archive (gz,bz) into container's fs.

COPY - copies files, folders but does not extract archives and won't download from http:// links
ADD - copies files, folders AND downloads/extracts archives 

![image](https://user-images.githubusercontent.com/17558124/138681509-f495a967-d819-4e51-9b17-30e86c805a2e.png)


instead of using ADD to download from url use below snippet:
```
RUN curl http://source.file/package.file.tar.gz \
  | tar -xjC /tmp/ package.file.tar.gz \
  && make -C /tmp/ package.file.tar.gz
```


### ENTRYPOINT vs RUN
TL:DR 
<tba>

