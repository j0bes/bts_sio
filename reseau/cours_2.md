# Cours 2 Réseau

> E6: Administration des réseaux

- [Modèle OSI](./cours_2.md#modèle-osi)
- [Modèle TCP/IP](./cours_2.md#modèle-tcpip)

## Modèle OSI
> **OSI** : Open Systems Interconnection = interconnexion des systèmes ouverts

|Numéro|Couche|Utilité/Protocoles|
|---|---|---|
|7|Application|-|
|6|Presentation|-|
|5|Session|-|
|4|Transport|-|
|3|Réseau|-|
|2|Liaison|-|
|1|Physique|-|

Le **modèle OSI** décrit comment deux machines communiquent sur un réseau. Découper en **7 couches**, chacune avec une repsonsabilité précise.

Principe de l'encapsulation des données: est le mécanisme par lequel chaque couche du réseau ajoute ses propres informations (un en-tête) aux données pour permettre leur transmission.

|Couche|Partie|Contenu|
|---|---|---|
|Transport|segment|en-tête de transport (TCP 20 octets/UDP 8 octets) + données|
|Réseau|paquet|en-tête IP + segment|
|Liaison|trame|en-tête de trame + paquet IP + informations de fin éventuelles|
|Physique|bits|des 0 et des 1 qui tranverses les supports de transmissions|

À la réception des bits, le processus inverse, appelé décapsulation, retire successivement les en-têtes pour retrouver les données d’origine.

### Transport
La couche du **transport** est l'une des couches les plus importante pour nous. Car elle contient des protocoles, et des concepts fondamentaux pour un BTS SIO (sisr).

- Mode connecté TCP: confirmation de reception avec l'utilisation d'une synchronisation (SYN) > 200, réponse positive (SYN/ACK) > 201
et donc le client doit lui aussi accuser de reception de la reponse (ACK) n+1
il y a donc réservation des ressources pendant un temps `t`.
Si interruption: erreur 404

    > 💡 On voit donc ici une faille pour saturé un serveur (DoS = *Déni de service*).

- Mode non_connecté UDP: pas de confirmation de reception (média/streaming), il peut donc y avoir des parties manquantes dans les données envoyées.

Cette couche fait aussi le travail de réassemblage des paquets, dans le bon ordre.
#### Port de communication
Les ports permettent de diriger, de centralisé les requêtes en fonction des services demandés.<br>
*Exemple*: `80 = HTTP`

Le client lui choisit un port aléatoire pour sortir (49152 à 65535).<br>
*Exemple notation*: `http://127.0.0.1:5000`

#### TCP & UDP
*À venir.*

### Reseau
*À venir.*

## Modèle TCP/IP
Modèle OSI mais en simplifié, 4 couches:
* Applications : *HTTP, DNS, DHCP, FTP, SMTP*
* Transport : *TCP/UDP & les ports*
* Internet : *IP, ICMP, ARP*
* Accès réseau : *Ethernet, WiFi, MAC*

<hr>
Cours 2 - cours réseau - BTS SIO 1B 2026

[Cours précédent](./cours_1.md)