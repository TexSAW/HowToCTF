# CTFd

## Deployment Model
The recommended setup for CTFd is running through uWSGI with NGINX acting as a reverse proxy. This is optimal for many reasons. NGINX can serve static content itself, optimizing download speed and easing the load on the uWSGI. This allows allows for easy creation of a landing and supporting web-pages, making the CTF a single section of an entire events website.

## Why CTFd?
CTFd is a CTF Web Framework written by ISIS Lab (the sponsors of CSAW CTF.) and is used for CSAW CTF. As such, it can handle a heavy load and is reliable, making it a perfect candidate to use. PicoCTF was seen as a viable alternative, however, there was an instance of a bug in the platform that allowed a rogue attacker to dump the database, causing CTFd to present itself as a more favorable alternative.

## Why NGINX?
NGINX is a lighter weight alternative to httpd (Apache) and really shines as a reverse proxy. This alone makes it a wonderful candidate for coupling with CTFd. Past that, it is a strong option to use for web challenges (and any needed reverse proxy for them), keeping the base software in use small.

## Why uWSGI?
uWSGI is included in the Flask documentation (CTFd is a Flask app) as a recommended way to serve applications at scale. Coupled with NGINX, uWSGI provides a standard and lightweight way to serve CTFd, handling a heavy load with minimal resource usage.

## CTFd Ansible
This entire set up has been automated with [void-ansible-roles/CTFd](https://github.com/void-ansible-roles/CTFd/), should Void Linux be chosen as the base operating system. Using this out of box solution should be highly considered. The important part of the CTF is serving challenges as reliably as possibly, not the back-end infrastructure. This is a known good configuration that can handle a heavy load and can allow you to spend more time on important things, like writing quality challenges.
