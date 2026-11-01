# Cours 1 Réseau

> E6: Administration des réseaux

Cette fiche explique les bases du réseau **sans prérequis**. Pas besoin de tout comprendre du premier coup : on part d'images simples, puis les vrais concepts.

**Sommaire**
* [Qu'est-ce qu'un réseau ?](./cours_1.md#quest-ce-quun-réseau-)
* [Les topologies : la forme du réseau](./cours_1.md#les-topologies--la-forme-du-réseau)
* [Les échelles : la taille du réseau](./cours_1.md#les-échelles--la-taille-du-réseau)
* [Adresses MAC et IP : qui est qui ?](./cours_1.md#adresses-mac-et-ip--qui-est-qui-)
* [Le modèle OSI](./cours_1.md#le-modèle-osi)
* [Le modèle TCP/IP](./cours_1.md#le-modèle-tcpip)

## Qu'est-ce qu'un réseau ?

Un **réseau informatique**, est un ensemble de machines qui peuvent **s'échanger des données**.

On peut le comparer à un **réseau routier** : des villes (les machines), des routes (les câbles ou le Wi-Fi) et des carrefours (les équipements qui orientent la circulation).

Il y a donc 3 ingrédients :

| Ingrédient | Rôle | Exemples |
|:--|:--|:--|
| **Périphériques** (ou *hôtes*) | Ceux qui envoient et reçoivent des données | PC, serveur, téléphone, imprimante |
| **Équipements réseau** | Ceux qui font circuler les données | **switch** (commutateur), **routeur** |
| **Supports de transmission** | Le chemin physique | câble cuivre (Ethernet), fibre optique (lumière), Wi-Fi (ondes) |

> 💡 **À retenir**
> - **Internet est un « réseau de réseaux »** : des millions de petits réseaux reliés entre eux.
> - Un réseau **n'a pas besoin d'Internet** pour fonctionner. Deux PC reliés par un câble forment déjà un réseau.

### Comment mesure-t-on la qualité d'un réseau ?

Image : un **tuyau d'eau**.

| Notion | Image | Unité |
|:--|:--|:--|
| **Bande passante** | Le *diamètre* du tuyau : ce qu'il peut faire passer au maximum | Mb/s, Gb/s |
| **Débit réel** | Ce qui coule *vraiment* en ce moment | Mb/s |
| **Latence** | Le temps pour que la *première goutte* arrive | ms |
| **Fiabilité** | Le tuyau est-il souvent en panne ou percé ? | % |

## Les topologies : la forme du réseau

La **topologie**, c'est la **façon dont les machines sont reliées** entre elles (le « plan » du réseau).

| Topologie | Avantage | Inconvénient | Où la trouve-t-on ? |
|:--|:--|:--|:--|
| **Bus** | Simple, peu de câble | Un câble coupé = tout le réseau tombe | Anciens réseaux |
| **Étoile** | Une panne reste isolée, facile à agrandir | Dépend du switch central | **Réseaux d'entreprise (le standard)** |
| **Anneau** | Débit régulier | Une rupture gêne toute la boucle | Réseaux historiques |
| **Maillée** | Très fiable (plusieurs chemins possibles) | Coûteuse, câblage complexe | Cœur d'Internet, WAN |

> 💡 Inutile de tout apprendre par cœur : il faut surtout savoir les **reconnaître sur un schéma**. Retiens que **l'étoile est la plus courante** aujourd'hui.

## Les échelles : la taille du réseau

On classe aussi les réseaux selon **la distance qu'ils couvrent**.

| Sigle | Nom | Taille | Exemples |
|:--|:--|:--|:--|
| **PAN** | *Personal Area Network* | Quelques mètres | Bluetooth, USB (ton casque et ton téléphone) |
| **LAN** | *Local Area Network* | Une maison, une école, une entreprise | Ethernet, Wi-Fi |
| **MAN** | *Metropolitan Area Network* | Une ville | Fibre, faisceaux hertziens |
| **WAN** | *Wide Area Network* | Pays, continents | **Internet** |

```txt
PAN ⊂ LAN ⊂ MAN ⊂ WAN
```

Le **LAN** est la plus courante, surtout lors du BTS SIO.

## Adresses MAC et IP : qui est qui ?

Pour que des machines se parlent, il faut pouvoir **les identifier**. On utilise deux adresses, qui ont chacune leur rôle.

> 💡 **Image : une personne**
> - L'**adresse MAC** = ton **numéro de sécurité sociale** : il t'est attribué à la naissance et te suit partout.
> - L'**adresse IP** = ton **adresse postale** : elle change selon l'endroit où tu es installé.

### L'adresse MAC (adresse physique)

- Gravée dans la **carte réseau** de chaque appareil (PC, téléphone, imprimante…) par le constructeur.
- **Unique au monde**.
- Codée sur **48 bits**, écrite en **hexadécimal** : `2C:58:B9:0B:9E:D7`
  - les 3 premiers octets (`2C:58:B9`) identifient le **constructeur**,
  - les 3 derniers (`0B:9E:D7`) sont le **numéro de série** de la carte.
### L'adresse IP (adresse logique)

- Donnée à la machine **par le réseau** : elle change si tu changes de réseau.
- Codée sur **32 bits** (IPv4), écrite en 4 nombres de 0 à 255 : `192.168.0.10`
- Attribuée **à la main** (IP statique) ou **automatiquement** par un service appelé **DHCP**, qui distribue les adresses.
### IP privée ou IP publique ?

| | **IP privée** | **IP publique** |
|:--|:--|:--|
| Usage | À l'intérieur d'un réseau local | Pour être vu sur Internet |
| Visible depuis Internet ? | Non | Oui |
| Combien ? | Chaque appareil du LAN en a une | Une seule pour tout le foyer (celle de la box) |

Plages d'adresses **privées** (réservées aux LAN) :

| Plage | Nombre d'adresses |
|:--|--:|
| `10.0.0.0/8` | 16 777 216 |
| `172.16.0.0/12` | 1 048 576 |
| `192.168.0.0/16` | 65 536 |

> Le `/8`, `/12`, `/16` indique la taille du réseau (**le masque**). On le détaillera plus tard dans les prochains cours.

Exemple : un réseau domestique.

```txt
             INTERNET
                 │
            IP publique
             80.x.x.x
                 │
               [BOX]
            192.168.0.1   ← IP privée de la box
                 │
       ┌─────────┴─────────┐
       │                   │
  192.168.0.10        192.168.0.11
     PC_01               PC_02
```

### La relation entre l'IP et le MAC

Quand le PC_01 veut intéragir avec `192.168.0.11`, il connaît son **IP** mais pas sa **MAC**. Il envoie donc dans le réseau : *« Qui possède l'IP 192.168.0.11 ? »* Le PC_02 répond : *« C'est moi, voici mon adresse MAC. »* Ce mécanisme s'appelle **le protocole ARP**.

> 💡 **À retenir**
> - **MAC = matériel** (identifie la carte) / **IP = réseau**
> - **Privée = réseau local** / **Publique = Internet**

À essayer sur ton PC : tape `ipconfig /all` (Windows) ou `ip a` (Linux) pour voir ta MAC et ton IP.

## Le modèle OSI

### Pourquoi un modèle ?

Envoyer un fichier d'un PC à un autre implique des centaines de petites tâches : encoder les données, choisir le chemin, gérer les erreurs, convertir en signal électrique… C'est pourquoi on a **découpé en 7 couches** le chemin emprunter par les données. Chaque couche a **un rôle précis** et ne se préoccupe pas des autres.

**OSI** = *Open Systems Interconnection* (interconnexion des systèmes ouverts).

> 💡 **Image : envoyer un colis**<br>
> Tu écris la lettre (application), tu la mets dans une enveloppe avec l'adresse (réseau), le facteur la dépose dans sa tournée (liaison), le camion roule sur la route (physique). Chaque étape ignore les détails des autres.

### Les 7 couches

| N° | Couche | Rôle en une phrase | Exemples |
|:-:|:--|:--|:--|
| 7 | **Application** | Le service utilisé par l'utilisateur | HTTP, DNS, SMTP, FTP |
| 6 | **Présentation** | Format et chiffrement des données | Chiffrement, compression |
| 5 | **Session** | Ouvre, maintient et ferme la conversation | Sessions |
| 4 | **Transport** | Découpe les données et assure leur livraison | **TCP, UDP**, ports |
| 3 | **Réseau** | Choisit le chemin et adresse les paquets | **IP**, routeur |
| 2 | **Liaison** | Livre la donnée à la machine voisine | **MAC**, Ethernet, switch |
| 1 | **Physique** | Transporte les 0 et les 1 | Câbles, Wi-Fi, fibre |

> 💡 À retenir pour la suite : **routeur = couche 3** (il lit les IP), **switch = couche 2** (il lit les MAC).

### L'encapsulation

Le chemin que parcours les données est de haut en bas à travers les différentes couches. À chaque étape, la couche ajoute **son enveloppe** (un **en-tête**) avec les informations dont elle a besoin.

```txt
Couche        Nom ensemble      Contenu
─────────────────────────────────────────────────────────────────────────
Application                                        [    DONNÉES    ]
Transport     → segment                       [TCP][    DONNÉES    ]
Réseau        → paquet                    [IP][TCP][    DONNÉES    ]
Liaison       → trame           [ETHERNET][IP][TCP][    DONNÉES    ][FIN]
Physique      → bits            0100110101001101...
```

| Couche | Nom de l'ensemble de données | Ce qu'on ajoute |
|:--|:--|:--|
| Transport | **Segment** | en-tête TCP ou UDP (ports) |
| Réseau | **Paquet** | en-tête IP (adresses IP) |
| Liaison | **Trame** | en-tête avec les adresses MAC |
| Physique | **Bits** | rien : on envoie des 0 et des 1 |

À l'arrivée, le destinataire fait l'inverse : c'est la **décapsulation**. Il ouvre les enveloppes une à une, de la plus extérieure à la plus intérieure, pour retrouver les données d'origine.

## Le modèle TCP/IP

Le modèle OSI est surtout **théorique** (un modèle pour comprendre). **TCP/IP** est le modèle **réellement utilisé** sur Internet. Il fait la même chose, mais avec **4 couches** au lieu de 7.
 
| TCP/IP | Correspond à OSI | Protocoles |
|:--|:--|:--|
| **4. Application** | 7 + 6 + 5 | HTTP, DNS, DHCP, FTP, SMTP |
| **3. Transport** | 4 | TCP, UDP, ports |
| **2. Internet** | 3 (Réseau) | IP, ICMP, ARP |
| **1. Accès réseau** | 2 + 1 (Liaison + Physique) | Ethernet, Wi-Fi, MAC |
 
```txt
        OSI                          TCP/IP
┌─────────────────┐
│ 7 Application   │
│ 6 Présentation  │  ───────────►  4  Application
│ 5 Session       │
├─────────────────┤
│ 4 Transport     │  ───────────►  3  Transport
├─────────────────┤
│ 3 Réseau        │  ───────────►  2  Internet
├─────────────────┤
│ 2 Liaison       │
│ 1 Physique      │  ───────────►  1  Accès réseau
└─────────────────┘
```
 
### La couche Transport : TCP ou UDP ?
 
**Important pour les SISR.**
 
| | **TCP** | **UDP** |
|:--|:--|:--|
| Image | Un **appel téléphonique** : on vérifie que l'autre est là | Une **carte postale** : on poste et on espère |
| Connexion | Oui, avec échange préalable | Non |
| Fiabilité | Confirmation de réception, ordre respecté, renvoi si perte | Aucune garantie |
| Vitesse | Plus lent | Plus rapide |
| Utilisation | Web, mails, transfert de fichiers | Streaming, appels vidéo, jeux en ligne |
 
**La « poignée de main » TCP** (*three-way handshake*) avant d'échanger :
 
```txt
 Client                      Serveur
   │ ── SYN ─────────────────►  │   « Allô ? Tu m'entends ? »
   │ ◄───────────── SYN/ACK ──  │   « Oui je t'entends, et moi ? »
   │ ── ACK ─────────────────►  │   « Oui, on peut commencer. »
```
 
> 💡 **Pourquoi c'est important en cybersécurité ?** Le serveur **réserve des ressources** dès le premier `SYN`. Si un attaquant envoie des milliers de `SYN` sans jamais finir la poignée de main, le serveur sature : c'est une attaque par **déni de service (DoS)**.
 
La couche transport s'occupe aussi de **découper** les données en segments, puis de les **remettre dans le bon ordre** à l'arrivée.
 
### Les ports
 
> 💡 **Image : un immeuble**<br>
> L'**adresse IP** est l'adresse de l'immeuble, le **port** est le **numéro de l'appartement**. L'IP trouve la bonne machine, le port trouve le bon **service** sur cette machine.
 
| Port | Service |
|:-:|:--|
| 22 | SSH (accès à distance sécurisé) |
| 53 | DNS (traduit un nom de site en adresse IP) |
| 80 | HTTP (web) |
| 443 | HTTPS (web chiffré) |
 
Côté client, le port d'envoi est choisi **au hasard** (entre 49152 et 65535).
 
On l'écrit après l'adresse IP, séparé par `:` > `http://127.0.0.1:5000`

---
Cours 1 - Réseau - BTS SIO 1B 2026