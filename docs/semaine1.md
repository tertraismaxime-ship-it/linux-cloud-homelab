# Semaine 1

## Jour 1
- Installation de VMware Workstation Pro
- Installation d’Ubuntu Server 24.04 LTS
- Activation du serveur SSH durant l’installation
- Première connexion à la VM Linux

---

## Jour 2

### Mise en place de l’environnement de travail
- Connexion de VS Code à Ubuntu via SSH
- Création du projet Linux dans :
  `/home/maxime/Linux-Cloud-Homelab`

### Structure du projet

Création des dossiers :
- docs
- scripts
- docker
- ansible
- screenshots

### Révision commandes Linux 
- pwd
- ls
- ls -la
- cd
- mkdir
- touch
- cp
- mv
- rm
- nano
- cat
- sudo

### Outils installés
- git
- tree
- htop
- curl
- wget
- net-tools

### Compréhension acquise
- Différence entre Windows et environnement Linux distant
- Utilisation de SSH pour administrer une machine Linux
- Utilisation de VS Code comme terminal distant Linux
- Structure d’un projet Linux/cloud

---

## Jour 3

### Réseau Linux

#### Adresse IP de la VM
- 192.168.126.129/24

#### Interface réseau
- ens33

#### Passerelle
- 192.168.126.2

#### DNS observé
- Resolver local Ubuntu : 127.0.0.53
- DNS VMware NAT : 192.168.126.2

### Compréhension DNS

Ubuntu utilise `systemd-resolved` comme resolver DNS local.

Les requêtes DNS sont ensuite relayées vers le service NAT VMware, qui transmet les requêtes aux serveurs DNS réels du réseau Windows/routeur.

---

### Tests réseau effectués

#### Test connectivité IP

```bash
ping 8.8.8.8
```

Résultat :
- connectivité Internet fonctionnelle

---

#### Test DNS

```bash
ping google.com
```

Résultat :
- résolution DNS fonctionnelle

---

#### Résolution DNS détaillée

```bash
nslookup google.com
```

Résultat :
- résolution correcte de google.com en adresse IPv4 et IPv6

---

#### Traceroute

```bash
traceroute google.com
```

Résultat :
- premier saut identifié :
  `192.168.126.2` (VMware NAT)

Observation :
- les sauts suivants ne répondent pas probablement à cause du filtrage ICMP/firewall
---

### Services et ports Linux observés

#### SSH
- Port : 22
- Service d’administration distante Linux

#### DNS local Ubuntu
- Port : 53
- Service : `systemd-resolved`

#### VS Code Server
- Port temporaire observé : 43419
- Utilisé pour la communication distante VS Code ↔ Linux

---

### Révision network
- différence entre IP et DNS
- rôle d’une passerelle réseau
- fonctionnement d’un resolver DNS local
- rôle du NAT VMware
- notion de ports réseau
- notion de services Linux
- principe client/serveur
- différence entre port fixe et port éphémère