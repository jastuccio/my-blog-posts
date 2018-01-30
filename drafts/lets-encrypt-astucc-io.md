https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04
Congratulations! You have successfully enabled https://astucc.io and
https://www.astucc.io

You should test your configuration at:
https://www.ssllabs.com/ssltest/analyze.html?d=astucc.io
https://www.ssllabs.com/ssltest/analyze.html?d=www.astucc.io

What Should I Do?
If you run a server…

This server supports weak Diffie-Hellman (DH) key exchange parameters. Grade capped to B.   MORE INFO »
https://weakdh.org/
If you have a web or mail server, you should disable support for export cipher suites and use a 2048-bit Diffie-Hellman group. We have published a Guide to Deploying Diffie-Hellman for TLS with step-by-step instructions. If you use SSH, you should upgrade both your server and client installations to the most recent version of OpenSSH, which prefers Elliptic-Curve Diffie-Hellman Key Exchange.

continue with `Step 5 — Updating Diffie-Hellman Parameters`




    # Redirect all HTTP requests to HTTPS with a 301 Moved Permanently response.
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;