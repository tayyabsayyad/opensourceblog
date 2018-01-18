---
title: "Self Signed Certificate"
date: 2018-01-15T21:46:55+05:30
draft: false
tags: ["ssl"]
categories: ["Tutorials"]
---

To secure your web server you need SSL certificate which can be obtained by two ways

1. Generate a self-signed certificate
2. Obtain from the third party like DigiCert or Thawte

## Generate Self Signed Certificate

Install openssl if not present using the following command

    $sudo apt-get install openssl

    
Next step is to generate private keys which can be generated as follows, This will ask you to enter a password to protect this key and will generate key file named www.opensourcetutorials.in.key

    #openssl genrsa -des3 -out www.opensourcetutorials.in.key 1024

If you want to the key you use cat and do as follows.

    #cat www.opensourcetutorials.in.key

Next step is to generate CSR file which is Certificate Signing Request which contains the details of the domain and owner etc. To generate CSR we will need the above generated key file.

    # openssl req -new -key www.opensourcetutorials.in.key -out www.opensourcetutorials.in.csr

This will ask you fill the details and generate CSR file.

Next is the final step to generate self-signed SSL certificate using following command

    # openssl x509 -req -days 365 -in www.opensourcetutorials.in.csr -signkey www.opensourcetutorials.in.key -out www.opensourcetutorials.in.crt

This will ask password to use the private key file and will generate certificate.

This certificate can be now installed on the apache server.

## Generate Certificate from the certificate signing authority

1. Select the certificate authority from where you want to buy the SSL certificate.
2. Fill the details of your organization
3. Generate CSR as shown above. Key size should be higher than 1024.
4. Submit your CSR file.
  1. You will receive the certificate on email.
