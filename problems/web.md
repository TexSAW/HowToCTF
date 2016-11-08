# Web

Web problems are a broad topic. I would recommend poking around at OWASP's Top 10 chart for inspiration. For simple exploits, it should be noted that Python web applications tend to be easy to write poorly, meaning easy web challenges can be written quickly. Anything allow remote code execution should be run sand-boxed away from other challenges, as RCE allows for an easy pivot into other infrastructure.

## NGINX

I strongly recommend using NGINX as the front end server for all web applications running. Combined with virtual hosts, this allows you to put more restrictive firewall rules (only allowing port 80 or 443) as well as keeping the load of static assets off the individual web applications running. Utilizing NGINX allowed us to turn multiple services running on a single IP across many nonstandard ports to each service running on its own domain name. This behavior could be easily be done with sub-domains if desired and services could easily be given SSL Certificates with Let's Encrypt if desired.
