# Subdomino [![Python 2.6|2.7](https://img.shields.io/badge/python-2.6|2.7-yellow.svg)](https://www.python.org/) 
![Image of Subdomino](http://image.noelshack.com/fichiers/2016/39/1475404267-capture-d-ecran-de-2016-10-02-17-28-57.png)
```
Warning : Need to be run as root in order to ping a domain, due to the socket use !
```
An application that enumerates subdomains, and scan them with several rules

## Dependencies 
* Ping-v0.2 - pip install ping
* Argparse  - pip install argparse
* DnsPython - pip install dnspython


## Features
* Bruteforce subdomains with file 'names.txt' or custom
* Detect subdomains using dork in Google
* Auto ping of every detected subdomains
* Generate report for every subdomains
* NMAP of every detected subdomains
* Advanced scan with custom rules to detect IOV (indicator of vulnerability)


## How to use to enumerate online subdomains, and launch detection rule-based
```
sudo python Subdomino.py --domain google.com (--nmap) (--all) (--google 5) (--yahoo 5) (--bing 5) (--baidu 5) (--reversedns) (--names big_names.txt) (--threads 20) (--file list_of_submn)
```
The options are:
* nmap       : launch a fast nmap on every discovered subdomains
* all        : search with all websites (google, yahoo, bing...)
* google     : add a search for subdomain using google dork, you must specify the number of result pages
* yahoo      : add a search for subdomain using yahoo dork, you must specify the number of result pages
* bing       : add a search for subdomain using bing dork, you must specify the number of result pages
* baidu      : add a search for subdomain using baidu dork, you must specify the number of result pages
* reversedns : add a search for subdomain using a reverse dns
* names      : allows you to use a custom file to bruteforce subdomains
* file       : allows you to provide an already pinged subdomain's list
* threads    : number of pools you want to use for the multiprocessing bruteforce


## How to add new rules
You need to add an entry in **"rules.txt"** like this
```
name: Name of the rule
rule: Put here the rule you want to match
desc: Description of the rule
```

You can use the following rules pattern:
* is_string_page
* is_string_header
* regex_match_page
* regex_match_header

You can also chain several rules with **AND** operator like this
```
rule: is_string_page("hash") AND regex_match_page("jquery.*?(1).([0-7]).([0-9]+)")
```
====