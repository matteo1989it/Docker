#Dockerfile for mini-httpd

FROM ubuntu
RUN apt-get update && apt-get -y dist-upgrade && apt-get -y install --no-install-recommends wget tar nano make gcc build-essential
RUN wget http://www.acme.com/software/mini_httpd/mini_httpd-1.30.tar.gz
RUN tar -xf mini_httpd-1.30.tar.gz 
WORKDIR mini_httpd-1.30/
RUN sed -i '102d' mini_httpd.c
RUN make


FROM ubuntu  
COPY --from=0 mini_httpd-1.30/ minihttpd/
WORKDIR minihttpd/
CMD ["./mini_httpd"] 



