### Multistage build example

Multistage builds save image size and 'throw away' some layers after use 
BuildKit (aka buildx) is the 2022 evolution of that with multiarch (amd64, arm etc), paralelism and no need to install docker engine 

```
$ cat Dockerfile
FROM alpine AS docker
ENV DOCKER_VERSION=20.10.8
WORKDIR /output
RUN apk add curl
RUN curl https: //download.docker.com/linux/static/stable/×86_64/docker-${DOCKER_VERSION}. tgz | tar zx docker/docker
FROM alpine AS kubectl
ENV KUBECTL_VERSION= 1.22.0
WORKDIR /output
RUN apk add curl
RUN curl - L0 https: //dl.k8s.io/release/v$ {KUBECTL_VERSION)/bin/linux/amd64/kubectl
RUN chmod +x kubecti
FROM alpine AS terraform
ENV TERRAFORM_VERSION= 1.0.4
WORKDIR /output

RUN apk add curl
RUN curl - LO https: / / releases. hashicorp.com/terraform/${TERRAFORM_ VERSION) /terraform ${TERRAFORM_VERSION_ linux amd64.zip
RUN unzip terraform_ $ (TERRAFORM_VERSION) linux amd64
FROM alpine
COPY - -from=docker /output /docker/docker /us/local/bin/ copy _from=kubecti /output/kubecti /ust/local/bin/ copy _-from=terraform /output/terraform /usr/local /bin/
CMD /
   docker version
   kubectl version
   terraform version
    uname -a

```
![image](https://github.com/telecomprofi/docker-101/assets/17558124/b5ce0847-8dc3-4b35-8113-498961699a5e)
