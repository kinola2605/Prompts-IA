J'ai besoin de générer une feuille de style XSLT 2.0 complète qui va transformer 
l'export XML (dont la structure est détaillée ci-dessous) en une documentation 
HTML 5 unique, interactive et visuellement attractive.

Style souhaité : Dashboard ou Documentation Technique avec CSS intégré.

Structure du XML source :
- Namespace : http://dps.docapost.com/ged/service/export
- Racine : <okoro> avec attribut okoro_version
- Contient <data> avec plusieurs collections :
  * <activitiesXmlb> : Activités avec hiérarchie (parentID)
  * <organisationsXmlb> : Organisations avec hiérarchie (parentID)
  * <groupesXmlb> : Groupes de sécurité
  * <profilesXmlb> : Profils de sécurité
  * <perimetersXmlb> : Périmètres (organisation + activité + profondeur)
  * <authorizationsXmlb> : Autorisations (profile + perimeter + groupe optionnel)
  * <metadatafieldsectionsXmlb> : Sections de métadonnées
  * <metadatafielddefinitionsXmlb> : Définitions de champs (90+ champs)
  * <recordtypesXmlb> : Types de records avec schémas de métadonnées
  * <casefiletypesXmlb> : Types de dossiers
  * <lifecyclerulesXmlb> : Règles de cycle de vie

Exigences :
1. CSS intégré moderne avec navigation sticky sur le côté gauche
2. Sections claires : Vue d'ensemble, Organisations, Activités, Types de Records, 
   Types de Dossiers, Règles de Cycle de Vie, Modèle de Sécurité, Dictionnaire de Données
3. Afficher les hiérarchies sous forme d'arbres visuels (organisations et activités)
4. Cards visuelles pour les types de records/dossiers avec leurs métadonnées
5. Tableaux pour les définitions de métadonnées avec toutes les propriétés
6. Modèle de sécurité : profils → autorisations → périmètres → groupes
7. Couleurs corporates : bleu (#3498db), gris foncé (#2c3e50), fond clair (#f5f7fa)
8. Design responsive avec hover effects
9. Utiliser xsl:key pour optimiser les performances (recherches hiérarchiques, 
   liaisons métadonnées)
10. Gérer les éléments optionnels (description, groupe dans autorisation, etc.)

La documentation doit être complète, professionnelle et facilement navigable.
