---
layout: post
title:  "Technical: e-mail configuration"
date:   2023-08-28 19:38:41 +0200
categories: technical
---
As explained in the previous post, I've managed to secure a nice domain and configured e-mail hosting/forwarding. Of course everything is a little bit more complex than previously told. Every new piece of equipment, tool, or SaaS software has a certain learning curve. Luckily, the combination Zoho and TransIP was relatively painless.

## Glossary
* **DNS (Domain Name System)** - The distributed online system by which symbolic names (such as www.
example.com) get translated to IP addresses (such as 123.234.345.456) and vice versa.
* **A Record** - An “A” record maps a fully qualified domain name to an IPv4 address.
* **MX Record (Mail Exchanger Record)** - DNS record that defines where email for a domain should be sent.
* **TXT Record (Text Record)** - TXT records contain text. They may be used to record information about a host, or as a way of creating a generic database in the DNS.

## Domain and DNS settings
TransIP provides an easy to use interface for managing your Domain and DNS settings. The DNS servers are set to TransIP automatically (as authoritative server) which provides easy and quick configuration changes. 

When a user browses to [https://dikkeklok.nl](https://dikkeklok.nl) we would like them to end up on our website. Similar for email, every _`[*]@dikkeklok.nl`_ email should arrive in the respective mailbox. DNS settings make this possible: 

![transip](/images/20230828/transip.nl.png)

Zoho has published an easy to understand [help article](https://www.zoho.com/mail/help/adminconsole/configure-email-delivery.html?zredirect=f&zsrc=langdropdown&lb=nl#manual) to assist with this. Following this _should_ result in e-mail being forwarded towards the Zoho servers. But, we should let Zoho know that e-mails are coming as well.

This starts with adding a TXT record, provided by Zoho, in TransIP that verifies that we're the actual owner of the domain. If you do not own a domain, you would be unable to add this. This makes it a secure way for Zoho to check if we're legit.

![zoho](/images/20230828/zoho-validation.png)

Once verified, we can update the DNS records even further. The idea is to be able to let TransIP know that our mailbox lives in a certain place. This can be achieved using _MX Records_. In this case, we would like to point it to Zoho.

The settings used are as follows:

| Host/ Domain          | Address/ Mail Server/ MX Entries/ Value | Priority |
|-----------------------|-----------------------------------------|----------|
| @/ Blank/ Domain name | mx.zoho.eu.                             | 10       |
| @/ Blank/ Domain name | mx2.zoho.eu.                            | 20       |
| @/ Blank/ Domain name | mx3.zoho.eu.                            | 50       |

### Catch all
Finally, we can create our 'Catch-all Address'. This allows us to receive any e-mail in a centralized mailbox.

![catch all](/images/20230828/catch-all.png)

Once this is all configured, both Zoho and TransIP should know what to do with e-mails. However, we still need to configure our user account with the respective settings to be able to send outgoing emails as well.

![alias](/images/20230828/alias.png)

This simple configuration results in us being able to use the Zoho web interface to handle all mail!

![zoho](/images/20230828/zoho.png)

## What's next?
Zoho allows us to use the _[admin@dikkeklok.nl](mailto:admin@dikkeklok.nl)_ address to sign up for additional services. This in combination with the Catch-all settings allow for some fancy trickery. For example, we can handle all our **hosting items** through _[hosting@dikkeklok.nl](mailto:hosting@dikkeklok.nl)_, our **marketing materials** through _[marketing@dikkeklok.nl](mailto:marketing@dikkeklok.nl)_, and **other items** through _[info@dikkeklok.nl](mailto:info@dikkeklok.nl)_. Zoho supports mail filters, so this makes managing everything a piece of cake.

Finally, as seen in the screenshot above, some _A Records_ were configured as well. These are used similarly to forward visitors of our website [https://dikkeklok.nl](https://dikkeklok.nl) to our web hosting party. More in the next blog...