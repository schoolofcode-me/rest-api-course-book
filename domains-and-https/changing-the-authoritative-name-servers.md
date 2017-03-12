# Changing the Authoritative nameservers

Our domain already has Authoritative nameservers. Namecheap sets it to some nameservers they own, and the IP address that our domain points to is a Namecheap address. You can verify this by navigating to your new domain now, using a browser.

I mentioned earlier we would another service for DNS configuration instead of Namecheap's PremiumDNS option. This service is Cloudflare. It's a Content Delivery Network \(CDN\) that also lets us use them as Authoritative nameservers.

## Setting up CloudFlare

The first step is to register with CloudFlare and tell them of our domain name.

Navigate to [https://www.cloudflare.com/a/sign-up](https://www.cloudflare.com/a/sign-up) and register. Once you've signed in, you'll see a page like the following:

![](/assets/cloudflare-set-up-page.png)Enter your domain name \(`rest-api-course-trial.com` in my case\) and then **Begin Scan**. After a while, you'll see what DNS records are associated with your domain. Note this may fail at this stage, as the DNS records may not be available yet. It may take up to 24 hours.

![](/assets/previous-dns-records.png)

Let's just press **Continue** for now. We'll change these records afterwards.

## Select CloudFlare plan

For now I suggest sticking to the **Free Website** plan. We'll learn how to use CloudFlare, and we can always upgrade later if required.

Normally I would only suggest upgrading if the website will have a lot of traffic \(tens of thousands or more per day\) or if there is a risk that a competitor may try to take your website down via [Denial of Service attacks](https://www.howtogeek.com/281707/what-are-denial-of-service-and-ddos-attacks/).

## Changing the Authoritative name servers

Finally, we get to change the nameservers!

The last step in the CloudFlare configuration tells us to change our nameservers:

![](/assets/cloudflare-change-nameservers.png)

Our nameservers have been automatically set up by Namecheap, but we can change them in the Namecheap domain management screen.

Log in to Namecheap, and you should see your domain list. Here, go to the domain management section:

![](/assets/domain-list.png)

Then, in the nameservers section, go from "Namecheap BasicDNS" to "Custom DNS":

![](/assets/changing-namecheap-dns.png)

And there, add the two nameservers that CloudFlare advises:

* `beth.ns.cloudflare.com`  and
* `justin.ns.cloudflare.com`

Just as in the image below:

![](/assets/setting-cloudflare-authoritative-nameservers.png)

Go back to CloudFlare and press **Continue**. Within a few minutes to a few hours, our nameservers will change.

Every now and then we can press the **"Recheck Nameservers"** button to know when this has happened.

