The attached example will mount scripts into a local directory within the Kubernetes job at the path /data/configs. In this case, it's important to include shell instructions in the job's entrypoint (containers.command section) to copy the contents of this directory into the NiFi volume designated for scripts.

1. Architecture & Déploiement

    Mode d’installation

        Quels sont les prérequis système (OS, CPU, RAM, stockage) pour déployer Fivetran Transformations (dbt) on‑premise ?

        Le déploiement on‑premise se fait‑il via conteneurs (Docker/Kubernetes) ou via packages natifs ?

        Existe‑t‑il une image Docker officielle et comment la maintenir à jour en interne ?

    Réseau & Connectivité

        Comment gère‑t‑on les accès réseau pour que Fivetran puisse communiquer avec nos entrepôts et notre Git interne sans sortir sur Internet ?

        Peut‑on restreindre les sorties sortantes (egress) et n’autoriser que certains endpoints internes (whitelisting) ?

        Comment s’intègre l’agent on‑premise au sein d’un réseau cloisonné (DMZ, VPC privé) ?

    Scalabilité & Performances

        Quel est le maximum de jobs dbt concurrents supportés dans la version on‑premise ?

        Comment se passe l’allocation dynamique de ressources (CPU/mémoire) pour les exécutions de modèles volumineux ?

        Peut‑on configurer des pools de workers ou du scaling automatique (autoscaling) ?

2. Sécurité & Conformité

    Authentification & Autorisations

        Supporte‑t‑on l’authentification SSO/SSO SAML ou OpenID Connect contre notre annuaire interne (LDAP/AD) ?

        Comment sont gérés les rôles et permissions (rôles admin, opérateur, lecture seule) dans l’interface on‑premise ?

    Chiffrement & Gestion des secrets

        Les identifiants (DB, Git, API) sont‑ils stockés chiffrés au repos ?

        Peut‑on intégrer un coffre-fort de secrets externe (HashiCorp Vault, AWS Secrets Manager on‑prem) pour la rotation automatique des credentials ?

        Quel niveau de chiffrement TLS est supporté pour les communications inter‑composants ?

    Conformité & Audit

        Fournissez‑vous des logs d’audit détaillés (qui a lancé quel job, quand, avec quels paramètres) ?

        Ces logs peuvent‑ils être exportés vers nos outils d’ELK/SIEM (Splunk, Datadog, etc.) ?

        Votre solution est‑elle certifiée ISO 27001, SOC 2 Type II, GDPR, HIPAA, PCI-DSS… pour un usage on‑premise ?

3. Fonctionnalités dbt

    Orchestration & Triggering

        Peut‑on déclencher un job dbt on‑prem dès qu’un connecteur Fivetran a fini d’ingérer les données, sans passer par la console cloud ?

        Existe‑t‑il une API REST ou CLI locale pour planifier/lancer/annuler des jobs dbt ?

    Versioning & CI/CD

        Comment s’intègre l’offre on‑prem aux pipelines CI/CD (GitLab CI, Jenkins, Azure DevOps) pour les tests et déploiements automatisés ?

        Supportez‑vous les déploiements multi‑environnements (dev/staging/prod) avec isolation des schémas et des variables ?

    Observabilité & Debug

        Quels outils embarqués ou intégrations (Prometheus, Grafana) proposez‑vous pour surveiller l’état et la durée des jobs dbt ?

        Y a‑t‑il des métriques exposées (temps par modèle, taux d’échec, volumétrie) ?

    Lineage & Documentation

        L’UI on‑prem affiche‑t‑elle le graphe de dépendance complet (lineage) entre les tables modélisées ?

        Peut‑on générer automatiquement la documentation (dbt docs) et l’héberger localement ?

    Tests & Qualité

        Comment sont exécutés les tests dbt test (schéma, singularité, relations) ?

        Peut‑on configurer des seuils de qualité (eg: % de tests acceptés) et bloquer un déploiement si ces seuils ne sont pas atteints ?

4. Exploitation & Maintenance

    Mises à jour & Patching

        Quel est le processus de mise à jour du produit on‑prem ?

        Y a‑t‑il un mécanisme de rolling upgrade pour minimiser les temps d’indisponibilité ?

    Sauvegarde & Reprise d’activité

        Quel état faut‑il sauvegarder (config, métadonnées, logs) pour pouvoir restaurer la plateforme ?

        Avez‑vous un guide DRP (Disaster Recovery Plan) spécifique pour la solution on‑premise ?

    Support & SLA

        Quel SLA garantissez‑vous pour la plateforme on‑prem (MTTR, disponibilité) ?

        Proposez‑vous une hotline 24×7 ou un support dédié pour les installations on‑prem ?

        Quel est votre process d’escalade et votre délai de première réponse ?

5. Roadmap & Évolutivité

    Roadmap fonctionnelle

        Les nouvelles fonctionnalités dbt Cloud (exécution parallèle, ephemeral environments, compute cost analytics…) seront-elles portées on‑prem ?

        Sur quel rythme de release se base l’offre on‑prem par rapport à la version cloud ?

    Interopérabilité & Extensibilité

        Peut‑on ajouter des plugins/custom adapters (ex: macros maison, packages internes) sans compromettre la compatibilité lors des futures mises à jour ?

        Existe‑t‑il un SDK ou un framework d’extensions pour enrichir les hooks et les macros dbt ?

6. Coûts & Licensing

    Modèle de licence

        Comment est‑tarifée l’offre ? Licence par CPU/RAM, par utilisateur, par connecteur, ou au forfait ?

        Y a‑t‑il des coûts additionnels pour le module Transformations (dbt) on‑prem par rapport à la version cloud ?

    Usage & Facturation

        Donnez-vous la possibilité de mesurer la consommation réelle (heures CPU, jobs exécutés) pour un pilotage fin des coûts ?

        Comment gérez‑vous la montée en charge (ajout de nœuds) et la facturation associée ?

Bonus – Questions stratégiques :

    Avez‑vous des références clients (secteur industriel) qui ont déployé Fivetran + dbt on‑prem ?

    Proposez‑vous des services d’accompagnement (POC, ateliers, tuning de performance) pour accélérer le démarrage ?

    Quelle est votre vision long terme de l’intégration dbt au sein de Fivetran pour les environnements entièrement isolés ?

Proposez‑vous, dans votre offre on‑premise, un éditeur intégré pour créer et modifier directement les modèles dbt (avec fonctionnalités comme l’auto‑complétion SQL, la visualisation du lineage et le contrôle de versions) depuis l’interface Fivetran ?






Proposez‑vous, dans votre offre on‑premise, un éditeur intégré pour créer et modifier directement les modèles dbt (avec fonctionnalités comme l’auto‑complétion SQL, la visualisation du lineage et le contrôle de versions) depuis l’interface Fivetran ?




 Dans un déploiement on‑premise, où vos services exécutent-ils concrètement les jobs dbt (sur nos serveurs, dans des conteneurs isolés ou sur votre infrastructure), et quelles mesures de sécurité (chiffrement des données en transit et au repos, contrôle d’accès, journalisation et audit, segmentation réseau, etc.) garantissent qu’aucune donnée sensible ne pourra être exfiltrée ou fuitée ?
