| Last update: 2026-05-04 10:12 CEST | 548 207 malicious IP |
| ---------------------------------- | -------------------- |

🇫🇷 Agrégation de listes d'adresses IP malveillantes de type **scanners** et **bruteforce**, donc à bloquer **UNIQUEMENT** en **entrée** : dans le sens **WAN > LAN**

🇬🇧 Aggregation of lists of malicious IP addresses such as scanners and bruteforce, therefore **ONLY** to be blocked in the **WAN > LAN** direction

<details>
  <summary><b>🇫🇷⚠️ Introduction : à lire ABSOLUMENT avant utilisation</b></summary>
  <p>

- Agrégation de listes d'adresses IP malveillantes de type **scanners** et **bruteforce**, donc à bloquer **UNIQUEMENT** en **entrée** : dans le sens **WAN > LAN** (pour les IP malveillantes en sortie c'est [ici](https://github.com/romainmarcoux/malicious-outgoing-ip))
- Peut être intégrées dans des pare-feux 🧱 (Fortinet **__FortiGate__**, Palo Alto, Check Point, Sophos, pfSense, OPNsense, IPtables ...), WAF ou serveurs (Linux avec ipset 🐧)
- Adresses IP ordonnées en fonction du nombre de sources dans lesquelles elles apparaissent (IP malveillantes apparaissant dans le plus de sources dans le premier fichier `full-aa.txt`)
- Mise à jour toutes les **heures** ⏱️

Fichiers à utiliser (URL des fichiers dans la partie "URL of files to copy paste" ci-dessous) :

- `full-aa.txt` : **131 072** adresses IP les plus malveillantes
- `full-40k.txt` : **40 000** adresses IP les plus malveillantes
- `full-a\*.txt` : toutes les adresses IP malveillantes en fichiers de **131 072** IP (notamment pour FortiOS < 7.4.4)
- `full-300k-a\*.txt` : toutes les adresses IP malveillantes en fichiers de **300 000** IP (notamment pour FortiOS > 7.4.4)
- `malicious-ip-by-country/full-\*.txt` : toutes les adresses IP malveillantes d'un **pays** (si vous avez besoin du fichier d'un pays manquant, envoyez moi un message)

Liste blanche : les adresses IP des services suivants sont retirées des fichiers : Google Bot, Bing Bot.
</p>
</details>
<details>
  <summary><b>🇬🇧⚠️ Introduction: MUST read before use</b></summary>
  <p>

