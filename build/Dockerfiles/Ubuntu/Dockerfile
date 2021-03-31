# FROM debian:bullseye

ARG baseImage=ubuntu:20.04
FROM $baseImage

# RUN echo yolo $baseImage

# FROM ubuntu:20.04
RUN apt update && apt install -y git build-essential autoconf automake dos2unix

WORKDIR /app
COPY src/l-smash ./

RUN dos2unix configure && chmod +x configure

RUN ./configure --prefix='/usr' --enable-shared --disable-static  \
    && make \
    && make install \
    && mkdir -p /build/bin \
    && mkdir -p /build/lib \
    && mkdir -p /build/include \
    &&  ./configure --prefix='/build' --enable-shared --disable-static \
    && make install

RUN rm -rf /app/*

# Running m4acut build

COPY src/m4acut ./

RUN rm -rf /build \
    && (automake || true) \
    && autoreconf -i \
    && ./configure \
    && make \
    && make install \
    && mkdir -p /build \
    && cp ./m4acut /build



# --build-arg baseImage=debian:bullseye


# docker build . -t lsm-test -f .\build\Dockerfiles\Ubuntu\Dockerfile --build-arg baseImage=debian:bullseye
# docker build . -t lsm-test -f .\build\Dockerfiles\Ubuntu\Dockerfile --build-arg baseImage=debian:bullseye-slim
# docker build . -t lsm-test -f .\build\Dockerfiles\Ubuntu\Dockerfile --build-arg baseImage=debian:oldstable-slim
# docker build . -t lsm-test -f .\build\Dockerfiles\Ubuntu\Dockerfile --build-arg baseImage=debian:oldstable-slim --platform arm

# linux/arm/v5
# linux/arm/v7
# linux/arm64/v8


# linux/amd64
# linux/386


# Start-Process powershell "docker build . -t lsm-test -f .\build\Dockerfiles\Ubuntu\Dockerfile --build-arg baseImage=debian:bullseye"
# Start-Process powershell "docker build . -t lsm-test -f .\build\Dockerfiles\Ubuntu\Dockerfile --build-arg baseImage=debian:bullseye-slim"
# Start-Process powershell "docker build . -t lsm-test -f .\build\Dockerfiles\Ubuntu\Dockerfile --build-arg baseImage=debian:oldstable-slim"
# Start-Process powershell "docker build . -t lsm-test -f .\build\Dockerfiles\Ubuntu\Dockerfile --build-arg baseImage=debian:oldstable-slim --platform arm"


# Start-Process powershell ""