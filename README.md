<h1>Activité pratique 3</h1>
<h2>Development Web JEE Spring MVC</h2>
<h3>Introduction</h3>
<p>Ce rapport présente le développement d'une application web sécurisée utilisant Spring Boot et Spring Security, centrée sur la gestion des patients. Les étapes incluent la création d'un projet avec les dépendances nécessaires, la mise en place d'entités JPA pour les patients, la configuration de la persistance des données, l'élaboration d'un contrôleur Spring MVC et la création de vues Thymeleaf. La particularité clé du projet est sa souplesse de connexion à H2 ou MySQL. La sécurité est primordiale, avec l'intégration de Spring Security via trois stratégies d'authentification : InMemoryAuthentication, JdbcAuthentication et UserDetailsService. L'objectif final est de fournir une application web fonctionnelle, adaptable et sécurisée, en exploitant pleinement les fonctionnalités de Spring Boot et Spring Security.</p>
<h3>Objectifs</h3>
<p>Créer une application web JEE qui permet de gérer des patients</p>
<h3>Enoncé :</h3>
<ol>
<li>Créer un projet spring boot avec les dépendances Web, Spring Data JPA, H2, Lombock, Thymeleaf</li>
<li>Créer l'entité JPA Patient</li>
<li>Créer l'interface PatientRepository basée sur Spring Data</li>
<li>Configurer l'application (application properties)</li>
<li>Créer le contrôleur Spring MVC</li>
</ol>
<h3>Procédure effectuée :</h3>
<ol>
<li>Créer un projet spring boot avec les dépendances Web, Spring Data JPA, H2,
Lombock, Thymeleaf</li>
<img src="./captures/screenshot.png" alt="dependencies" style="width: 500px">
<li>Créer l'entité JPA Patient</li>
<img src="./captures/patient.png" alt="patient entity" style="width: 500px">
<li>Créer l'interface PatientRepository basée sur Spring Data</li>
<img src="./captures/patientRepository.png" alt="patient repository" style="width: 500px">
<li>Configurer l'application (application properties)</li>
<img src="./captures/applicationProperties.png" alt="application properties" style="width: 500px">
<li>Créer le contrôleur Spring MVC</li>
<p>Partie qui gère l'affichage des patients avec la pagination</p>
<img src="./captures/controller.png" alt="controller" style="width: 500px">
<p>Partie qui concerne le bouton delete pour effacer un patient</p>
<img src="./captures/deletePatient.png" alt="delete" style="width: 500px">
<img src="./captures/controller2.png">
<li>Créer les vues basées sur Thymeleaf</li>
<img src="./captures/vue.png" style="width: 500px">
</ol>

<h2>La validation des formulaires : </h2>
<h3>La dépendence utilisée :</h3>
<img src="./captures/dependence_validation.png" />
<p>Cette dépendance fournit des fonctionnalités de validation en intégrant la validation de Bean 
de Java (JSR-380) dans Spring Boot. On peut maintenant créer des classes de modèle pour vos formulaires 
et utiliser des annotations de validation pour définir les contraintes sur les champs de ces classes.</p>
<p>Maintenant, on peut utiliser les annotations pour valider les champs :</p>
<img src="captures/entity_validated.png">
<h2>La page template Layout : </h2>
<img src="captures/template_layout.png">
<p>Container content : </p>
<img src="captures/layout_fragment.png">
<p>Le principe du template layout dans Thymeleaf est d'avoir un modèle de mise en page (layout)
qui définit la structure générale de nos pages web, avec des emplacements réservés pour le
contenu spécifique de chaque page. Cela permet de créer un modèle de conception cohérent pour notre 
site web tout en réutilisant certaines parties communes.</p>
<h2>Spring Security</h2>
<p>Spring Security est un framework puissant et hautement personnalisable qui fournit des 
fonctionnalités de sécurité pour les applications Java. Son rôle est de gérer l'authentification,
l'autorisation et la protection contre les attaques pour les applications basées sur Spring.</p>
<h3>Enoncé : </h3>
<p>Sécuriser l'application en intégrant un système d'authentification basé sur Spring Security avec 
les trois stratégies : InMemoryAuthentification, JdbcAuthentification et UserSetailsService.</p>
<h3>Les dépendances : </h3>
<img src="captures/security_dependencies.png"></img>
<ol>
<li><h3>InMemoryAuthentification</h3></li>
<p>La stratégie InMemoryAuthentification permet de définir les utilisateurs et leurs 
information d'authentification directement en mémoire, sans nécessiter de stockage externe comme 
une base de données.</p>
<p>Dans la classe SecurityConfig : </p>
<img src="captures/InMemoryAuthentification.png">
<li><h3>JdbcAuthentification</h3></li>
<p>L'authentification JDBC permet de gérer l'authentification en utilisant une base de donnée relationnelle
pour stocker les informations sur les utilisateurs, y compris leurs identifiants et leurs rôles.
Cela offre une solution plus robuste et extensible que l'authentification en mémoire pour des 
applications réelles.</p>
<p>application.properties : </p>
<img src="captures/jdbc_app_properties.png">
<p>Avec cette configuration, Spring Boot va chercher un script Sql et va l"executer.
Dans le script schema.sql qui se trouve dans ressources, On a mis les tables des utilisateurs
et les roles qui seront ajoutés à la base de données.</p>
<p>Dans la classe SecurityConfig :</p>
<img src="captures/jdbcUserDetailsManager.png">
<p>Dans la classe HopitalWebApplication :</p>
<img src="captures/jdbc_CLR.png"/>
<li><h3>UserDetailsService</h3></li>
<p>L'utilisation de UserDetailsService offre une grande flexibilité car elle permet de charger les détails de l'utilisateur à partir de différentes sources de données tout en intégrant cette logique au processus d'authentification de Spring Security. Cela permet une gestion efficace et personnalisée des utilisateurs dans votre application.</p>
<p>En général, on commence par créer une interface AccountService qui va contenir les méthoders pour ajouter les utilisateurs et leur roles et même affecter un rôle à un utilisateur ou bien le supprimer.</p>
<img src="captures/accoutServiceInterface.png">
<p>Puis on implémente cette interface pour ajouter notre Code</p>
<img src="captures/AccountServiceImpl.png">
<p>UserDetailsService est une interface fondamentale de Spring Security utilisée pour charger les détails de l'utilisateur lors de l'authentification. Son rôle principal est de récupérer les informations spécifiques d'un utilisateur (telles que les informations d'identification, les rôles, les autorisations) à partir d'une source de données, souvent une base de données ou tout autre système de stockage.</p>
<img src="captures/userDetailsService.png" />
<p>Maintenant, pour ajouter des utilisateurs dans notre base de données, on doit executer cette méthode :</p>
<img src="captures/accountServiceUsage.png" />
</ol>
<h3>Conclusion</h3>
<p>Cette application Spring Boot avec Spring Security offre une gestion robuste des patients tout en mettant l'accent sur la sécurité. En intégrant des fonctionnalités flexibles, telles que la pagination et la recherche, et en personnalisant l'authentification avec InMemoryAuthentication, JdbcAuthentication et UserDetailsService, l'application allie efficacité, adaptabilité et sécurité.</p>