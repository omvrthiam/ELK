#  Installation et configuration de la stack ELK avec Ansible

Ce dépôt automatise l'installation de la stack ELK (Elasticsearch, Logstash, Kibana) sur une VM Ubuntu Server à l'aide d'Ansible.

##  Prérequis

- VirtualBox
- Ubuntu Server 22.04 LTS (VM)
- Ansible installé sur votre machine hôte
- Accès SSH configuré vers la VM cible
- RAM : 4 Go min (8 Go recommandé)
- CPU : 2 cœurs min
- Réseau : NAT + Host-Only


##  Lancer le déploiement

```bash
ansible-playbook -i inventory playbook.yml
```

##  Exemple de Playbook

`playbook.yml` :
```yaml
- name: Install ELK Stack
  hosts: elk
  become: yes
  roles:
    - elasticsearch
    - kibana
    - logstash
```

##  Description des rôles

Chaque rôle contient :
- `tasks/` : tâches principales (installation, config)
- `defaults/` : variables par défaut
- `vars/` : variables spécifiques
- `handlers/` : redémarrage des services
- `templates/` : fichiers de configuration si nécessaire

---

##  Accès Kibana

Une fois le déploiement terminé :

[http://<IP_VM>:5601](http://<IP_VM>:5601)

---

##  Étapes suivantes

- [ ] Ajouter Filebeat pour l'ingestion des logs
- [ ] Créer des dashboards dans Kibana
- [ ] Ajouter des pipelines Logstash

##  Licence

MIT

