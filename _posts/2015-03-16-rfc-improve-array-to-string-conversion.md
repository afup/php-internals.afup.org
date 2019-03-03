---
id: 178
title: 'RFC : Improve array to string conversion'
date: 2015-03-16T08:30:26+00:00
author: Pascal MARTIN
layout: post
guid: http://php-internals.afup.org/?p=178
permalink: /2015/03/16/rfc-improve-array-to-string-conversion/
categories:
  - Non classé
---
Voici une RFC qui tourne autour de la conversion de tableaux (`array`) en chaînes (`string`) : Improve array to string conversion

  * URL : <https://wiki.php.net/rfc/array-to-string>
  * Version cible : PHP 7

Cette RFC partait du constat que, aujourd&rsquo;hui, convertir un `array` vers une `string` entraîne la levée d&rsquo;une `E_NOTICE` et donne &laquo;&nbsp;`Array`&nbsp;&raquo; comme résultat&#8230; Autrement dit, une chaîne peu utile et seulement une _semi-_erreur.

Elle proposait au départ deux alternatives (opposées) visant à éliminer ce comportement problématique :

  * Interdire totalement la conversion `array` → `string` en levant une &laquo;&nbsp;`catchable fatal error`&laquo;&nbsp;, comme c&rsquo;est déjà le cas pour la conversion `object` → `string` pour les classes n&rsquo;ayant pas de méthode `__toString()`.
  * Supporter réellement la conversion `array` → `string`, en déterminant et implémentant un algorithme réalisant la conversion.

Après discussions sur `internals@`, la seconde option a été supprimée avant l&rsquo;ouverture des votes, qui n&rsquo;ont donc porté que sur la première.

Considérant que la conversion `array` → `string` n&rsquo;était que rarement voulue et correspondait quasiment toujours à des cas de bugs, [nous avons indiqué sur `internals@`](http://news.php.net/php.internals/84363) que nous étions en faveur de cette proposition.  
La RFC a finalement été acceptée, avec 34 votes &laquo;&nbsp;pour&nbsp;&raquo; et 10 votes &laquo;&nbsp;contre&nbsp;&raquo;.

&nbsp;

&nbsp;