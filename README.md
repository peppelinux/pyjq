# pyjq
A simple Python package to Query over Json Data

# installation
````
````
# example data

````

````


# usage
````
python3 pyJQ.py -j ../Scaricati/alerts.json -filter 'agent__ip == 172.16.16.102 and agent__name == telegram-gw or agent__ip == 172.16.16.108'
````

````
python3 pyJQ.py -j ../Scaricati/alerts.json -filter 'rule__description in iptables and agent__name == dev-bastion'
````

````

````

# author 
Giuseppe De Marco <giuseppe.demarco@unical.it>

# credits
Wazuh SIEM group @GarrLab
