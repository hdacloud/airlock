# build environment
FROM docker.io/golang:1.25.4-alpine3.22 AS build-env
ADD . /src
RUN cd /src && go build -mod=vendor

# run environment
FROM docker.io/alpine:3.22
WORKDIR /
COPY --from=build-env /src/airlock /usr/local/bin/airlock
CMD [ "/usr/local/bin/airlock", "serve" ]
