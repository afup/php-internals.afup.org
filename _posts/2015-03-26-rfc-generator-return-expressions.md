---
id: 249
title: 'RFC: Generator Return Expressions'
date: 2015-03-26T08:35:45+00:00
author: Pascal MARTIN
layout: post
guid: http://php-internals.afup.org/?p=249
permalink: /2015/03/26/rfc-generator-return-expressions/
categories:
  - Non classé
---
Voici une première RFC qui visait à élargir le périmètre fonctionnel des générateurs ajoutés avec PHP 5.5 :

  * Nom : Generator Return Expressions
  * URL : <https://wiki.php.net/rfc/generator-return-expressions>
  * Version cible : PHP 7

Note : cette proposition conditionne la [RFC Generator Delegation](https://wiki.php.net/rfc/generator-delegation), qui a été rédigée quelques jours plus tard.

Cette RFC proposait de permettre aux fonctions générateur l&rsquo;utilisation de `return` avec une valeur (ce qui provoque aujourd&rsquo;hui une Fatal Error). Une méthode `Generator::getReturn()` serait alors ajoutée pour permettre l&rsquo;obtention de cette valeur de retour. Elle ne pourrait bien sûr être appelée qu&rsquo;une fois la fonction génératrice terminée.

En somme, cela permettrait d&rsquo;avoir une vraie valeur de retour explicite pour les générateurs, plutôt que de considérer que la dernière valeur _yieldée_ joue ce rôle.

Les votes ont été ouvert le 09 mars pour être clôturés le 16 Mars 2015. Nous avons [exprimé un avis positif sur `internals@`](http://news.php.net/php.internals/84998).  
Et cette RFC a été acceptée à l&rsquo;unanimité (33 votes &laquo;&nbsp;pour&nbsp;&raquo; et 0 vote &laquo;&nbsp;contre&nbsp;&raquo;).
