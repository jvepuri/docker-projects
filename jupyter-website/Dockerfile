FROM amazonlinux:latest

# Install dependencies
RUN dnf update -y && \
    dnf install -y httpd && \
    dnf search wget && \
    dnf install wget -y && \
    dnf install unzip -y

# change directory
RUN cd /var/www/html

# download webfiles
RUN wget https://github.com/azeezsalu/jupiter/archive/refs/heads/main.zip

# unzip folder
RUN unzip main.zip

# copy files into html directory
RUN cp -r jupiter-main/* /var/www/html/

# remove unwanted folder
RUN rm -rf jupiter-main main.zip

# exposes port 80 on the container
EXPOSE 80

# set the default application that will start when the container start
ENTRYPOINT ["/usr/sbin/httpd", "-D", "FOREGROUND"]