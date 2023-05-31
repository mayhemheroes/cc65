# Build Stage:
FROM --platform=linux/amd64 ubuntu:20.04 as builder

## Install build dependencies.
RUN apt-get update && apt-get install -y build-essential

ADD src /src
ADD include /include
ADD libsrc /libsrc
ADD asminc /asminc
ADD cfg /cfg
ADD doc /doc
ADD util /util
ADD targettest /targettest
ADD test /test
ADD samples /samples
ADD Makefile /

## Build Step
RUN make -j 4

# Package Stage
FROM --platform=linux/amd64 ubuntu:20.04
COPY --from=builder /bin/cc65 /
