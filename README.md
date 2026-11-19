# 📶 MeshCore Local Interface pour PC Linux ou Windows ou Mac

<img src="logo-mesh.png" align="center"/>



Pourquoi j'ai créé cette application : 
L'écosystème manquait d'une solution simple : discuter sans se prendre la tête, avec juste un fichier et une antenne MeshCore. Résultat : communiquez avec vos amis, votre famille, vos collègues ou même des inconnus. 

Bref Bienvenue sur la toile numérique sans être connecté forcement à internet être libre et résilient cela commence ici.


Je suis en cours de développement  du programme :
Chaque semaine j'actualise mais si j'ai des bugs n’hésitez pas a me le dire je serai ravi d'essayer de remettre au gout du jour.




**Télécharger le fichier nommé meshcore-local-v9.html 
c'est Un client web pour radios [MeshCore](https://meshcore.fr), tenu dans un seul fichier HTML, qui fonctionne en local dans votre navigateur.**

Branchez votre radio MeshCore en **USB** ou en **Bluetooth**, puis échangez des messages, consultez vos contacts, voyez le maillage sur une carte ou en 3D, surveillez vos répéteurs et analysez votre antenne. Il n'y a rien à installer et aucun compte à créer. Vos messages restent sur votre ordinateur.

> Application non officielle, développée par [IndomptableBar](https://github.com/indomptableBar) pour la communauté Meshcore. Elle n'est pas affiliée à l'équipe MeshCore.

---

## ✨ À quoi ça sert ?

MeshCore est un réseau maillé LoRa : les messages passent de radio en radio, sans Internet ni réseau mobile. L'application officielle tourne sur smartphone. **MeshCore Local** apporte les mêmes fonctions de base sur ordinateur, avec en plus des outils d'analyse :

- 💬 discuter avec vos contacts et sur les canaux ;
- 🔎 voir **par où un message est passé** (relais, distances, carte animée) ;
- 📡 connaître la **puissance réelle émise** par votre radio et la qualité de votre antenne ;
- 👁 être prévenu quand un **répéteur tombe en panne**.

---

## 🚀 Démarrage rapide

1. **Flashez votre radio** avec un firmware **Companion** :
   - `companion_radio_usb` pour une connexion par câble USB ;
   - `companion_radio_ble` pour une connexion Bluetooth.

   Vous pouvez flasher depuis [flasher.meshcore.co.uk](https://flasher.meshcore.co.uk). Les firmwares *Repeater* et *Room server* ne se connectent pas à l'application.
2. **Téléchargez** le fichier `meshcore-local-v9.html`.
3. **Ouvrez-le** dans **Chrome**, **Edge** ou **Opera** (double-clic sur le fichier, ou via `http://localhost`).
4. Cliquez sur **🔌 USB** ou **📶 Bluetooth** en haut, puis choisissez votre radio.

L'application lit alors votre identité, vos contacts, vos canaux et les messages en attente.
---

## 🧭 Les onglets

| Onglet | Ce qu'il fait |
|---|---|
| 💬 **Messages** | Conversations privées et canaux. Chaque message reçu affiche l'heure, le SNR et le nombre de sauts. Le lien **« détails »** ouvre le parcours complet du message : émetteur → relais → vous, avec distances, RSSI, puissance en mW et région d'origine. Le parcours peut être rejoué en animation sur la carte. |
| 👥 **Contacts** | Liste des nœuds connus (compagnons, répéteurs, room servers, capteurs), dernier advert, chemin, position. Permet de partager ou d'importer un contact (`meshcore://…`), de réinitialiser un chemin et de supprimer un contact. |
| 🧊 **Visualisation** | Le maillage en 3D, disposé selon la géographie ou par type de nœud. Les liens viennent des chemins mémorisés par votre radio. |
| 🗺️ **Carte** | Vos contacts sur OpenStreetMap, avec plusieurs fonds de carte. Les nœuds sans GPS peuvent être **placés à la main** ; ces positions restent dans votre navigateur. |
| 📡 **Antenne** | Statistiques et analyse de votre radio (détails plus bas). |
| 👁 **Surveillance** | Suivi en ligne / hors ligne des nœuds de votre choix, contrôlé chaque minute (voir plus bas). |
| # **Canaux** | Rejoindre un canal public `#hashtag` (clé dérivée du nom, comme dans l'appli officielle) ou créer un canal privé avec une clé secrète. |
| ⚙️ **Réglages** | Nom, position, adverts, paramètres radio (préréglages Europe / USA), puissance TX avec conversion dBm ↔ mW, annuaire des répéteurs, options. |
| 🧾 **Journal** | Journal technique (et trames brutes en hexadécimal si l'option est activée). |

---

## 📡 L'onglet Antenne en détail

L'onglet se rafraîchit toutes les 10 secondes et regroupe :

- **Signal** : plancher de bruit (avec historique), dernier SNR et RSSI, marge sur le bruit.
- **Temps d'antenne** : temps d'émission et de réception, comparés à la limite réglementaire de la bande utilisée (par exemple 10 % sur 869,4–869,65 MHz).
- **Paquets** : reçus, envoyés, flood / direct, erreurs.
- **Matériel** : modèle, firmware, puce radio, GPS, écran, alimentation.
- **Paramètres radio & antenne** :
  - fréquence, BW, SF, CR, longueur d'onde, taille d'un fouet λ/4 ou d'un dipôle λ/2 ;
  - **réglage TX de la puce** *et* **puissance réelle en sortie** ;
  - temps d'émission d'un message, débit, sensibilité théorique ;
  - **tableau de conversion dBm ↔ mW ↔ tension** sur toute la plage de votre appareil.
- **Mon antenne** : vous saisissez le gain, les pertes de câble et la hauteur. L'application calcule la **PIRE / PAR**, la **conformité réglementaire**, le bilan de liaison, la portée théorique, l'horizon radio et la zone de Fresnel.
- **Mesures de session** et **lieux d'origine des messages**, calculés localement.

### Réglage TX ≠ puissance émise

Le réglage TX MeshCore pilote la **puce radio** (de −9 à +22 dBm pour une SX1262). Sur un appareil équipé d'un **amplificateur**, comme le Heltec V4, la puissance réelle est plus élevée : un réglage de 10 donne environ 21 dBm en sortie. L'application affiche les deux valeurs et fait tous ses calculs sur la puissance réelle.

### Appareils reconnus

L'appareil est détecté automatiquement d'après le modèle lu sur la radio. Vous pouvez aussi le choisir dans **Antenne → Mon antenne**.

| Appareil | Puce | Amplificateur | Puissance max |
|---|---|---|---|
| Heltec WiFi LoRa 32 V3 | SX1262 | — | 21 ± 1 dBm |
| Heltec WiFi LoRa 32 V4 (haute puissance) | SX1262 | GC1109 / KCT8103L | 28 ± 1 dBm |
| Heltec WiFi LoRa 32 V4 (basse puissance) | SX1262 | — | 22 dBm |
| LilyGo T-Echo | SX1262 | — | 22 dBm |
| LilyGo T-Beam (SX1262) | SX1262 | — | 22 dBm |
| LilyGo T-Beam (ancienne version) | SX1276 | — | 20 dBm |
| LilyGo T-Deck Plus | SX1262 | — | 22 dBm |
| Heltec Mesh Node T114 | SX1262 | — | 22 dBm |
| Seeed SenseCAP T1000-E | LR1110 | — | 22 dBm |
| RAK WisMesh Tag | SX1262 | — | 22 dBm |
| RAK4631 WisBlock | SX1262 | — | 22 dBm |
| Seeed SenseCAP Solar Node P1 Pro | SX1262 | — | 22 dBm |

Pour le Heltec V4, deux courbes réglage → puissance réelle sont proposées : la table officielle Heltec, ou des mesures au banc publiées par la communauté.

> ⚠️ La radio ne sait pas quelle antenne est branchée. Le gain proposé est une valeur indicative : saisissez celui de **votre** antenne pour obtenir des calculs justes.

---

## 👁 Surveillance des répéteurs

Ajoutez un nœud depuis le parcours d'un message (**👁 surveiller**) ou depuis sa fiche sur la carte. Chaque minute, l'application vérifie s'il a été entendu récemment :

- advert capté ;
- message envoyé (direct ou sur un canal) ;
- paquet relayé (son empreinte apparaît dans le chemin) ;
- réponse à une **sonde de statut** (option, pour les répéteurs et room servers).

S'il reste silencieux plus longtemps que le seuil choisi (120 min par défaut), il passe **🔴 hors ligne** et vous êtes alerté par un message et, si vous les activez, par une notification. Une frise montre sa disponibilité sur 24 h.

> La surveillance ne tourne que si la page est ouverte et la radio connectée.

---

## 🔒 Vie privée et fonctionnement hors ligne

- **Messages, contacts, positions manuelles et réglages** sont stockés uniquement dans votre navigateur (`localStorage`), séparément pour chaque radio.
- Aucune donnée n'est envoyée à un serveur, **sauf** pour ces fonctions facultatives :

| Fonction | Ce qui est chargé ou envoyé |
|---|---|
| 🧊 Visualisation 3D | bibliothèque three.js (CDN jsDelivr) |
| 🗺️ Carte | bibliothèque Leaflet (CDN unpkg) et tuiles OpenStreetMap |
| Nom de lieu des messages *(option, désactivée par défaut)* | coordonnées envoyées à Nominatim (OpenStreetMap) |
| Résolution en ligne des relais inconnus *(option)* | empreintes de relais envoyées à une instance CoreScope |

Sans Internet, la messagerie, les contacts, les canaux, l'onglet Antenne et la surveillance fonctionnent normalement. Pour identifier les relais hors ligne, importez un fichier de nœuds JSON dans **Réglages → Annuaire des répéteurs**.

---

## ❓ Problèmes fréquents

| Problème | Solution |
|---|---|
| Les boutons USB / Bluetooth sont grisés | Utilisez Chrome, Edge ou Opera. Firefox et Safari ne prennent pas en charge Web Serial ni Web Bluetooth. |
| La radio n'apparaît pas | Vérifiez qu'elle a un firmware **Companion** (USB ou BLE selon la connexion) et fermez les autres applications connectées à la radio. |
| « Contexte non sécurisé » dans le Journal | Ouvrez le fichier directement (`file://`) ou via `http://localhost`, pas via une adresse réseau en `http://`. |
| Les statistiques d'antenne sont vides | Votre firmware ne fournit pas `CMD_GET_STATS` : mettez-le à jour. Les mesures de session fonctionnent quand même. |
| La carte ou la 3D ne s'affiche pas | Ces onglets ont besoin d'Internet pour charger leurs bibliothèques, au moins la première fois. |
| Rien ne passe avec les autres nœuds | Tous les nœuds doivent avoir **exactement** les mêmes fréquence, BW, SF et CR (onglet Réglages). |

---

## 🛠 Pour les développeurs

- Tout tient dans **un seul fichier HTML** : HTML, CSS et JavaScript, sans dépendance à compiler.
- Protocole : MeshCore **Companion Radio Protocol** (trames USB `<`/`>` + longueur, ou service BLE Nordic UART).
- Bibliothèques chargées à la demande : [three.js](https://threejs.org) et [Leaflet](https://leafletjs.com).

Les contributions sont bienvenues : ouvrez une *issue* pour signaler un bug, ou une *pull request*. Pour un appareil manquant ou mal reconnu, indiquez son nom exact tel qu'il apparaît dans **Antenne → Matériel → Modèle**.

---

## 📜 Avertissement

Respectez la réglementation radio de votre pays : puissance maximale (PAR / PIRE) et temps d'émission dans chaque bande. 
Les calculs de l'application sont donnés **à titre indicatif** et ne remplacent pas une mesure.


<img src="logo.png" align="center"/>

N'hesitez pas a me mettre un petit like par une étoile 🌠 au haut a droite du projet pour témoigner votre soutien cela me ferai plaisir si vous avez un compte github si non.
On s'en fiche on se rencontrera surement sur les ondes :)
