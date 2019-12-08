#
# Nginx Dockerfile
#
# https://github.com/dockerfile/nginx
#

# Pull base image.
FROM ubuntu:16.04

# Install Nginx.
RUN apt-get update
RUN apt-get install nginx -y
RUN apt-get install vim -y

RUN mkdir /etc/nginx/ssl
COPY nginx.crt /etc/nginx/ssl/nginx.crt
COPY nginx.key /etc/nginx/ssl/nginx.key
COPY default /etc/nginx/sites-available/default


# Define working directory.
WORKDIR /etc/nginx

# Define default command.
#CMD ["nginx"]

# Expose ports.
EXPOSE 80
EXPOSE 443
CMD ["nginx", "-g", "daemon off;"]
#CMD ["nginx"]

#docker build -t ff -f Dockerfile-1 . 

#ENTRYPOINT [ "./entrypoint.sh" ]



