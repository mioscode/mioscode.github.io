---
title: "(Docker) Go Docker 빌드 및 실행"
categories:
  - Docker
tags:
  - Go
  - Docker
comments: true
---

# (macOS) Docker 설치
Install Docker Desktop on Mac
https://docs.docker.com/docker-for-mac/install/

# Docker image 빌드 및 실행
- (Dockerfile 없으면) Dockerfile 생성

```
# Dockerfile References: https://docs.docker.com/engine/reference/builder/

# Start from the latest golang base image
FROM golang:latest

# Add Maintainer Info
LABEL maintainer="mioscode <mioscode@email.com>"

# Set the Current Working Directory inside the container
WORKDIR /app

## Copy go mod and sum files
# COPY go.mod go.sum ./

## Download all dependencies. Dependencies will be cached if the go.mod and go.sum files are not changed
# RUN go mod download

# Copy the source from the current directory to the Working Directory inside the container
COPY . .

# 
RUN go get github.com/labstack/echo \
 && go get github.com/dgrijalva/jwt-go

# Build the Go app
RUN go build -o main .

# Expose port 8080 to the outside world
EXPOSE 8080

# Command to run the executable
CMD ["./main"]
```

- build the Docker image

```
$ docker build -t project_name .
```

- You can list all the available images by typing the following command

```
$ docker image ls
REPOSITORY                    TAG                            IMAGE ID            CREATED             SIZE
go-docker                     latest                         ed03a0732734        21 seconds ago      830MB    
golang                        latest                           2422e4d43e15     
```

- Running the Docker image

```
$ docker run -d -p 8080:8080 project_name
84e43b3651aa0ebf7b1ed843127dd2f4d179bab006e6bcf55a873772f838e99c
```

- Finding Running containers

```
$ docker container ls
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS                    NAMES
84e43b3651aa        project_name             "./main"            8 minutes ago       Up 8 minutes        0.0.0.0:8080->8080/tcp   practical_shirley
```

- Stopping the container
 
```
$ docker container stop 84e43b3651aa
84e43b3651aa
```