Menu:

- [Statistics](https://github.com/romainmarcoux/malicious-ip#statistics)
- [Version Française](https://github.com/romainmarcoux/malicious-ip#fr-listes-dadresses-ip-malicieuses)
- [English version](https://github.com/romainmarcoux/malicious-ip#en-malicious-ip-addresses-lists)
- [Sources](https://github.com/romainmarcoux/malicious-ip#sources)

# Statistics

History of statistics [here](https://github.com/romainmarcoux/malicious-ip/blob/main/statistics/historical_statistics.md)

Update of the following table: 2024-01-03 18:44 CEST

| Malicious IP addresses in full-\*                          | Number of IPs |
| ------------------------------------------------------------ | ----------- |
| Present in 6 sources | 1.64% (6858) |
| Present in 5 sources | 1.43% (6000) |
| Present in 4 sources | 3.35% (13978) |
| Present in 3 sources | 5.40% (22542) |
| Present in 2 sources | 13.39% (55840) |
| Present in 1 source | 74.67% (311231) |
| Total | 100% (416791) |

Update of the common IP table with the FortiGate ISDB Malicious-Malicious.Server: 2024-01-03 13:19 CEST

| FortiGate models                                           | full-\* IPs common with ISDB |
| ------------------------------------------------------------ | ----------- |
| 100F and below | 11.09% |
| 200F and above | 16.67% |

# [FR] Listes d'adresses IP malicieuses
Agrégation de listes d'adresses IP malicieuses scindée en fichiers de 131 072 entrées au maximum pour être intégrées dans des pare-feux : Fortinet **__FortiGate__**, Palo Alto, pfSense, OPNsense, IPtables ...

Adresses IP ordonnées en fonction du nombre de listes dans lesquelles elles apparaissent (les IP malicieuses apparaissant dans le plus de listes sont donc dans le premier fichier full-aa.txt).

C'est un complément de la base de données ISDB "**__Malicious-Malicious.Server__**" des FortiGate (statistiques d'IP communes entre la liste full-\* et l'ISDB [ici](https://github.com/romainmarcoux/malicious-ip#statistics)).

**Comment intégrer** ces listes dans un **pare-feu** ?
- **FortiGate**
   * Menu "Security Fabric → External Connectors → Create New → IP Address"
   * Prendre l'URL "Raw" (bouton en haut à droite de chaque fichier)
   * Après, les listes peuvent être utilisées dans les "Firewall Policy" avec les objets "**IP Address Threat Feed**"
   * Implémentation de la liste full validée même sur le plus petit boitier FortiGate 40F
   * Plus d'informations : mon [tutorial](https://www.linkedin.com/posts/romainmarcoux_bloquer-des-ip-de-listes-externes-sur-fortigate-activity-7112413515725852673-KD4q) et cette [page](https://docs.fortinet.com/document/fortigate/7.0.12/administration-guide/891236/ip-address-threat-feed) de l'aide Fortinet
- **Palo Alto** : [lien](https://docs.paloaltonetworks.com/pan-os/9-1/pan-os-admin/policy/use-an-external-dynamic-list-in-policy/external-dynamic-list)
- **pfSense** : via ce [repo](https://github.com/jaredhendrickson13/pfsense-api) GitHub qui permet d'implémenter une API dans pfSense. Attention, par défaut le nombre maximal d'objets est de 400k. 
Possibilité d'augmenter cette valeur si votre pfSense a beaucoup de RAM. Plus d'infos [ici](https://docs.netgate.com/pfsense/en/latest/firewall/aliases.html#alias-sizing-concerns).
- **OPNsense** : via API ([doc](https://docs.opnsense.org/development/api/core/firewall.html). Modifier le nombre maximal d'entrées d'un alias : "Firewall -> Settings -> Advanced -> Firewall Maximum Table Entries".
- **IPTables** avec le paquet "ipset" : [tutorial 1](https://www.malekal.com/comment-utiliser-ipset-sur-linux/) [tutorial 2](https://fr-wiki.ikoula.com/fr/Cr%C3%A9er_et_administrer_facilement_une_blacklist_avec_ipset/iptables)

Mise à jour toutes les **heures**.

Contactez-moi via LinkedIn ([mon profil](https://linkedin.com/in/romainmarcoux/)) pour :
- être notifié quand un **nouveau segment** de fichier est créé (pour l'ajouter dans votre pare-feu)
- me proposer d'ajouter une **autre** blocklist (voir [listes actuelles](https://github.com/romainmarcoux/malicious-ip#sources))

# [EN] Malicious IP addresses lists
Aggregation of lists of malicious IP addresses split into files of a maximum of 131,072 entries to be integrated into firewalls: Fortinet **__FortiGate__**, Palo Alto, pfSense, OPNsense, IPtables, etc.

IP addresses ordered according to the number of lists in which they appear (the malicious IPs appearing in the most lists are therefore in the first full-aa.txt file).

It is a complement to the FortiGate ISDB "**__Malicious-Malicious.Server__**" database (common IP address statistics between the full-\* list and the ISDB [here](https://github.com/romainmarcoux/malicious-ip#statistics)).

**How to integrate** these lists into a **firewall**?
- **FortiGate**
   * Menu "Security Fabric → External Connectors → Create New → IP Address"
   * Take the "Raw" URL (button at the top right on each file)
   * Then, the lists can be used in "Firewall Policy" as "**IP Address Threat Feed**" objects.
   * Implementation of the full list validated even on the smallest FortiGate 40F appliance
   * More information: my [tutorial](https://www.linkedin.com/posts/romainmarcoux_bloquer-des-ip-de-listes-externes-sur-fortigate-activity-7112413515725852673-KD4q) and this [Fortinet help page](https://docs.fortinet.com/document/fortigate/7.0.12/administration-guide/891236/ip-address-threat-feed)
- **Palo Alto**: [here](https://docs.paloaltonetworks.com/pan-os/9-1/pan-os-admin/policy/use-an-external-dynamic-list-in-policy/external-dynamic-list)
- **pfSense**: via this GitHub [repo](https://github.com/jaredhendrickson13/pfsense-api) which allows you to implement an API in pfSense. Be careful, by default the maximum number of objects is 400k.
Possibility to increase this value if your pfSense has a lot of RAM. More info here [here](https://docs.netgate.com/pfsense/en/latest/firewall/aliases.html#alias-sizing-concerns).
- **OPNsense** : via API ([doc](https://docs.opnsense.org/development/api/core/firewall.html). Change the maximum number of entries for an alias: "Firewall -> Settings -> Advanced -> Firewall Maximum Table Entries".
- **IPTables** with the "ipset" package: [tutorial 1](https://www.malekal.com/comment-utiliser-ipset-sur-linux/) [tutorial 2](https://fr-wiki.ikoula.com/fr/Cr%C3%A9er_et_administrer_facilement_une_blacklist_avec_ipset/iptables)

Updated every **hour**.

Contact me via LinkedIn ([my profile](https://linkedin.com/in/romainmarcoux/)) to:
- be notified when a **new file** segment is created (to add it to your firewall)
- suggest I add **another** blocklist (see [current blocklists](https://github.com/romainmarcoux/malicious-ip#sources))

# Sources

| Filename                                                | Source | Description |
| ------------------------------------------------------------ | ----------- | ----------- |
| abuseipdb-\* | [link](https://github.com/borestad/blocklist-ip) | [Collaborative blocklist](https://www.abuseipdb.com/): IPs listed in the last 120 days |
| blocklist.de-\* | [link](https://www.blocklist.de/en/export.html) | Collaborative blocklist ([6k sensors](https://www.blocklist.de/en/index.html)): IPs listed in the last 30 days ([stats](https://www.blocklist.de/en/statistics.html))|
| cinsscore.com-\* | [link](https://cinsscore.com/#list) | IP Block List maintained by [CINS](https://cinsscore.com/#cins): IPs listed in the last 30 days |
| crowdsec.net-\* | [link](https://www.crowdsec.net/product/crowdsec-security-engine) | Collaborative blocklist (64k sensors): IPs listed in the last 30 days |
| emergingthreats.net-\* | [link](https://rules.emergingthreats.net/blockrules/) | IP Block List maintained by [Proofpoint](https://www.proofpoint.com/): IPs listed in the last 30 days |
| greensnow.co-\* | [link](https://greensnow.co/) | IP Block List maintained by [greensnow.co](https://greensnow.co/): IPs listed in the last 30 days |
| isc.sans.edu-\* | [link](https://isc.sans.edu/xml.html) | Collaborative blocklist ([500k sensors](https://isc.sans.edu/about.html)): false positives removed, IPs listed in the last 15 days |
| malicious-ip-\* | [link](https://github.com/duggytuxy/malicious_ip_addresses) | Private honeypots and other sources |
| snort.org-\* | [link](https://www.snort.org/) | IP Block List maintained by [Cisco Talos](https://talosintelligence.com/) / snort.org: IPs listed in the last 30 days |
| full-\* | | All blocklists, sorted by relevance (IPs present in most files first), duplicates removed |

The IP addresses of Google bots and Bing bots are removed from all files so as not to impact the SEO of the websites.

