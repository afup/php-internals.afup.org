---
id: 14
title: 'RFC: Integer Semantics'
date: 2014-10-06T05:45:18+00:00
author: Pascal MARTIN
layout: post
guid: http://php-internals.afup.org/?p=14
permalink: /2014/10/06/rfc-integer-semantics/
categories:
  - Non classé
---
La RFC [Integer Semantics](https://wiki.php.net/rfc/integer_semantics) visait à améliorer la cohérence de PHP entre plate-formes différentes, en implémentant les changements suivants :

  * `NaN` et `Infinity` seraient toujours égaux à `0` lorsque transtypés en entiers,
  * les décalages bit-à-bit d&rsquo;un nombre négatif de bits seraient interdits,
  * le décalage bit-à-bit vers la gauche d&rsquo;un nombre de bits supérieur à la taille d&rsquo;un entier donnerait toujours `0`,
  * et le décalage bit-à-bit vers la droite d&rsquo;un nombre de bits supérieur à la taille d&rsquo;un entier donnerait toujours `0` ou `-1` (en fonction du signe)

En effet, aujourd&rsquo;hui, une partie de ces manipulations a un comportement qui dépend de l&rsquo;architecture et de la plate-forme sur laquelle tourne PHP.

Cette RFC vise donc à uniformiser les choses, en considérant que c&rsquo;est le rôle d&rsquo;un langage de haut-niveau comme PHP.

Les échanges que nous avons eu sur la mailing-list `php-internals@afup` montrant assez bien que nous étions globalement d&rsquo;accord sur le fait qu&rsquo;uniformiser le langage est une bonne chose et que les développeurs travaillant avec un langage de haut-niveau ne devraient pas avoir à se soucier du type de détails que veut corriger la RFC, j&rsquo;ai [posté en ce sens sur internals@](http://news.php.net/php.internals/77391).

Cette RFC a été acceptée quelques jours après et le comportement de PHP 7, pour ce qui concerne quelques cas spécifiques de manipulation d&rsquo;entiers, devrait donc être moins dépendant de la plate-forme sur laquelle nos applications sont exécutées.
