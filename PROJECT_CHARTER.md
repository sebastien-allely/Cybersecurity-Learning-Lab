# PROJECT CHARTER

## Vision

Cybersecurity Learning Lab est un référentiel pédagogique francophone destiné à accompagner les professionnels de l'informatique et les personnes en reconversion dans l'apprentissage de la cybersécurité défensive.

Le projet propose une approche progressive permettant de concevoir, sécuriser, superviser et maintenir une infrastructure cohérente en s'appuyant sur des laboratoires reproductibles, des scripts testés et des référentiels reconnus.

L'objectif n'est pas uniquement de déployer des outils, mais de comprendre leur rôle, de justifier leur mise en œuvre, de mesurer leur efficacité et d'inscrire leur utilisation dans une démarche d'amélioration continue.

---

# Les constats

Ce projet est né de deux constats.

* De nombreuses ressources expliquent comment installer des outils de cybersécurité, mais peu montrent comment construire une architecture cohérente, la superviser, la tester et la maintenir dans le temps.

* Les référentiels reconnus (ANSSI, NIST, OWASP, MITRE ATT&CK...) fournissent des recommandations de qualité, mais leur mise en application concrète dans un laboratoire pédagogique reste souvent dispersée.

Cybersecurity Learning Lab a pour ambition de rapprocher ces deux approches.

---

# Les objectifs

Le projet poursuit plusieurs objectifs :

* développer des compétences techniques et méthodologiques ;
* construire une architecture reproductible ;
* appliquer des mesures de durcissement adaptées ;
* intégrer des solutions de protection complémentaires ;
* superviser les composants déployés ;
* apprendre à mesurer l'efficacité des contre-mesures ;
* documenter les choix techniques et leurs limites ;
* promouvoir une démarche d'amélioration continue.

---

# Public visé

Ce projet s'adresse principalement :

* aux étudiants ;
* aux administrateurs systèmes et réseaux ;
* aux administrateurs systèmes orientés cybersécurité ;
* aux analystes SOC ;
* aux DevSecOps ;
* aux professionnels souhaitant approfondir leurs connaissances en cybersécurité défensive.

Une connaissance de base des systèmes Linux, des réseaux IP et de la virtualisation est recommandée.

---

# Infrastructure de référence

Le laboratoire de référence repose sur l'architecture suivante :

* un cluster Proxmox VE composé de deux nœuds ;
* une machine virtuelle Active Directory ;
* une machine virtuelle GLPI ;
* une machine virtuelle Zabbix.

Cette architecture constitue le socle pédagogique du projet. Elle peut être adaptée en fonction des besoins du lecteur ou de son environnement.

---

# Ce que ce projet est

Cybersecurity Learning Lab est :

* un référentiel pédagogique ;
* un laboratoire reproductible ;
* un support d'apprentissage progressif ;
* un projet orienté cybersécurité défensive ;
* une démonstration de bonnes pratiques d'administration, de supervision et de durcissement.

---

# Ce que ce projet n'est pas

Cybersecurity Learning Lab n'est pas :

* une préparation officielle à une certification ;
* une norme de sécurité ;
* un référentiel réglementaire ;
* un guide consacré aux techniques offensives ;
* un remplacement des recommandations publiées par les organismes de référence.

Les choix techniques présentés dans ce dépôt sont systématiquement contextualisés et peuvent être adaptés selon les besoins de chaque infrastructure.

---

# Principes fondateurs

Chaque module du projet respecte les principes suivants :

* comprendre avant de déployer ;
* justifier chaque choix technique ;
* privilégier l'automatisation lorsque cela est pertinent ;
* superviser les composants déployés ;
* documenter les limites des solutions étudiées ;
* distinguer les recommandations officielles des choix propres au laboratoire ;
* favoriser la reproductibilité et la maintenabilité.

---

# Référentiels

Le projet s'appuie notamment sur :

* ANSSI ;
* NIST ;
* OWASP ;
* MITRE ATT&CK ;
* PDCA (Deming) ;
* le guide SOCLE de Stéphane Robert ;
* les ressources pédagogiques d'IT-Connect (Florian Burnel) ;
* les documentations officielles des logiciels étudiés.

---

# Méthodologie

Le projet applique le principe d'amélioration continue (PDCA).

Chaque composant suit un cycle identique :

1. analyser le besoin ;
2. concevoir l'architecture ;
3. déployer la solution ;
4. vérifier son fonctionnement ;
5. superviser son état ;
6. améliorer la configuration à partir des résultats obtenus.

---

# Organisation documentaire

Chaque module est construit selon une structure homogène comprenant notamment :

* une présentation du composant ;
* les prérequis ;
* les choix d'architecture ;
* l'installation ;
* la configuration ;
* la validation ;
* la supervision ;
* les tests ;
* les limites ;
* un résumé ;
* des exercices ;
* les références utilisées.

---

# Engagements qualité

Chaque contenu publié dans ce dépôt :

* est relu avant publication ;
* est testé dans le laboratoire de référence ;
* cite ses principales sources ;
* distingue les recommandations officielles des choix du projet ;
* documente les limites des solutions proposées ;
* privilégie des procédures reproductibles.

La qualité des contenus est privilégiée à la quantité.

---

# Philosophie de publication

Le projet évolue progressivement.

Un module est publié uniquement lorsqu'il est considéré comme suffisamment mature sur les plans technique, documentaire et pédagogique.

Cette approche permet de garantir la cohérence de l'ensemble du référentiel.

---

# Évolution du projet

Cybersecurity Learning Lab a vocation à évoluer en fonction :

* des retours de la communauté ;
* des évolutions des logiciels étudiés ;
* des mises à jour des référentiels ;
* des nouveaux besoins identifiés.

Toute évolution devra rester cohérente avec les principes définis dans cette charte.

---

# Auteur

**Sébastien Allely**

Ce projet est développé et maintenu dans un objectif de transmission des connaissances, de partage des bonnes pratiques et de développement des compétences en cybersécurité défensive.
