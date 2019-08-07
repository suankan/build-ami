# Ansible role description

This role is a minimal set of actions:

1. Install Nginx.
2. Copy static html files from `files/website` to default virtual host root `/usr/share/nginx/html/`.
3. Start Nginx server.

# Requirements

This role should be executed on Amazon Linux distribution.

# Usage

Place your static website content into `files/website` and execute this role on any Centos 6 based server.

# Limitations and assumptions

This ansible role does not configure Nginx after installing rpm package. It simply assumes that default nginx virtualhost defined in `/etc/nginx/nginx.conf` points to `/usr/share/nginx/html/`.
The role has been tested and works on Amazon Linux distribution.