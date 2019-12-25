### Create a docker file

```
vi Dockerfile
```

### Docker file content

```
FROM node AS source
RUN mkdir -p /node/weather-app
ADD src/ /node/weather-app
WORKDIR /node/weather-app
RUN npm install

FROM node:alpine
ARG APP_VERSION=V1.1
LABEL org.label-schema.version=$APP_VERSION
ENV NODE_ENV="production"
COPY --from=source /node/weather-app /node/weather-app
WORKDIR /node/weather-app
EXPOSE 3000
ENTRYPOINT ["./bin/www"]
```
Download a source code from git repository. 

### get hash code of commit

```
git log -1 --pretty=%H
```

### build docker image

```
sudo docker image build -t <imagename>:<previous hashcode> --build-arg APP_VERSION=1.5 .
```

### run docker container

docker container run -d --name <containername> -p 8090:3000 <imagename>:<previous hashcode>


