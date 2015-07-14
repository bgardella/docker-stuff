FROM ubuntu:latest

MAINTAINER bgardella@ getoveryourself.com

# turn off console ui
RUN export DEBIAN_FRONTEND=noninteractive

# Update the repository
RUN apt-get update

# Install necessary tools
RUN apt-get install -q -y nano wget dialog net-tools nginx mysql-server php5-gd libssh2-php
