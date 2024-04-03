# SentimAnalyzer
Cette application sera capable de déterminer si un texte donné exprime un sentiment positif, négatif, ou neutre. Cette application sera accessible via une API REST ful
L'application sera développer en Python.


# Intruction 

1. Clone le repository : https://github.com/hclem27/SentimAnalyzer.git
2. Déplacer vous dans le dossier 'cd/SentimAnalyzer'
3. pip install 
4. Rendez vous sur l'url : 

# Contribute 

1. Déplacer vous sur la branche dévelop
2. Git Pull la branche dévlop pour avoir la dernière version du code
3. Crée votre branche de développement 'feat/fonctionality'
4. Chaque commit devra respecter lee principe du conventionnal commit :
    "feat(scope): message cours de ce que le commit apporte 

    - Message avec un peu plus de détails

    - issue github associé ou ticket de développement
    " 
5. Quand vous avez finit le développement de la feature et que le code et propre et tester, crée votre merge request sur dévelop

# Workflow de développement 


1) Le besoin
Le besoin est déterminé en interne via un cahier des charges, il est explicite et claire. 
2) Mise à jour
Nous mettrons la livraison une fois par mois en place, permettant aux clients de voir des retours de manière régulière sur l'application et d'apporter des nouveautés chaque mois ainsi que des fix
3) La documentation
La documentation sera mise en ligne via différents supports : Détails des appels API via des commentaires avant d'avoir le code de Controller, mise en place d'un swagger, mise en place de test Guerkin avec QUI / QUAND / COMMENT ? 
4) Qualité de code
La qualité de code sera assurée par Renovatebot et SonarCube 
5) Les tests
On assure les tests avec des règles de non régression vérifiant que les nouveautés ne cassent pas les anciennes features pour l'utilisateur, et ont test l'intégralité des nouvelles features
6) Mise en place de la livraison
Une fois la PR complète (après les 3 approuveur) on créait une nouvelle image via le CAAS 
et on viens la push dans openShift afin d'envoyer ça sur l'environnement "intégration" et commencer à faire les premiers test puis passé à l'environnement préprod et vérifier le chemin utilisateur puis finir par la mise en production (MEP) 


# Organisation des branches github 

- Mise en place d'un blocage sur la branche main, puisque l'on ne développe jamais sur cette branche
- Les développeurs tireront leurs branche de dev à partir de la branche develop, ce qui permet une gestion efficace des fonctionnalités. Chaque fonctionnalité ou tâche peut être développée dans son propre contexte isolé, avec sa propre branche dédiée. Cela facilite le suivi des modifications spécifiques à chaque fonctionnalité et permet des tests unitaires et     d'intégration ciblés.
- Une fois que la feature est terminé et que la branche de feature a atteint un état stable (code propre, refactoring) et qu'elle a été tester correctement (80% de coverage), les développeurs devront creer leur merge request sur la branche develop.
- La Merge Request devra être relu part les 3 approuveur avant de push de la branche feature à la branche develop

# Security 

1. Renovatebot : https://github.com/renovatebot/renovate
Renovatebot est un bot qui tourne une fois par jour et qui fait le tour des packages.logs afin de les mettre à jour, lorsqu'il remarque un package non mis à jour il va crééer une PR en upgradant la version du package. Ce qui limitera le nombre de fails liés aux packages en les maintenant à jour
2. Sonarcube
Sonarcube va lire le code statique et faire des remontées sur les fails / améliorations de code ... 
Il est lié au CI et commente automatiques les PR 


# Deployment 
- pour redis + app
cmd -> docker compose up -d
- pour l'app
cmd -> docker build .

deployer sur kubernetes : 
-> docker build -f Dockerfile -t sentimanalyzer:latest . 
-> docker run -p 5001:5000 sentimanalyzer
-> kubectl apply -f deployment.yaml  

