### Fichier De La Honte
Il existe un concept intéressant, popularisé par Harry Roberts, Dave Rupert et Chris Coyier qui consiste à ranger toutes les déclarations CSS, les hacks et tout ce dont on n’est pas vraiment fier dans un fichier de la honte. Ce fichier, pathétiquement dénommé _shame.scss, est importé après tous les autres fichiers, à la toute fin de la feuille de style.

    /**
    * Réparation du problème de spécificité sur la Nav.
    *
    * Quelqu’un a utilisé un ID dans le code du header (`#header a {}`) qui
    * prend le pas sur les sélecteurs nav (`.site-nav a {}`). Utiliser !important
    * pour l’écraser en attendant de trouver le temps de refactoriser le header.
    */
    .site-nav a {
        color: #BADA55 !important;
    }