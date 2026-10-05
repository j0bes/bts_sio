# Cours 1 Réseau

> E6: Administration des réseaux

* [Introduction](./cours_1.md#réseau-informatique)
* [Identifier une machine sur un réseau](./cours_1.md#identifier-une-machine-sur-un-réseau)
* [Caractéristiques d'un réseau](./cours_1.md#caractéristiques-dun-réseau)
* [Topologies réseau](./cours_1.md#topoligies-réseau)
* [Échelle réseau](./cours_1.md#échelle-de-réseau)

## Réseau informatique

Un réseau est un ensemble de périphériques connectés avec des équipements réseau via des supports de transmission.

* Périphériques: *machines (ordinateur, serveur),*
* Équipements réseau: *switch, routeur,*
* Supports de transmission des données: *câble en cuivre, air, lumière*

> 💡 **Important**<br>
> Internet est un réseau de réseaux.<br>
> Un réseau n'a pas besoin d'internet pour fonctionner.

## Identifier une machine sur un réseau

### Adresse physique

Toute machine pouvant se connecter à un réseau possède une carte réseau; ordinateur, téléphone, imprimante, etc... Cette carte réseau possède un identifiant unique dans le monde permettant de la reconnaître, c'est l'**adresse physique/MAC**.

Elle est codée sur 48 bits. 3 octets dédiés à l'identification du constructeur (code constructeur), 3 octets pour le numéro de série de la carte réseau.<br>
*Exemple*: `2C:58:B9:0B:9E:D7`

### Adresse logique

Cependant, une adresse physique ne suffit pas pour assurer la communication de deux machines sur un même réseau. Il faut donc lui associer une adresse logique plus communément appelée **adresse IP**. Cette adresse peut être attribuée manuellement ou de manière automatique avec un service **DHCP** (on abordera cette notion plus tard).

Elle est codée sur 32 bits.<br>
*Exemple*: `78.123.8.12`

> On différenciera les adresses IP **privées** et **publiques**.<br>

<hr>

**@IP Privé**:<br>
On les utilise au sein d'un réseau local, par exemple chez soi, dans une entreprise ou dans une école. Ces adresses ne sont pas directement accessibles depuis un réseau extérieur.

**Principales plages d'adresses IPv4 privées**

|plage|taille|
|:--------------|:--------|
|   `10.0.0.0/8`   | 16 777 216 |
|  `172.16.0.0/12` |  1 048 576 |
| `192.168.0.0/16` |   65 536   |

Ces adresses permettent donc la communication entre les machines d'un même réseau.

#### @IP Publique

On les utilise pour identifier un réseau sur internet. Ces adresses communiquent directement avec le dehors, et généralement une seule IP publique est attribuée par foyer (box à la maison).

Pour exemple, voici un schéma représentant un réseau domestique (maison):

```txt
             INTERNET
                 │
            IP publique
             80.x.x.x
                 │
               [BOX]
            192.168.0.1
              (privée)
                 │
       ┌─────────┴─────────┐
       │                   │
  192.168.0.10        192.168.0.11
      PC                Téléphone
    (privée)             (privée)
```

> 💡 **À retenir**:<br>
> MAC = matériel - IP = réseau<br>
> Privé = réseau local - Publique = internet

## Caractéristiques d'un réseau

* **Bande passante** (Mb/s - Gb/s): débit maximal théorique,
* **Débit réel**: Quantité de données réellement transmise,
* **Latence** (ms): Délai de transmission d'un bout à l'autre,
* **Fiabilité** (%): Disponibilité et taux d'erreurs/pertes

## Topologies réseau

| topologie | avantages                                     | inconvénients                                       | usage typique                |
| --------- | --------------------------------------------- | --------------------------------------------------- | ---------------------------- |
| Bus       | Simple, peu coûteux, peu de câble             | panne du bus = panne de tout le réseau (collisions) | anciens réseaux              |
| Étoile    | Panne isolée, évolutive, facile à administrer | dépend du commutateur central                       | LAN d'entreprises (standard) |
| Anneau    | Débit régulier, pas de collision              | Rupture d'un nœud impacte la boucle                 | Réseaux historiques          |
| Maillée   | Très fiable, redondante, tolérante aux pannes | Coûteuse, câblage complexe                          | WAN, cœur de réseau          |

Les topologies ne sont pas forcément à connaître par cœur, simplement il est important de savoir les visualiser.

## Échelle de réseau

* **PAN** *Personal*: Quelques mètres, Bluetooth - USB
* **LAN** *Local*: Réseau domestique/entreprise, Ethernet - WiFi
* **MAN** *Metropolitan*: Interconnexions de sites au sein d'une ville, Fibre - FH
* **WAN** *Wide*: Interconnexions de réseaux distants, Internet

<hr>
Cours 1 - cours réseau - BTS SIO 1B 2026
