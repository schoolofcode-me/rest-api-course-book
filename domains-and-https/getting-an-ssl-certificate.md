# Getting an SSL certificate

> Before continuing, make sure your domain and associated web application works well. Access your domain name and test your app using Postman if necessary!

**Using Google Chrome**, go to your CloudFlare page and click on the "**Crypto**" tab in the top menu. Here is where we'll generate the SSL certificate. Other browsers may or may not work for the generation of the SSL certificate and key.

In the **Origin Certificates** section, press **Create Certificate**.

Leaving everything as the default, press **Next**.

You should then see a screen as the below:

&lt;&gt;

These are the SSL certificate key and pem files, which the server needs to enable HTTPS.

## Copying the files into the server

Log in to your DigitalOcean server via SSH. This can be done as we have already seen, using a console window or via the DigitalOcean control panel.

Here, I will create two files. Make sure to replace the domain name for your own:

* `/var/www/ssl/rest-api-course-trial.com.key` ; and
* `/var/www/ssl/rest-api-course-trial.com.pem`.

In each, paste the corresponding text from the CloudFlare SSL certificate generation window.

Voilà! You have an active, signed SSL certificate in your server!

The last thing remaining is to tell nginx to use the SSL certificate and serve traffic via `https`. Let's do that!

