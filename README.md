# ansible-role-thumbor [![build status](https://gitlab.com/hugomrdias/ansible-role-thumbor/badges/master/build.svg)](https://gitlab.com/hugomrdias/ansible-role-thumbor/commits/master)
> Role to install Thumbor in Debian/Ubuntu systems

This is for advanced users.

## Requirements
None   

## Role Variables
Check `defaults/main.yml`

## Dependencies
None

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: hugomrdias.thumbor }

## Example Nginx vhost

```
upstream thumbor  {  
    server 127.0.0.1:8000;
    server 127.0.0.1:8001;
    server 127.0.0.1:8002;
    server 127.0.0.1:8003;
}

server {  
    listen       80;
    server_name  <INSERT YOUR DOMAIN NAME>;
    client_max_body_size 10M;

    location / {
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header HOST $http_host;
        proxy_set_header X-NginX-Proxy true;

        proxy_pass http://thumbor;
        proxy_redirect off;
    }
}
```
## License
MIT © [Hugo Dias](http://hugodias.me)
