#ssh-srv : A wrapper bash script for using SSH through SRV 

Just a simple script that do `nslookup` to a URL that contains SRV record and use its information to execute `ssh`. Should work on OSX/Linux since I used `grep`.

## What is an SRV record?

[Service Record](https://en.wikipedia.org/wiki/SRV_record). It is a type of record set (among A, CNAME, etc.) that has a target port number and a corresponding server host name. You could then use a custom name defined in SRV record to point to your services that you have open without remembering port numbers.

My situation for example has SSH open on 5argon.thddns.net:6560 that my internet provider allowed. It is possible with SRV record to define an easy to remember name without port number and redirect to the real service.

This operation depends on implementation. SSH is one program that does not respect SRV record so when you SSH directly into the custom name on your SRV record it will not connect, since it is expecting a port number 22. With this script the port number on your SRV record will be queried and then used in `ssh`'s `-p` argument.

## Installation

Get the `ssh-srv` file then `chmod +x` and `./ssh-srv` it. Or maybe you could copy it to `usr/local/bin/` then you can do just `ssh-srv`.

## Usage

`ssh-srv username@srvurl`

