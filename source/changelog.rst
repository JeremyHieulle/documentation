.. _changelog:

=========
Changelog
=========

***********
0.64 -> 0.7
***********

.. warning::

   Galette 0.7 est encore en cours de développement, les informations de ce changelog peuvent être amenées à évoluer.

.. _ajouts:

Ajouts et modifications
=======================

* Refonte complète de l'interface,
* Validation XHTML 1 et CSS 2,
* Nouvelle gestion de l'historique,
* Gestion de mailings (avec historique),
* Pages publiques (liste des membres et trombinoscope),
* Système de plugins (voir :ref:`la liste des plugins disponibles <plugins>`),
* Export au format CSV des tables de la base courante et/ou export de requêtes paramétrées (https://mail.gna.org/public/galette-devel/2009-02/msg00006.html),
* Paramétrage des champs obligatoires pour l'enregistrement et la modification d'adhérents,
* Gestion multilingue des sujets et messages des mails envoyés automatiquement par Galette (inscription, perte de mot de passe, ...),
* Gestion des statuts utilisateur,
* Gestion des types de contributions,
* Intégration de JQuery UI pour améliorer l'interface (menus, onglets dans les préférences, date picker, ...),
* Impression de cartes de membres

.. _suppressions:

Suppressions
============

* Suppression du support IE6,
* Suppression de l'espagnol (qui n'est plus maintenu :'( )
* Suppression de AdoDB (remplacé par PEAR MDB2) (*en cours*)

.. _souscapot:

Sous le capot...
================

Quelques modifications, d'ordre un peu plus technique ont également été apportées :

* Compatible PHP 5.3 et supérieurs,
* Utilisation de bibliothèques PEAR :

  * MDB2 : gestion des bases de données (en lieu et place de AdoDB),
  * Log : système de log

* Mise en place de relations dans la base de données pour assurer l'intégrité référentielle.

.. _plugins:

Plugins
=======

Quelques plugins sont dores et déjà disponibles pour Galette !

* **Auto** : Gestion d'associations automobiles (gestion des véhicules et de l'historique des modifications).
* **Paypal** : Gestion des différents montants de cotisation, formulaire de paiement ; à venir : ajout de la contribution dans la base Galette lorsque le paiement est validé par Paypal.
* **Fiche Adhérent** : Génération au format PDF d'une fiche adhérent avec les principales informations pré-remplies.
* **TinyMCE** : Éditeur HTML WYSIWYG complet en remplacement du plus simple éditeur fourni par défaut.
* **Sport** (*à venir*) : Intégration des fonctionnalités supplémentaires existantes dans galette-sport

**************
0.63.3 -> 0.64
**************

* Handle 'stripos' missing function to keep 0.63.x php4 compliant
* Upgrade Adodb to 4992
* Upgrade to Smarty 2.6.22, and replace old hack for translations with more elegant plugin
* Replace phppdflib with tcpdf
* Symlink to adodb has been removed, we now use a php file defining the versions for the libraries
* Improved pagination: only 20 pages will appear now, instead of all pages
* Remove spanish language which has not been maintaned for ages
* Use UTF-8 for translation files
* Fix a bug calculating end membership date when using begining date for membership in the preferences
* Remove not functionnal and not used "public" pages
* Remove unused files
* Handle 'mb_strtoupper' to avoid error on labels generation when mb extension is not present
* Move config file from includes to config directory. Wrtie access on includes directory will no longer be required at install
* Only super-admin can change its login/password now. Standard admins can no longer do that

****************
0.63.2 -> 0.63.3
****************

