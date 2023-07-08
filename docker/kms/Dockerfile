FROM ubuntu:22.04 as builder
RUN apt-get update
RUN apt-get dist-upgrade -y
RUN apt-get install git gcc make -y
RUN mkdir /server
WORKDIR /server
RUN git clone https://github.com/Wind4/vlmcsd.git
WORKDIR vlmcsd
RUN make

FROM ubuntu:22.04 as runner
RUN apt-get update
RUN apt-get dist-upgrade -y
RUN mkdir /server
WORKDIR /server
COPY --from=builder /server/vlmcsd/bin ./
EXPOSE 1688/tcp
CMD ["./vlmcsd", "-D", "-d"]