---

copyright:
  years: 2017
lastupdated: "2017-08-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# SSL Offload

For all incoming HTTPS connections, the load balancer service terminates SSL connection and establishes plain-text HTTP communication with the back-end server. The back-end servers are thus offloaded from performing CPU-intensive SSL handshakes and encryption/decryption tasks, so they can use all their CPU cycles for processing application traffic. An SSL certificate is required for the load balancer to perform SSL offload tasks. You may use a pre-existing SSL certificate or purchase a new one, and manage it through the [IBM Cloud Certificate Store ](https://control.softlayer.com/security/sslcerts). 

# Custom SSL cipher.
The load balancer service supports TLS version 1.2 with SSL offload.

You can now customize which SSL cipher your load balancer supports. You can select the ciphers from a predifned list of ciphers (listed below). Note that you can't custmize the ciphers at the time of load balancer creation. By default your load balancer supports all the predefined ciphers. You can customize the ciphers in an update to the existing load balancer. If the response of the get load balancer details with mask 'sslCiphers' doesn't return any ciphers, it means by default all ciphers are in effect and you have not customized any ciphers.

# Supported Ciphers
The following list details the supported ciphers :

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256