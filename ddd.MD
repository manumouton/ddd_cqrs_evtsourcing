# API’s métier

Domain Driven Design
                    
                    ### Plan

                    1. Domain Driven Design
                    2. Concepts
                    3. Bounded context
                    4. Ubiquitous language
                    5. CQRS & Event sourcing
                    6. Techniques
                   
                          ## Domain Driven Design

                            aka DDD
                       
                        ### Approche de conception logicielle


                        * Métier au centre : modélisation de la problématique
                        * Collaboration avec les experts fonctionnels
                        * Pas influencé par les données
                        * Pas influencé par les contraintes techniques
                        * Langage partagé (*ubiquitous language*) dans un contexte délimité (*bounded context*)
                       
                        ### Avantages

                        * Modèle modulaire, réutilisable et maintenable
                        * Modélisation du core business
                        * Collaboration améliorée entre métier et IT : on parle tous le même langage !
                        * Le code reflète totalement la problématique métier
                      
                            ## Concepts
                        
                            ### Domaine
                            * Quel est notre core business ?
                            * Quelle est notre problématique métier ?
                            * Quels sont les objets qui rentrent en jeu ?
                       
                            ### Modèle
                            * Comment modéliser mon **Domaine** ?
                            * Quels sont les concepts en présence ?
                        
                            ### Bounded context
                            * Ou placer la limite autour de mon **Modèle** ?
                            * Y-a-t'il des interactions avec d'autres contextes ?
                       
                            ### Ubiquitous language
                            * Que signifient les différents composants de mon **Modèle** ?
                            * Tous les membres de l'équipe sont-ils d'accord sur un **langage commun** ?
                            * Ce **langage commun** fait-il sens au niveau métier ?
                       
                            ## Bounded context
                        
                            Un **Bounded context** permet de poser une frontière
                            * Autour du modèle business
                            * Donner sens au langage commun utilisé pour définir le modèle
                            * Envisager les interactions avec d'autres contextes
                        
                            Aggregate - Entity - Value object
                        
                            * Un Aggregate est un cluster d'objets du modèle qui peut être considéré comme un tout (intégrité)
                            * Une Entité est un objet défini par une identité propre (i.e. ID; e.g. personne, contrat, ...)
                            * Un Value Object contient des attributs mais n'a pas d'identité propre (e.g. adresse ?)
                 
                            ## Ubiquitous language
                            
                            ### Problème

                            * Développeurs: langage technique
                            * Métier: terminologie spécifique
                            * Applications: langages de programmation
                            
                            ### Solution

                            * Construction d'un langage commun (glossaire)
                            * Partagé et utilisé entre métier et développeurs
                            * Basé sur le modèle du domaine
                            * Utilisé directement dans les modèles du code!
                       
                            ## CQRS & Event sourcing
                        
                            **Command-Query Responsability segregration (CQRS)** est un pattern architectural qui divise les composants du système en deux parties:
                            * l'écriture (exécution de commandes)
                            * la lecture (exécution de requêtes)
                       
                            Une **commande** permet de demander au système d'accomplir une action ou de changer son état.

                            **Les commandes modélisent le business**
                        
                            Une **requête** permet de récupérer de l'information dans le système, sans en changer son état.

                            Cela permet de reconstruire des vues aux structures différentes selon les besoins finaux.
                       
                            **Event Sourcing** est souvent utilisé de paire avec **CQRS**.

                            Toutes les données du système sont stockées sous forme d'événements, dans un events log.

                            E.g. *personne créée, adresse modifiée, sinistre encodé*
                        
                            ### Les événements
                            * Ne peuvent pas être supprimés ou modifiés
                            * Corrigés avec un événement complémentaire
                            * Reconstruire l'état du modèle à un instant T (timeline)
                        
                            ### Avantages CQRS / Event sourcing
                            * Separation of concerns (READ / WRITE)
                            * Facilité au niveau du reporting
                            * Meilleures performances
                       
                            ## Outils et exemples
                      
                            ### Event storming

                            * Technique de design collaborative (métier et dev)
                            * Donne de l'input à l'**Ubiquitous language**
                            * Focus sur les événements et les processus business
                            * Très visuel: post-it, marqueurs et un très grand mur
                            * Trop d'événements est mieux que pas suffisamment
                       
                            ### Principes (1)

                            **Représenter les événements du processus business**
                              1. Un event par post-it (orange)
                              2. Un event business = Un verbe au passé (e.g. ProductCreated, PersonUpdated, ...)
                              3. Ne pas être trop précis
                              4. Placer les events dans l'ordre chronologique
                              5. Marquer les points bloquants, les events en //, ...
                      
                            ### Principes (2)

                            **Représenter les commandes qui causent chaque event du domaine**
                              1. Une commande par post-it (bleu)
                              2. Une commande = Un verbe infinitif (e.g. CreateProduct, UpdatePerson, ...)
                              3. Placer les commandes à côté des events correspondants
                              4. Rôle de l'initiateur (e.g. Client, Gestionnaire, ...)
                     
                            ### Principes (3)

                            **Associer l'Entité/Aggrégat correspondant à la commande et l'event résultant**
                              1. Un aggrégat par post-it (jaune)
                              2. Possible que le même aggrégat apparaisse plusieurs fois
                              3. Découvertes de nouveaux événements
                              4. Redécoupe des aggrégats
                     
                            ### Principes (4)

                            **Dessiner des frontières et des flèches afin de représenter le flux business**
                              1. Marquer les bounded contexts (cercles continus)
                              2. Indiquer les sous-domaines (cercles pointillés)
                              3. Nommer les différents contextes (post-it)
                              4. Modéliser les relations entre bounded contexts (flèches)
                              5. Bon moyen pour identifier comment certains events arrivent dans le système sans être générés par une commande dans ce bounded context
                       
                            ### Principes (5)

                            ** Identifier les rôles utilisateurs majeurs et les vues nécessaires pour lancer les commandes **
                            1. Quel rôle pour quelle commande ?
                            2. Vision globale des écrans nécessaires
                       
                            ### Concept board

                            [Concept Board | https://conceptboard.com/]
                        
                            ## Ressources
                       
                            * Livres
                              * [Domain-Driven Design: Tackling the Complexity at the Heart of Software](https://amzn.com/0321125215) (The Blue book)
                              * [Implementing Domain-Driven Design](https://vaughnvernon.co/?page_id=168#iddd)
                              * [Domain-Driven Design Distilled](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420)
                              * [Getting started with DDD when Surrounded by Legacy Systems](http://domainlanguage.com/wp-content/uploads/2016/04/GettingStartedWithDDDWhenSurroundedByLegacySystemsV1.pdf)
                       
                            * Web
                              * [Domain Driven Design: des armes pour affronter la complexité](https://blog.octo.com/domain-driven-design-des-armes-pour-affronter-la-complexite/)
                              * [Domain driven design example](https://www.mirkosertic.de/blog/2013/04/domain-driven-design-example/)
                              * [Best Practise - An introduction to Domain-Driven-Design](https://msdn.microsoft.com/en-us/magazine/dd419654.aspx)
                              * [Formation DDD avec Eric Evans - Nicolas Martignole](http://www.touilleur-express.fr/2010/02/15/formation-domain-driven-design-avec-eric-evans-jour-1/)
                    
