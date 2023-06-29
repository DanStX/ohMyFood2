## Le Pattern 7-1

J’utilise habituellement ce que j’appelle le pattern 7-1 : 

    - 7 dossiers, 1 fichier. 

Tous vos partiels regroupés dans 7 dossiers différents et un fichier simple à la racine (généralement appelé main.scss) qui les importe tous pour les compiler dans une feuille de style CSS.

   > -  abstracts/
   > -  base/
   > -  components/
   > -  layout/
   > -  pages/
   > -  themes/
   > -  vendors/
  
Et bien sûr :

  #### main.scss

Si vous souhaitez utiliser le pattern 7-1, il y a déjà un boilerplate sur GitHub.
 Il contient tout ce dont vous avez besoin pour démarrer avec cette architecture.


 Idéalement, nous pouvons proposer quelque chose comme ceci :

## scss/

  abstracts/

    _variables.scss    # Scss Variables
    _functions.scss    # Scss Functions
    _mixins.scss       # Scss Mixins
    _placeholders.scss # Scss Placeholders
    …                     # Etc.


  base/

    _reset.scss        # Reset/normalize
    _typography.scss   # Typography rules
    …                     # Etc.


  components/

    _buttons.scss      # Buttons
    _carousel.scss     # Carousel
    _cover.scss        # Cover
    _dropdown.scss     # Dropdown
    …                     # Etc.

  layout/

    _navigation.scss   # Navigation
    _grid.scss         # Grid system
    _header.scss       # Header
    _footer.scss       # Footer
    _sidebar.scss      # Sidebar
    _forms.scss        # Forms
    …                     # Etc.
 

  pages/

    _home.scss         # Home specific styles
    _contact.scss      # Contact specific styles
    …                     # Etc.
 

  themes/

    _theme.scss        # Default theme
    _admin.scss        # Admin theme
    …                     # Etc.
 

 ### vendors/

    _bootstrap.scss    # Bootstrap
    _jquery-ui.scss    # jQuery UI
    …                     # Etc.



 #### le main.scss              # Main Scss file


Les fichiers suivent les conventions de nommage décrites précédemment : minuscules et utilisation du trait d’union.

FICHIER PRINCIPAL
Le fichier principal (généralement appelé main.scss) devrait être le seul fichier de toute la base à ne pas commencer par un underscore (_). Ce fichier ne devrait rien contenir d’autre que les @import et des commentaires.

Les fichiers doivent être importés en fonction du dossier dans lequel ils sont rangés, l’un après l’autre dans l’ordre suivant :

  > -  abstracts/
  > -  vendors/
  > -  base/
  > -  layout/
  > -  components/
  > -  pages/
  > -  themes/

Afin d’assurer une bonne lisibilité, le fichier principal devrait respecter ces recommandations :

un fichier par @import ;
un @import par ligne ;
pas de saut de ligne entre 2 imports provenant du même dossier ;
un saut de ligne après le dernier import d’un dossier ;
les extensions fichiers et les underscores initiaux doivent être omis.

Il existe une autre façon d’importer les partiels, que je considère également valable. D’un côté, elle rend le fichier plus lisible. D’un autre côté, elle rend la mise à jour moins aisée. En tout cas, c’est à vous de décider, ce n’est pas très important. Dans cette façon de faire, le fichier principal doit respecter ces recommandations :

un @import par dossier ;
retour à la ligne après @import ;
chaque fichier sur sa propre ligne ;
un saut de ligne après le dernier import d’un dossier ;
les extensions fichiers et les underscores initiaux doivent être omis.
        @import
        'abstracts/variables',
        'abstracts/functions',
        'abstracts/mixins',
        'abstracts/placeholders';

        @import
        'vendors/bootstrap',
        'vendors/jquery-ui';

        @import
        'base/reset',
        'base/typography';

        @import
        'layout/navigation',
        'layout/grid',
        'layout/header',
        'layout/footer',
        'layout/sidebar',
        'layout/forms';

        @import
        'components/buttons',
        'components/carousel',
        'components/cover',
        'components/dropdown';

        @import
        'pages/home',
        'pages/contact';

        @import
        'themes/theme',
        'themes/admin';

Pour éviter d’avoir à importer chaque fichier manuellement, il y a une extension de Sass Ruby appelée sass-globbing, qui permet d’utiliser les patterns glob dans Sass @import tels que @import "components/*".

Ceci dit, je ne la recommande pas car elle importe les fichiers par ordre alphabétique ce qui n’est pas souhaitable en général, surtout s’agissant d’un langage dans lequel l’ordre des sources est essentiel.

