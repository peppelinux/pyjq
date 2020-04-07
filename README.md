# pyjq
A simple Python package to Query Json Data

# installation
````
pip install pytz
````
# example data

See `alerts.json`

# usage

Apply some custom filters with AND and OR operators
````
python3 pyjq.py -j ../Scaricati/alerts.json -filter 'agent__ip == 172.16.16.102 and agent__name == telegram-gw or agent__ip == 172.16.16.108'
````

Contains operator
````
python3 pyjq.py -j ../Scaricati/alerts.json -filter 'rule__description in iptables and agent__name == dev-bastion'
````

Convert a specified filed to a pure datetime object and filter in a specified range
````
python3 pyjq.py -j ../Scaricati/alerts.json -start_datetime 2020-04-06T10:22:00 -end_datetime 2020-04-06T13:22:00 -datetime_field timestamp
````

Limit results to 2 
````
python3 pyjq.py -j ../Scaricati/alerts.json  -limit 2
````

# author 
Giuseppe De Marco <giuseppe.demarco@unical.it>

# credits
Wazuh SIEM group @GarrLab