* fix a security flaw that allowed attacker to send arbitrary PHP files on some servers
* when sendind invalid member form, line dynamic fields were repeated (bug #10187)
* some encoding issues has been noticed on UFT-8 MySQL servers. Connection is now forced to LATIN1 (thanks to Cédric)
* unbreakable spaces appears on non html email (thanks to Cédric)
* using XML characters in mailing subjects causes XML analysis errors on preview (bug #14571)
* needless data were stored into logs (and not at the right place) sending mailings (bug #14569)
* XML analysis errors where thrown on logs page when a member card contains reserved characters (bug #14561)
* html tags in mailing were not showed while previewing a mailing under Firefox (bug #14465)

****************
0.63.1 -> 0.63.2
****************

* membership's deadline was incorrect for a fiscal year (bug #13010)
* donations didn't appear in the right color in the table (bug #13009)
* history entries when adding or editing a contribution did not contains member's login - as when adding/editing a member (bug #13011)
* on windows, some characters were incorrectly interpreted - ¿\n¿ for example (bug #14162)
* when saving a picture (PNG format), alpha channel was not saved, causing image to get a default background color (bug #14327)
* restrictions showing pictures (since 0.63.1) prevents custom logo to display correctly (bug #14442)
* when editing member's language, current session was also translated (bug #14443)
* some characters - like simple quotes - were badly encoded mailings subjects (bug #14449)
* mail sending were always active, even if disabled in preferences (bug #14450)

**************
0.63 -> 0.63.1
**************

* some preferences were not updated at install time
* on some web hosting services, exif functions are not available. In this case, we use GD (bug #12836)
* XHTML was sometimes not well formed, due to PHP sessions (bug #13071)
* fix PHP notices in the logs (patch #1133)
* remove of posix functions which are deprecated in PHP 5.3
* add of a .htaccess file to prevent read of uploaded photos from the web

************
0.62 -> 0.63
************

* Project leader change :-)
* Added transactions managment
* Added dynamic field managment, to add some extra fields; also added the ability to translate such fields labels
* Members can now self-subscribe
* Use of Smarty template engine for pages generation. This causes complete xhtml compliant rewrite of html pages
* Upgrade from ADODB 4.7.1 to 4.9.2
* Use of gettext possibilities for translations
* Added spanish translations (all translations are not done yet)
* Added the possibility to upload a custom logo
* Fixes numerous bugs

***************
0.62a -> 0.62.2
***************

* change adodb framework due to security alert :
  http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-0410
* use x.y.z naming convention (0.62a == 0.62.1)

*************
0.62 -> 0.62a
*************

* correct bug #590 : date before 1970 [Frédéric Jacquot]
* Typos fixed [Roland Telle]
* replace logo by new one [Frédéric Jacquot]
* add an empty config.inc.php [Loïs Taulelle]

************
0.61 -> 0.62
************

* More documentation
* Typos fixed
* Recoded the html_entity_decode() function to preserve compatibility with pre-4.3 PHP
* Defined a maxsize for the text fields (preferences)
* First version of the Upgrade documentation using a Linux shell (in French)
* Font size for table headers defined
* "Update complete" string translated
* Errors on DROP and RENAME operations can now be safely be ignored
* Structure of the 'preferences' table enhanced
* Font size defined for form labels
* Bugfix concerning a call to imagegif when the function wasn't available (reported by Vincent Bossuet)
* Fixed a bug reported by Lois Taulelle. Membership ending date wasn't updated when removing the "Freed of dues" attribute
* Added the possibility to be visible or not in the members list (if you wan't to list members outside from Galette). Courtesy of Stephane Sales
* Removed many PHP warnings (Galette should be running fine when error_reporting = E_ALL)
* The log can now be sorted

************
O.60 -> 0.61
************

* Bugfix in member edition form (admin)
* Merged ajouter_adherent.php and gestion_contributions.php (member edition)
* Table prefixes are now allowed
* Removed all eval() functions (potentially dangerous)
* Picture resizing if GD is available
* HTML equivalents in members' names were badly displayed
* Go back to the member's contributions after adding one
* "1 days left" was not correct ;)
* Date filter added in contribution listing
* Correction of a few spelling mistake
* Navigation links when on a member's contributions list added
* Clicking on a member's name in the contributions list shows his
  contributions intead of his profile
* Lost password recovery added
* Removed the Galette acronym meaning
* Header corrections
* Better language file detection
* Bugfix in thumbnail display
* DROP permission wasn't checked during install process
* English translation

************
O.60 -> 0.61
************

* Correction du formulaire d'édition d'adhérent (admin)
* Fusion des fichiers ajouter_adherent.php et gestion_contributions.php
  (edition de membre)
* Les prefixes de tables sont maintenant autorisés
* Réduction des photos si GD est disponible
* Les équivalents HTML dans les noms d'adhérents étaient parfois
  mal affichés
* Retour aux contributions d'un membre après l'ajout d'un contribution
* Filtre sur les dates dans le listing des cotisations
* Correction de fautes d'orthographe
* Liens de navigation sur la fiche de cotisations d'un membre
* Cliquer sur le nom d'un adhérent dans la liste des cotisations
  permet d'obtenir ses contributions au lieu de son profil
* Lien "mot de passe perdu"
* Masquage de la signification de l'acronyme "Galette"
* Corrections dans les en-têtes
* Meilleure détection du fichier de langue
* Correction de bug dans l'affichage des vignettes
* Le permission DROP n'était pas vérifié durant l'installation
* Traduction en anglais

