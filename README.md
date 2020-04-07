# pyjq

A simple Python package to Query Json Data.

## Features

- Supports pure json files
- Supports multiple json objects in a file, delimited by newlines (/n)
- Supports gzipped files
- Supports customizabile filters
- Supports pure datetime range filters 

## Todo

The filters could be extended easily, adopting [Python3 stdlib operator](https://docs.python.org/3/library/operator.html).
See `pyjq.PyJQ.filter` to extend ops mapping.

## Installation

````
pip install pyjq-ng
````
## Example data

See `example/alerts.json`.
pyjq works on lines by lines (splitted by \n).
It have been used for Wazuh alert json files and Django dumps.

````
pyjq -j examples/django_dump.json -limit 2 -filter 'fields__original_url == https://google.com'
pyjq -j examples/django_dump.json -limit 2 -filter 'model == urlshortener.urlshortener'
````

## Usage

'agent__name' it's an example of the namespace used by pyjq to access to nested childs. It other word it means `json['agent']['name']`.
It haven't limits on number of nested elements.


Apply some custom filters with AND and OR operators on Wazuh Alert file
````
pyjq -j ../Scaricati/alerts.json -filter 'agent__ip == 172.16.16.102 and agent__name == telegram-gw or agent__ip == 172.16.16.108'
````

Contains operator
````
pyjq -j ../Scaricati/alerts.json -filter 'rule__description in iptables and agent__name == dev-bastion'
````

Convert a specified filed to a pure datetime object and filter in a specified range
````
pyjq -j ../Scaricati/alerts.json -start_datetime 2020-04-06T10:22:00 -end_datetime 2020-04-06T13:22:00 -datetime_field timestamp
````

Realtime reading
````
pyjq -j /var/ossec/logs/alerts/alerts.json -r -start_date 2020-04-07T14:40:23 -datetime_field timestamp -realtime
````

Use a gzipped json file directly
````
pyjq -j ../Scaricati/alerts.json.gzip
````

Limit results to 2 
````
pyjq -j ../Scaricati/alerts.json  -limit 2
````

## Author

Giuseppe De Marco <giuseppe.demarco@unical.it>

## Credits

Wazuh SIEM group @GarrLab
