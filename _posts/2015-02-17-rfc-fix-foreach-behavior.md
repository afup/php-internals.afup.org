---
id: 140
title: 'RFC: Fix "foreach" behavior'
date: 2015-02-17T08:30:46+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=140
permalink: /2015/02/17/rfc-fix-foreach-behavior/
categories:
  - Non classé
---
Voici une RFC à propos de la construction de boucle `foreach` : Fix "foreach" behavior

  * URL : <https://wiki.php.net/rfc/php7_foreach>
  * Version cible : PHP 7

L&rsquo;idée de départ de cette proposition était d&rsquo;améliorer les performances de `foreach` (autour de 1% de gain pour certaines applications)&#8230; Mais, finalement, la RFC s&rsquo;est plus orientée sur la correction d&rsquo;incohérences et de comportement indéfinis.

Sans entrer dans les détails (ils sont plutôt techniques) sur cette page, il s&rsquo;agit en somme d&rsquo;essayer d&rsquo;uniformiser quelques cas un peu _tordus_ d&rsquo;utilisation de `foreach` en cas d&rsquo;itérations par valeurs et par références &#8212; [la RFC liste ces cas](https://wiki.php.net/rfc/php7_foreach#proposal), avec des exemples.

Cette RFC a été soumise à deux votes, ouverts le 05 févier 2015 pour être clôturés le 12 février 2015 :

  * le premier concernait directement la RFC, à une majorité des 2/3 des voix,
  * et le second demandait s&rsquo;il faudrait cesser de modifier le pointeur tableau/objet dans `foreach` et nécessitait une majorité de 50% +1 voix.

Considérant que PHP 7 est une bonne occasion pour corriger des comportements étranges et apporter un peu de cohérence au langage, nous avons [exprimé notre opinion, positive, sur `internals@`](http://news.php.net/php.internals/82496).  
Les deux propositions de cette RFC ont été acceptées, toutes deux avec 34 voix pour 1 et une voix contre.