- Aggregation of lists of malicious IP addresses such as scanners and bruteforce, therefore **ONLY** to be blocked in the **WAN > LAN** direction (for malicious outgoing IP it is [here](https://github.com/romainmarcoux/malicious-outgoing-ip))
- To be integrated into firewalls 🧱 (Fortinet **__FortiGate__**, Palo Alto, Check Point, Sophos, pfSense, OPNsense, IPtables ...), WAF or servers (Linux with `ipset` 🐧)
- IP addresses ordered by the number of sources they appear in (malicious IPs appearing in most sources in the first file `full-aa.txt`)
- Updated every **hour** ⏱️

Files to use (links in the "URL of files to copy paste" section below):

- `full-aa.txt`: **131,072** most malicious IP addresses
- `full-40k.txt`: **40,000** most malicious IP addresses
- `full-a\*.txt`: all malicious IP addresses in **131,072** IP files (especially for FortiOS < 7.4.4)
- `full-300k-a\*.txt`: all malicious IP addresses in **300,000** IP files (especially for FortiOS > 7.4.4)
- `malicious-ip-by-country/full-\*.txt`: all malicious IP addresses of a **country** (if you need a missing country file, send me a message)

Whitelist: IP addresses of the following services are removed from the files: Google Bot, Bing Bot.
</p>
</details>
<details>
  <summary><b>🇫🇷 Est-ce efficace ? 🛡</b></summary>
  <p>

Oui, par exemple, chez un de mes utilisateurs, plus de 300 000 requêtes malveillantes bloquées par jour, rien qu'avec le premier fichier full-aa.txt.

![Efficacite](https://sekio.fr/img/malicious-ip-efficiency.png 'efficacite')

</p>
</details>
<details>
  <summary><b>🇬🇧 Is it effective? 🛡</b></summary>
  <p>

Yes, for example, for one of my users, more than 300,000 malicious requests blocked per day, just with the first full-aa.txt file.

![Efficiency](https://sekio.fr/img/malicious-ip-efficiency.png 'efficiency')

</p>
</details>
<details>
  <summary><b>🇫🇷 Comment l'utilisez dans mes équipements ? 🔧</b></summary>
  <p>

**Comment intégrer** ces listes dans un **pare-feu** ?
- **FortiGate**
   * C'est un complément de la base de données ISDB "**Malicious-Malicious.Server**" des FortiGate (statistiques d'IP communes entre la liste full-\* et l'ISDB, voir section "Statistics").
   * Menu `Security Fabric` → `External Connectors` → `Create New` → `IP Address`
   * Prendre une URL dans la partie "Links" ci-dessous
   * Après, les listes peuvent être utilisées dans les `Firewall Policy` avec les objets "**IP Address Threat Feed**"
   * Plus d'informations : mon [tutorial](https://www.linkedin.com/posts/romainmarcoux_bloquer-des-ip-de-listes-externes-sur-fortigate-activity-7112413515725852673-KD4q), le [tutorial vidéo](https://www.youtube.com/watch?v=cg2fliMQdjo) d'un expert sécurité Fortinet et cette [page](https://docs.fortinet.com/document/fortigate/7.0.12/administration-guide/891236/ip-address-threat-feed) de l'aide Fortinet
- **Palo Alto** : [lien](https://docs.paloaltonetworks.com/pan-os/9-1/pan-os-admin/policy/use-an-external-dynamic-list-in-policy/external-dynamic-list). Modèle PA-3200 et supérieurs limités à 150k IP (utilisez uniquement full-aa.txt), modèles inférieurs limités à 50k IP (utilisez le fichier full-40k.txt)
- **Check Point** : [lien](https://support.checkpoint.com/results/sk/sk132193)
- **Sophos** : [lien](https://docs.sophos.com/nsg/sophos-firewall/21.0/Help/en-us/webhelp/onlinehelp/AdministratorHelp/ActiveThreatResponse/ConfigureFeeds/ThirdPartyThreatFeeds/index.html).
- **pfSense** : via le package [pfBlocker-NG](https://docs.netgate.com/pfsense/en/latest/packages/pfblocker.html). Il faut aussi augmenter le nombre maximum d'entrées : voir [ici](https://docs.netgate.com/pfsense/en/latest/firewall/aliases.html#alias-sizing-concerns).
- **OPNsense** : via API ([doc](https://docs.opnsense.org/development/api/core/firewall.html)). Modifier le nombre maximal d'entrées d'un alias : `Firewall` -> `Settings` -> `Advanced` -> `Firewall Maximum Table Entries`.
- **IPTables** avec le paquet `ipset` sur serveur Linux 🐧 : [tutorial 1](https://www.malekal.com/comment-utiliser-ipset-sur-linux/) [tutorial 2](https://fr-wiki.ikoula.com/fr/Cr%C3%A9er_et_administrer_facilement_une_blacklist_avec_ipset/iptables)

</p>
</details>
<details>
  <summary><b>🇬🇧 How do I use it in my devices? 🔧</b></summary>
  <p>

**How to integrate** these lists into a **firewall**?
- **FortiGate**
   * It is a complement to the FortiGate ISDB "**Malicious-Malicious.Server**" database (common IP address statistics between the full-\* list and the ISDB, see "Statistics" section).
   * Menu `Security Fabric` → `External Connectors` → `Create New` → `IP Address`
   * Take a URL in the "Links" section below
   * Then, the lists can be used in `Firewall Policy` as "**IP Address Threat Feed**" objects.
   * More information: my [tutorial](https://www.linkedin.com/posts/romainmarcoux_bloquer-des-ip-de-listes-externes-sur-fortigate-activity-7112413515725852673-KD4q), the [video tutorial](https://www.youtube.com/watch?v=cg2fliMQdjo) from a Fortinet security expert and this [Fortinet help page](https://docs.fortinet.com/document/fortigate/7.0.12/administration-guide/891236/ip-address-threat-feed)
- **Palo Alto**: [link](https://docs.paloaltonetworks.com/pan-os/9-1/pan-os-admin/policy/use-an-external-dynamic-list-in-policy/external-dynamic-list). PA-3200 model and above limited to 150k IP (use full-aa.txt only), lower models limited to 50k IP (use full-40k.txt file)
- **Check Point** : [link](https://support.checkpoint.com/results/sk/sk132193)
- **Sophos** : [link](https://docs.sophos.com/nsg/sophos-firewall/21.0/Help/en-us/webhelp/onlinehelp/AdministratorHelp/ActiveThreatResponse/ConfigureFeeds/ThirdPartyThreatFeeds/index.html).
- **pfSense**: via the package [pfBlocker-NG](https://docs.netgate.com/pfsense/en/latest/packages/pfblocker.html). The maximum number of entries must be increased: see [here](https://docs.netgate.com/pfsense/en/latest/firewall/aliases.html#alias-sizing-concerns).
- **OPNsense**: via API ([doc](https://docs.opnsense.org/development/api/core/firewall.html)). Change the maximum number of entries for an alias: `Firewall` -> `Settings` -> `Advanced` -> `Firewall Maximum Table Entries`.
- **IPTables** with the `ipset` package on Linux server 🐧 : [tutorial 1](https://www.malekal.com/comment-utiliser-ipset-sur-linux/) [tutorial 2](https://fr-wiki.ikoula.com/fr/Cr%C3%A9er_et_administrer_facilement_une_blacklist_avec_ipset/iptables)

</p>
</details>
<details>
  <summary><b>Statistics 📊</b></summary>
  <p>

Update of the following table: 2026-05-04 10:12 CEST

| Malicious IP addresses in full-\*                          | %       | Number of IPs |
| ---------------------------------------------------------- | ------- | ------------- |
| Present in 6 sources and more | 7.84 % | 43 028 |
| Present in 5 sources | 5.09 % | 27 938 |
| Present in 4 sources | 5.01 % | 27 477 |
| Present in 3 sources | 6.08 % | 33 352 |
| Present in 2 sources | 13.34 % | 73 141 |
| Present in 1 source | 62.61 % | 343 271 |
| Total | 100 % | 548 207 |

Update of the common IP table with the FortiGate ISDB Malicious-Malicious.Server: 2026-05-04 01:50 CEST

| FortiGate models                                           | full-\* IPs common with ISDB |
| ------------------------------------------------------------ | ----------- |
| 100F and below | 5.45 % |
| 200F and above | 5.45 % |

History of statistics [here](https://github.com/romainmarcoux/malicious-ip/blob/main/statistics/historical_statistics.md).

Classification by [country](https://github.com/romainmarcoux/malicious-ip/blob/main/statistics/country_statistics.md) and [organizations](https://github.com/romainmarcoux/malicious-ip/blob/main/statistics/as_statistics.md) of malicious IP addresses present in at least 2 sources.

</p>
</details>
<details>
  <summary><b>🔗 URL of files to copy paste ⧉</b></summary>
  <p>

Files URLs with all malicious IP addresses split in 131,072 IP files (especially for FortiOS < 7.4.4):

```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-aa.txt
```
```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ab.txt
```
```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ac.txt
```
```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ad.txt
```
```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ae.txt
```
```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-af.txt
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ag.txt
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ah.txt
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ai.txt
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-aj.txt
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-ak.txt
```

Files URLs with all malicious IP addresses split in 300,000 IP files (especially for FortiOS > 7.4.4):

```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-300k-aa.txt
```
```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-300k-ab.txt
```
```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-300k-ac.txt
```
```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-300k-ad.txt
```

File URL of the 40,000 most malicious IPs (for small firewall or Palo-Alto < PA-3200):

```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/full-40k.txt
```

URL example of a country file

```
https://raw.githubusercontent.com/romainmarcoux/malicious-ip/main/malicious-ip-by-country/full-fr-aa.txt
```

</p>
</details>
<details>
  <summary><b>Sources</b></summary>
  <p>

| Filename                                                | Source | History | Description |
| ------------------------------------------------------------ | ----------- | ------- | ----------- |
| abuseipdb-\* | [link](https://www.abuseipdb.com/) | 120d | Collaborative blocklist |
| alienvault-fakelabs-\* | [link](https://otx.alienvault.com/pulse/62b111807cf993489def0c3b) | 30d | SSH Brute-Force Honeypot |
| alienvault-georgs-\* | [link](https://otx.alienvault.com/pulse/606d75c11c08ff94089a9430) | 30d | RDP/SSH/VNC intrustion and Trojan request |
| alienvault-ssh-bruteforce-\* | [link](https://otx.alienvault.com/pulse/60ece5998a5b54a5ffe75cb4) | 30d | SSH Brute-Force Honeypot |
| binarydefense.com-\* | [link](https://www.binarydefense.com/) | 30d | IP Block List maintained by Binary Defense |
| blocklist.de-\* | [link](https://www.blocklist.de/en/export.html) | 30d | Collaborative blocklist ([6k sensors](https://www.blocklist.de/en/index.html)) ([stats](https://www.blocklist.de/en/statistics.html))|
| cinsscore.com-\* | [link](https://cinsscore.com/#list) | 30d | IP Block List maintained by [CINS](https://cinsscore.com/#cins) |
| emergingthreats.net-\* | [link](https://rules.emergingthreats.net/blockrules/) | 30d | IP Block List maintained by [Proofpoint](https://www.proofpoint.com/) |
| greensnow.co-\* | [link](https://greensnow.co/) | 30d | IP Block List maintained by greensnow.co |
| isc.sans.edu-\* | [link](https://isc.sans.edu/xml.html) | 20d | Collaborative blocklist ([500k sensors](https://isc.sans.edu/about.html)): false positives removed |
| malicious-ip-\* | [link](https://github.com/duggytuxy/malicious_ip_addresses) | - | Private honeypots and other sources |
| nxdomain.no-\* | [link](https://nxdomain.no/) | - | Bruteforce |
| projecthoneypot.org-\* | [link](https://www.projecthoneypot.org/) | 30d | Collaborative blocklist |
| sekio-\* | - | 30d | Malicious IPs sent by my customers |
| snort.org-\* | [link](https://www.snort.org/) | 30d | IP Block List maintained by snort.org (owned by [Cisco Talos](https://talosintelligence.com/)) |
| stamparm-\* | [link](https://github.com/stamparm/ipsum) | 30d | Aggregation of lists of malicious IP addresses |

</p>
</details>
<details>
  <summary><b>Release notes 📋</b></summary>
  <p>

- 2026-01-27: New source: nxdomain.no
- 2025-02-08: Akamai removed (source no longer available)
- 2024-08-23: Added 300k malicious IP files and malicious IP by country files
- 2024-07-05: New source: projecthoneypot.org
- 2024-06-05: Whitelisting of IP addresses used by Cloudflare
- 2024-05-26: New source: binarydefense.com. Improved exploitation of isc.sans.edu with low signal IPs. Moving historical source files to the source folder.
- 2024-01-20: New sources: alienvault-ssh-bruteforce, alienvault-georgs, alienvault-fakelabs.
- 2024-01-19: New sources: stamparm, akamai.
- 2024-01-16: Whitelisting of IP addresses used by French mobile operators.
- 2023-12-26: New sources: cinsscore.com, emergingthreats.net, greensnow.co, snort.org.
- 2023-10-05: New source: isc.sans.edu.
- 2023-09-26: New sources: blocklist.de, abuseipdb.com.
- 2023-09-20: Initial release with first source: malicious-ip (github.com/duggytuxy/malicious_ip_addresses).

</p>
</details>
<details>
  <summary><b>To support me 🫴</b></summary>
  <p>

[![BuyMeACoffee](https://raw.githubusercontent.com/romainmarcoux/romainmarcoux/main/img/buymeacoffee.png 'BuyMeACoffee')](https://buymeacoffee.com/romainmarcoux)
[![Paypal](https://www.paypalobjects.com/en_US/FR/i/btn/btn_donateCC_LG.gif 'Paypal')](https://www.paypal.com/donate/?hosted_button_id=TNPNMMBFVVL8E)

</p>
</details>
<details>
  <summary><b>🇫🇷 Qui suis-je ?</b></summary>
  <p>

Je suis expert freelance en cybersécurité, notamment sur les pare-feux.

Je maintiens ce projet depuis 2023 pour aider la communauté à se protéger contre les cybermenaces.

N'hésitez pas à me consulter pour vos besoins d'expertise pare-feux (audit, intégration, migration, problématiques ...) : voir contact ci-dessous.

</p>
</details>
<details>
  <summary><b>🇬🇧 Who am I?</b></summary>
  <p>

I am a freelance cybersecurity expert, particularly on firewalls.

I have been maintaining this project since 2023 to help the community protect itself against cyber threats.

Do not hesitate to consult me for your firewall expertise needs (audit, integration, migration, issues, etc.): see contact below.

</p>
</details>
<details>
  <summary><b>🇫🇷 📬 Pour me contacter (faux positifs, idées, remerciements ...)</b></summary>
  <p>

Contactez-moi via LinkedIn ([mon profil](https://linkedin.com/in/romainmarcoux/)) pour :
- m'indiquer des faux positifs
- me proposer d'ajouter une **autre** source d'adresses IP malveillantes (voir section "Sources" ci-dessus)
- me solliciter pour vos besoins d'expertise pare-feux (audit, intégration, migration, problématiques ...)
- me remercier et m'encourager pour le maintien de ce projet 😉

</p>
</details>
<details>
  <summary><b>🇬🇧 📬 To contact me (false positives, ideas, thanks, etc.)</b></summary>
  <p>

Contact me via LinkedIn ([my profile](https://linkedin.com/in/romainmarcoux/)) to:
- notify me false positives
- suggest I add **another** source of malicious IP addresses (see "Sources" section above)
- to consult me for your firewall expertise needs (audit, integration, migration, issues, etc.)
- thank me and encourage me for maintaining this project 😉

</p>
</details>

