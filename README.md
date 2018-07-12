## ip-utils

### About

This repository contains some utilities for determining (public) IP addresses and updating a dynamic DNS entry. 

### Dependencies

The scripts in this repository require accounts at the following excellent and free services:

* [ipinfo](https://ipinfo.io) - "IP Address API and Data Solutions"
* [DuckDNS](https://duckdns.org) - "Free dynamic DNS hosted on Amazon VPC"

You will require accounts at these services to use this script. Each of these services provide a user token, which are required by the scripts:

* $IPINFO_TOKEN
* $DUCKDNS_TOKEN

These tokens must be set in the calling environment, otherwise the scripts will execute and record an error.

`get_ip_info` works best with the json parser jq installed. Both scripts use curl.

### Usage

#### get_ip_info

Script contains two functions:

* `get_host_ip()` - seeks to retrieve the current host IP from ifconfig
* `get_external_ip()` - uses ipinfo.io to retrieve the public IP

The script can be sourced, or called directly from the command line, in which case both `get_host_ip()` and `get_external_ip()` are called. Executed in either fashion, `get_external_ip()` requires token $IPINFO_TOKEN to function.

#### update_dns

Script contains a single function, `updatedns()` to set the specified domain to the given IP address:

```
updatedns <domain-name> <ip-address>
```
Returns 0 upon update success (OK 200 from DuckDNS) and 1 in all other cases.

The script can be sourced, or called directly from the command line. Executed in either fashion, `updatedns()` requires token $DUCKDNS_TOKEN to function.

### Support and feature requests

Ping me if you have any questions, suggestions or requests for new features.

### License

Distributed under the MIT License, see LICENSE file in the repository root for more information.
