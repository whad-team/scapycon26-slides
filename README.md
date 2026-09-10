# SSTIC 2025 - We Have A Deal: we provide the Lego bricks, you build cool wireless attacks (FR)

## Plan prévisionnel

### Who are we (1 minute)

 - Présentation

### Motivations (3 minutes)

 - Expliquer l'origine de la systématisation

 - L'intérêt de "tout poser à plat" en ce qui concerne les attaques

 - Un des objectifs majeurs: la création d'un ensemble d'outils (CLI) qui puissent être combinés
   pour réaliser un maximum d'attaques -> faire référence à WHAD

 - On affiche un fingerprinting live des devices sur la slide (+ stats ?)
   - Mention particulière pour les Flipper Zero :D

### Disclaimer (1 minute)

 - l'article dans les actes présente en détail les primitives, leurs choix, => RTFM !
   leur utilisation à des fins de modélisation des attaques courantes, etc.

---< 5 minutes  >--------------------------------------

### Systématisation (7 minutes)

#### La systématisation: méthodologie (4 minutes)

 - Présentation de la méthodologie
   - Définition d'un threat model générique
   - Formalisation de catégories d'attaques
     ( 6 protocoles: WiFi/BLE/ZigBee/Unifying/RF4CE/LoRaWAN )
   - Inférence des briques élémentaires (primitives, actions atomiques) <-- output de la systématisation

 - Les contraintes de la systématisation proposée: <-- ne pas en faire des tonnes !
   - Eviter l'explosion combinatoire
   - Eviter une sur-spécialisation des primitives (généricité de la systématisation)
    
    (
        - En conséquence:
        - pas de prise en compte des aspects couche physique
        - pas de spécialisation des noeuds d'un réseau sans-fil
        - considération d'un "réseau" sans-fil assez large
        - pas de prise en compte des couches logiques (type routage)
    ) -> RTFM !

#### Présentation des primitives (briques Lego) (3 minutes)

 - Vue d'ensemble des briques par catégories
   - Présentation des briques de couche physique: Injection / Capture
   - Présentation des briques de couche logique: Connection / Synchro / Spoofing / Jamming
   - Traitement des PDUs: Forge / Replay / Dump / Transform / Extract

 - Combinaison de primitives: lien logique (flux) / lien temporel

 - Exemples de combinaisons de primitives (on fait le lien avec la présentation précédente sur le Bluetooth Mesh)
   - Modélisation de E1 avec les primitives (Forge + Injection, chaînage logique)
   - Modélisation de E3 avec les primitives (t0: Capture + Extract [Path Request], t1: Forge + Injection)
   - Modélisation de MitM

---< 12 minutes  >--------------------------------------

### De la théorie à la pratique (10 minutes)

 - Rappel de l'objectif: "la création d'un ensemble d'outils (CLI) qui puissent être combinés"

#### WHAD et combinaison (2-3 minutes)

 - Présentation rapide de WHAD: framework + outils CLI
    - framework: API Python (Connecteurs, Devices) utilisable en programmation
    - Outils CLI: collection d'outils utilisant l'API pour implémenter les primitives

 - Combinaison des outils
    - Systèmes de blocs à la GnuRadio -> Top mais super compliqué (et pas CLI !)
    - Pipes UNIX -> ok mais unidirectionnel seulement
    - Solution hybride (pipes bidirectionnels) -> Pipes + sockets Unix

#### Exemples d'utilisation (5 minutes)

 - Attaque par rejeu d'une sonnette 433MHz (YardStickOne):
   - Modélisation de l'attaque et équivalent en ligne de commande
     --------[ théorie ]------    --------[ pratique ]-----------

 - Man-in-the-Middle BLE avec replace de valeur de characteristic à la volée
   - Démo avec remplacement de SMS à la volée
   - Modélisation de l'attaque et équivalent en ligne de commande (théorie / pratique, tout ça ...)

 - Cassage de clé RF4CE + extraction des keystrokes + flux audio <-- utilisation d'une primitive Extract spécialisée

 - Développement de briques complémentaires via l'API Python <--- ne pas trop rentrer dans les détails (RTFM)
   - Exemple de sniffing/déchiffrement de messages Meshtastic via une brique custom
   - (Modélisation + ligne de commande)

#### Le prix de la modularité (rapide+) (2 minutes)

 - cf. papier :D

---< 22 minutes  >--------------------------------------

### Conclusion (3 minutes)

 - Il y a beaucoup plus dans WHAD que ce que l'on a montré (WHAD c'est bien, mangez-en)
 - Appel à contribution (sur la systématisation + WHAD)
 - On remercie les beta-testeurs + contributeurs
 - Renvoi vers les actes SSTIC pour plus d'infos
 - Merci + questions