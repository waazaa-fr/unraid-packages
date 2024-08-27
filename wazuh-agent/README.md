**wazuh-agent pour unRAID**

Vous trouverez ici le nécessaire pour faire tourner l'agent wazuh pour unRAID.

Lien du projet wazuh: https://wazuh.com

**Installation de l'agent unRAID**

L'installation va se faire grâce à 2 paquets que j'ai créé.
- Un paquet qui va installer l'agent dans /mnt/user/appdata/wazuh-agent-unraid
- Un paquet qui sera chargé d'ajouter le user et group wazuh et de démarrer les services

**Exemple d'installation pour la version v4.7.4**

Le paquet d'installation: wazuh-agent-4.7.4-Unraid.txz
```bash
# Récupération du paquet
wget https://git.waazaa.fr/waazaa/unraid-packages/raw/branch/main/wazuh-agent/v4.7.4/wazuh-agent-4.7.4-Unraid.txz
# Installation du paquet
installpkg wazuh-agent-4.7.4-Unraid.txz
```

Ceci va donc l'installer dans /mnt/user/appdata/wazuh-agent-unraid/
Allez modifier l'ip du serveur :
```bash
nano /mnt/user/appdata/wazuh-agent-unraid/etc/ossec.conf
```

Modifiez l'ip du serveur wazuh en remplacant 192.168.1.29:
```xml
<ossec_config>
  <client>
    <server>
      <address>192.168.1.29</address>
```

Installation des dépendances la première fois que vous utilisez l'agent.

Les fois suivantes au boot cela se fera tout seul:
```bash
# Installation des dépendances
installpkg /boot/extra/wazuh-00*
```

Si tout se passe bien votre agent se connectera à votre serveur wazuh.
