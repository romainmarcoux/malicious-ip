# Introduction
#### **[FR]**

- Agrégation de 12 listes d'adresses IP malveillantes scindée en fichiers de 131 072 entrées au maximum pour être intégrées dans des pare-feux : Fortinet **__FortiGate__**, Palo Alto, pfSense, OPNsense, IPtables ...
- Adresses IP malveillantes de type **scanners** et **bruteforce**, donc à bloquer **UNIQUEMENT** dans le sens **WAN > LAN**
- Adresses IP ordonnées en fonction du nombre de listes dans lesquelles elles apparaissent (IP malveillantes apparaissant dans le plus de listes sont donc dans le premier fichier full-aa.txt)
- Mise à jour toutes les **heures**

Fichiers à utiliser (liens dans la partie "Links" ci-dessous) :

- full-aa.txt : 131 072 adresses IP les plus malveillantes
- full-aX.txt : autres adresses IP malveillantes
- full-40k.txt : 40 000 adresses IP les plus malveillantes

Les adresses IP de Google Bot et Bing Bot ont été retirées de tous les fichiers pour ne pas impacter le référencement des services.

#### **[EN]**

- Aggregation of 12 lists of malicious IP addresses split into files of a maximum of 131,072 entries to be integrated into firewalls: Fortinet **__FortiGate__**, Palo Alto, pfSense, OPNsense, IPtables ...
- Malicious IP addresses such as scanners and bruteforce, therefore **ONLY** to be blocked in the **WAN > LAN** direction
- Adresses IP classées selon le nombre de listes dans lesquelles elles apparaissent (malicious IPs appearing most frequently first and therefore at the beginning of the full-aa.txt file)
- Updated every **hour**

Files to use (links in the "Links" section below):

- full-aa.txt: 131,072 most malicious IP addresses
- full-aX.txt: other malicious IP addresses
- full-40k.txt: 40,000 most malicious IP addresses

The IP addresses of Google bots and Bing bots are removed from all files so as not to impact the SEO of the websites.

# Menu:

