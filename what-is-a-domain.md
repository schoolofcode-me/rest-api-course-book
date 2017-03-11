# What is a domain?

Until now, we have accessed our deployed applications using IP addresses. An IP address is a reference to a unique location. For us, these locations have been servers we've rented off DigitalOcean.

Now, asking our users to remember IP addresses for our application is unreasonable. We must give them memorable names, such as `rest-api-course-trial.com`.

A domain name is thus a memorable string that internet connected devices can use instead of the IP address they represent.

## What IP address do they represent?

Domain names do not magically point to our IP address just by wishful thinking! We've got to first purchase the domain name, and then tell the Domain Name System what IP address the domain should point to.

## What is DNS?

The Domain Name System is a simple yet essential system in today's internet. It is what allows all devices to retrieve the IP address corresponding to a domain.

Simplifying slightly, the DNS looks like this:![](/assets/dns-steps.png)

There are three \(and sometimes four\) steps in the Domain Name System.

1. The root servers;
2. The TLD servers;
3. The Authoritative server\(s\).

When your browser requests `http://example.com`,  two things can happen. Either the browser has the IP address stored in memory \(e.g. because you've accessed it recently\), or it has to go to the DNS to find out the IP address.

Let's assume the latter.

The browser asks the Operating System to perform a series of requests. First, it goes to the hard-coded root servers. These can be hard-coded in your internet provider or your operating system.

We can ask the root servers what the IP address of `http://example.com` is, but most likely they won't know. They might know what the TLD servers are. These servers are those in charge of knowing what domains are registered under `.com`. Thus, the root servers can reply with the IP addresses of the TLD servers.

Then, we go to the TLD servers and ask for the address of `http://example.com`. Chances are they won't know either, but they may know what DNS servers are registered to know the IP address. These are `example.com`'s DNS servers.

Finally, we will make a third request to the Authoritative name servers. These are the servers which do know the IP address. They can give us the IP address, and finally our browser can make the request to the correct location on the internet.

To recap:

1. The root servers know what the `.com` DNS servers are \(these are TLD name servers\);
2. The TLD servers know what the `example.com` DNS servers are \(these are Authoritative name servers\);
3. The Authoritative name servers know what the IP address of `example.com` is.



