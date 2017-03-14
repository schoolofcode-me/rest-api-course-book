# Serving HTTPS traffic with nginx

Now that we've got the SSL certificate in our server, we can tell NGINX to use it. All we have to do is modify the configuration file. Open the application's configuration file. From the course, this is on `/etc/nginx/sites-enabled/items-rest.conf`.

Find the following lines:

```nginx
listen 80;

server_name localhost;
```

And we are going to change then to this:

```nginx
listen 443 default_server;

server_name rest-api-course-trial.com;

ssl on;
ssl_certificate /var/www/ssl/rest-api-course-trial.com.pem;
ssl_certificate_key /var/www/ssl/rest-api-course-trial.com.key;
```

We want to change the `listen` because `http` traffic accesses our server on port 80, but `https` traffic uses port 443.

The other fields tell nginx to use SSL, and the locations of the certificate and key.

### HTTPS rewrites

Sometimes, users will access the `http` version of our site—accidentally or because they have it bookmarked. We can tell nginx to redirect users to the `https` version of the site when this happens.

At the bottom of our config file, add the following lines:

```nginx
server {
    listen 80;
    server_name rest-api-course-trial.com;
    rewrite ^/(.*) https://rest-api-course-trial.com/$1 permanent;
}
```

What that does is listen on port 80, and rewrite the URL to the `https` protocol. The `$1` appends at the end of the domain name whatever users requested. For example, `$1` could be `/stores`.

### Restart nginx

Finally, reload and restart nginx to apply the changes.

```bash
sudo systemctl reload nginx
sudo systemctl restart nginx
```

### Verify it all works

Access your `https` site or API using Postman. It should all work!

