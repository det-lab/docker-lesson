# Dockerfile
FROM ubuntu:22.04

# Install SSH server
RUN apt-get update && apt-get install -y openssh-server

# Create SSH directory and set password for root
RUN mkdir /var/run/sshd && echo 'root:rootpassword' | chpasswd

# Allow root login (not recommended for production)
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# Expose port 22 and start SSH
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]