- [Statistics](https://github.com/romainmarcoux/malicious-ip#statistics)
- [FR-EN - Implementation](https://github.com/romainmarcoux/malicious-ip#implementation)
- [Sources](https://github.com/romainmarcoux/malicious-ip#sources)
- [Releases Notes](https://github.com/romainmarcoux/malicious-ip#releases-notes)
- [Contact](https://github.com/romainmarcoux/malicious-ip#contact)

# Statistics
Update of the following table: 2024-03-28 07:44 CEST

| Malicious IP addresses in full-\*                          | %       | Number of IPs |
| ---------------------------------------------------------- | ------- | ------------- |
| Present in 6 sources and more | 3.73 % | 20 577 |
| Present in 5 sources | 2.72 % | 15 016 |
| Present in 4 sources | 4.04 % | 22 239 |
| Present in 3 sources | 4.68 % | 25 793 |
| Present in 2 sources | 14.66 % | 80 707 |
| Present in 1 source | 70.13 % | 385 988 |
| Total | 100 % | 550 320 |

Update of the common IP table with the FortiGate ISDB Malicious-Malicious.Server: 2024-03-28 01:30 CEST

| FortiGate models                                           | full-\* IPs common with ISDB |
| ------------------------------------------------------------ | ----------- |
| 100F and below | 10.38 % |
| 200F and above | 15.03 % |

History of statistics [here](https://github.com/romainmarcoux/malicious-ip/blob/main/statistics/historical_statistics.md).

Classification by [country](https://github.com/romainmarcoux/malicious-ip/blob/main/statistics/country_statistics.md) and [organizations](https://github.com/romainmarcoux/malicious-ip/blob/main/statistics/as_statistics.md) of malicious IP addresses present in at least 2 sources.

# Implementation
#### **[FR]**
**Comment intégrer** ces listes dans un **pare-feu** ?
- **FortiGate**
   * C'est un complément de la base de données ISDB "**Malicious-Malicious.Server**" des FortiGate (statistiques d'IP communes entre la liste full-\* et l'ISDB [ici](https://github.com/romainmarcoux/malicious-ip#statistics)).
   * Menu "Security Fabric → External Connectors → Create New → IP Address"
   * Prendre une URL dans la partie "Links" ci-dessous
   * Après, les listes peuvent être utilisées dans les "Firewall Policy" avec les objets "**IP Address Threat Feed**"
   * Implémentation de la liste full validée même sur le plus petit boitier FortiGate 40F
   * Plus d'informations : mon [tutorial](https://www.linkedin.com/posts/romainmarcoux_bloquer-des-ip-de-listes-externes-sur-fortigate-activity-7112413515725852673-KD4q) et cette [page](https://docs.fortinet.com/document/fortigate/7.0.12/administration-guide/891236/ip-address-threat-feed) de l'aide Fortinet
- **Palo Alto** : [lien](https://docs.paloaltonetworks.com/pan-os/9-1/pan-os-admin/policy/use-an-external-dynamic-list-in-policy/external-dynamic-list). Modèle PA-3200 et supérieurs limités à 150k IP (utilisez uniquement full-aa.txt), modèles inférieurs limités à 50k IP (utilisez le fichier full-40k.txt)
- **pfSense** : via ce [repo](https://github.com/jaredhendrickson13/pfsense-api) GitHub qui permet d'implémenter une API dans pfSense. Attention, par défaut le nombre maximal d'objets est de 400k. 
Possibilité d'augmenter cette valeur si votre pfSense a beaucoup de RAM. Plus d'infos [ici](https://docs.netgate.com/pfsense/en/latest/firewall/aliases.html#alias-sizing-concerns).
- **OPNsense** : via API ([doc](https://docs.opnsense.org/development/api/core/firewall.html). Modifier le nombre maximal d'entrées d'un alias : "Firewall -> Settings -> Advanced -> Firewall Maximum Table Entries".
- **IPTables** avec le paquet "ipset" : [tutorial 1](https://www.malekal.com/comment-utiliser-ipset-sur-linux/) [tutorial 2](https://fr-wiki.ikoula.com/fr/Cr%C3%A9er_et_administrer_facilement_une_blacklist_avec_ipset/iptables)

#### **[EN]**
**How to integrate** these lists into a **firewall**?
- **FortiGate**
   * It is a complement to the FortiGate ISDB "**Malicious-Malicious.Server**" database (common IP address statistics between the full-\* list and the ISDB [here](https://github.com/romainmarcoux/malicious-ip#statistics)).
   * Menu "Security Fabric → External Connectors → Create New → IP Address"
   * Take a URL in the "Links" section below
   * Then, the lists can be used in "Firewall Policy" as "**IP Address Threat Feed**" objects.
   * Implementation of the full list validated even on the smallest FortiGate 40F appliance
   * More information: my [tutorial](https://www.linkedin.com/posts/romainmarcoux_bloquer-des-ip-de-listes-externes-sur-fortigate-activity-7112413515725852673-KD4q) and this [Fortinet help page](https://docs.fortinet.com/document/fortigate/7.0.12/administration-guide/891236/ip-address-threat-feed)
- **Palo Alto**: [here](https://docs.paloaltonetworks.com/pan-os/9-1/pan-os-admin/policy/use-an-external-dynamic-list-in-policy/external-dynamic-list). PA-3200 model and above limited to 150k IP (use full-aa.txt only), lower models limited to 50k IP (use full-40k.txt file)
- **pfSense**: via this GitHub [repo](https://github.com/jaredhendrickson13/pfsense-api) which allows you to implement an API in pfSense. Be careful, by default the maximum number of objects is 400k.
Possibility to increase this value if your pfSense has a lot of RAM. More info here [here](https://docs.netgate.com/pfsense/en/latest/firewall/aliases.html#alias-sizing-concerns).
- **OPNsense** : via API ([doc](https://docs.opnsense.org/development/api/core/firewall.html). Change the maximum number of entries for an alias: "Firewall -> Settings -> Advanced -> Firewall Maximum Table Entries".
- **IPTables** with the "ipset" package: [tutorial 1](https://www.malekal.com/comment-utiliser-ipset-sur-linux/) [tutorial 2](https://fr-wiki.ikoula.com/fr/Cr%C3%A9er_et_administrer_facilement_une_blacklist_avec_ipset/iptables)

# Links

Full aggregation files:

```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-aa.txt
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ab.txt
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ac.txt
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ad.txt
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ae.txt
```

File of the 40,000 most malicious IPs:

```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-40k.txt
```

# Sources

| Filename                                                | Source | History | Description |
| ------------------------------------------------------------ | ----------- | ------- | ----------- |
| abuseipdb-\* | [link](https://www.abuseipdb.com/) | 120d | Collaborative blocklist |
| akamai.com-\* | [link](https://threatintelligence.akamai.com/download-guardicore-cyber-threat-intelligence-data.html) | 30d | IP Block List maintained by Akamai |
| alienvault-fakelabs-\* | [link](https://otx.alienvault.com/pulse/62b111807cf993489def0c3b) | 30d | SSH Brute-Force Honeypot |
| alienvault-georgs-\* | [link](https://otx.alienvault.com/pulse/606d75c11c08ff94089a9430) | 30d | RDP/SSH/VNC intrustion and Trojan request |
| alienvault-ssh-bruteforce-\* | [link](https://otx.alienvault.com/pulse/60ece5998a5b54a5ffe75cb4) | 30d | SSH Brute-Force Honeypot |
| blocklist.de-\* | [link](https://www.blocklist.de/en/export.html) | 30d | Collaborative blocklist ([6k sensors](https://www.blocklist.de/en/index.html)) ([stats](https://www.blocklist.de/en/statistics.html))|
| cinsscore.com-\* | [link](https://cinsscore.com/#list) | 30d | IP Block List maintained by [CINS](https://cinsscore.com/#cins) |
| crowdsec.net-\* | [link](https://www.crowdsec.net/product/crowdsec-security-engine) | 30d | Collaborative blocklist (64k sensors) |
| emergingthreats.net-\* | [link](https://rules.emergingthreats.net/blockrules/) | 30d | IP Block List maintained by [Proofpoint](https://www.proofpoint.com/) |
| greensnow.co-\* | [link](https://greensnow.co/) | 30d | IP Block List maintained by greensnow.co |
| isc.sans.edu-\* | [link](https://isc.sans.edu/xml.html) | 15d | Collaborative blocklist ([500k sensors](https://isc.sans.edu/about.html)): false positives removed |
| malicious-ip-\* | [link](https://github.com/duggytuxy/malicious_ip_addresses) | - | Private honeypots and other sources |
| snort.org-\* | [link](https://www.snort.org/) | 30d | IP Block List maintained by snort.org (owned by [Cisco Talos](https://talosintelligence.com/)) |
| stamparm-\* | [link](https://github.com/stamparm/ipsum) | 30d | Aggregation of lists of malicious IP addresses |
| full-\* | | | All blocklists, sorted by relevance (IPs present in most sources first), duplicates removed |

# Release Notes
- 2024-01-20: New sources: alienvault-ssh-bruteforce, alienvault-georgs, alienvault-fakelabs
- 2024-01-19: New sources: stamparm, akamai
- 2024-01-16: Whitelisting of IP addresses used by French mobile operators
- 2023-12-26: New sources: cinsscore.com, emergingthreats.net, greensnow.co, snort.org
- 2023-10-05: New sources: crowdsec.net, isc.sans.edu
- 2023-09-26: New sources: blocklist.de, abuseipdb.com
- 2023-09-20: Initial release with first source: malicious-ip (github.com/duggytuxy/malicious_ip_addresses)

# Contact
#### **[FR]**

Contactez-moi via LinkedIn ([mon profil](https://linkedin.com/in/romainmarcoux/)) pour :
- m'indiquer des faux positifs
- être notifié quand un **nouveau segment** de fichier est créé (pour l'ajouter dans votre pare-feu)
- me proposer d'ajouter une **autre** source d'adresses IP malveillantes (voir [sources](https://github.com/romainmarcoux/malicious-ip#sources) actuelles)

#### **[EN]**

Contact me via LinkedIn ([my profile](https://linkedin.com/in/romainmarcoux/)) to:
- notify me false positives
- be notified when a **new file** segment is created (to add it to your firewall)
- suggest I add **another** source of malicious IP addresses (see current [sources](https://github.com/romainmarcoux/malicious-ip#sources)
