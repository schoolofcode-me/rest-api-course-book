# Modifying our DNS records

When our Authoritative nameservers have successfully changed, we can go ahead and make changes to our DNS records. Whenever we make changes to the records, it can take a while for them to take effect \(up to a few hours\).

The first thing we're going to do is go ahead and delete existing DNS records.

Go to your CloudFlare domain, and to the DNS tab at the top of the page.

By clicking on the `X` in each DNS record, delete all records.

## Types of DNS record

Once we have erased all the pre-existing Namecheap records, we are going to create our own.

Let's start by explaining what the different types of records do:

* `A` record;
* `AAAA` record;
* `CNAME` record;
* `MX` record; and
* `TXT` record.

There are a few more types, but you'll seldom encounter them. For more information, visit [this link](https://technet.microsoft.com/en-us/library/cc958958.aspx).

#### A record

The **Address** \(A\) record maps a domain name to an IPv4 address. For example, `rest-api-course-trial.com` to `95.85.15.100`.

An IPv4 address is the normal IP address that we know and love. This is what DigitalOcean gives us as a location of our server.

#### AAAA record

The **IPv6 Address** \(AAAA\) record maps a domain name to an IPv6 address. For example, `rest-api-course-trial.com` to `2001:0db8:85a3:0000:0000:8a2e:0370:7334`. 

An IPv6 address behaves in just the same way as IPv4. However, as you can see it is longer and has a slightly different structure. IPv6 was created because we are _running out_ of IPv4 addresses. There are too many devices that IPv4 can no longer provide a unique address to each device. This is where the longer IPv6 comes in.

#### CNAME record

A **Canonical name** \(CNAME\) record is used to create an alias for a domain name. For example, we can create an alias for `rest-api-course-trial.com` that is `www.rest-api-course-trial.com`. That way, our users will be able to access either of those two domains when requesting our page.

#### MX record

The **Mail Exchange** \(MX\) record is used to specify mail exchange servers for a domain name. A mail exchange server is one that processes or forwards mail. This type of record is used when creating e-mail addresses that use our domain name \(e.g. `jose@schoolofcode.me`.

#### TXT record

The **Text** \(TXT\) record is used to store a string against a domain name. These are often used to verify domain ownership \(e.g. if you can set a TXT record to have the value `x`, that means you own the domain because you were able to perform that change\).

## Adding our DNS records

Now let's add our DNS records. We'll need the IP address of the DigitalOcean server that hosts our REST API. For the purposes of this book I'll use my server, `95.85.15.100`.

Add an A record that points our domain name, `rest-api-course-trial.com` to our IP address, `95.85.15.100`. Leave the Time To Live \(TTL\) as Automatic.

Then, add a CNAME record that maps `www` to our domain name. Instead of typing out `rest-api-course-trial.com`, you can use `@` here instead as a shorthand.

**That's all we need!**

When the DNS records have propagated across the internet you will be able to access the REST API using the domain name as opposed to the IP address. Propagation can take a while if the TLD servers have the old Authoritative nameservers in their cache, or if your Authoritative nameservers have the old IP address in their cache.

Caches expire after a set amount of time \(the Time To Live, TTL\).



