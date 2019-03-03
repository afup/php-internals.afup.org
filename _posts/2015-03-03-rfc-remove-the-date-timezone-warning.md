---
id: 202
title: 'RFC: Remove the date.timezone warning'
date: 2015-03-03T08:30:07+00:00
author: Guillaume
layout: post
guid: http://php-internals.afup.org/?p=202
permalink: /2015/03/03/rfc-remove-the-date-timezone-warning/
categories:
  - Non classé
---
La [RFC Remove the date.timezone warning](https://wiki.php.net/rfc/date.timezone_warning_removal) partait du constat qu&rsquo;il existe à l&rsquo;heure actuelle une directive de configuration qui nécessite d&rsquo;être définie afin de pouvoir lancer PHP sans erreur : `date.timezone`.

Lorsque cette directive n&rsquo;est pas configurée, une erreur de type `warning` est générée par PHP, même si le moteur lui attribue une valeur par défaut (_UTC_).

Le but de cette RFC était de supprimer cette erreur, afin de pouvoir fournir à PHP une installation paramétrée complète par défaut. En effet, il apparaît que de nombreuses autres directives, bien plus sensibles notamment en terme de sécurité, sont d&rsquo;ores et déjà configurées par défaut.

Il nous semblait que l&rsquo;absence de configuration de cette directive devait à minima générer une erreur stricte, car elle impacte des fonctions de date très usitées (telle `date()`), d&rsquo;autant que la zone par défaut est aujourd&rsquo;hui définie de manière arbitraire. Nous avons donc répondu en ce sens sur [internals@](http://news.php.net/php.internals/83631).

Néanmoins, avec 32 votes pour et 11 contre, cette RFC est passée et l&rsquo;avertissement correspondant ne sera donc plus levé à partir de PHP 7.