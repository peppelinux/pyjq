# pyjq

A simple Python package to Query Json Data.

## Installation

````
pip install pyjq
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

Limit results to 2 
````
pyjq -j ../Scaricati/alerts.json  -limit 2
````

## Author

Giuseppe De Marco <giuseppe.demarco@unical.it>

## Credits

Wazuh SIEM group @GarrLab
