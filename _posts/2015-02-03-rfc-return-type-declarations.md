---
id: 117
title: 'RFC: Return Type Declarations'
date: 2015-02-03T08:30:40+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=117
permalink: /2015/02/03/rfc-return-type-declarations/
categories:
  - Non classé
---
L&rsquo;idée avait déjà été évoquée alors que PHP 5.6 était en cours de préparation &#8212; peut-être via une RFC pour 5.7.  
En tout cas, voici le retour de cette proposition, mise à jour par rapport à la branche master, avec la RFC : [Return Type Declarations](https://wiki.php.net/rfc/return_types).

Pour faire simple : cette RFC proposait de mettre en place la possibilité de spécifier un type de retour pour les fonctions et méthodes. Ce type de retour serait, bien sûr, optionnel : s&rsquo;il est spécifié, il devra être respecté, mais s&rsquo;il n&rsquo;est pas présent, les choses fonctionneront comme aujourd&rsquo;hui (on retrouve la logique déjà en place sur le _type-hinting_ de paramètres).

Avec la syntaxe proposée, il deviendrait possible de déclarer, par exemple, qu&rsquo;une fonction retourne toujours un tableau :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    function foo(): array {
        return [];
    }

[/pastacode]

Bien entendu, cette fonctionnalité est également branchée dans l&rsquo;API de `Reflection`.

  * URL : <https://wiki.php.net/rfc/return_types>
  * Version cible : PHP 7

Les votes ont été ouverts le 16 janvier 2015 et clôturés le 23 janvier 2015 et [nous avons posté un avis positif sur `internals@`](http://news.php.net/php.internals/80996).  
La RFC a été adoptée par 47 voix contre 3 et il sera donc possible, avec PHP 7, de spécifier un type de retour pour les fonctions et méthodes !