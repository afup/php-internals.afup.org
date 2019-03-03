---
id: 7
title: 'RFC: Opérateur null-coalesce ??'
date: 2014-10-06T06:30:36+00:00
author: Pascal MARTIN
layout: post
guid: http://php-internals.afup.org/?p=7
permalink: /2014/10/06/rfc-operateur-null-coalesce/
categories:
  - Non classé
---
La RFC [Null Coalesce Operator](https://wiki.php.net/rfc/isset_ternary) proposait d&rsquo;introduire un nouvel opérateur `??` qui renverrait le résultat de sa première opérande s&rsquo;il existe et est différent de `NULL` (en comparaison stricte), et celui de sa seconde opérande sinon.

Le constant de départ était que l&rsquo;opérateur `?:` introduit avec PHP 5.3 est pratique, mais pas parfait : il peut notamment entrainer des levées de notices si sa première opérande n&rsquo;existe pas (ce qui force souvent à utiliser `isset()`).

Avec le nouvel opérateur `??` proposé par cette RFC, il deviendrait possible d&rsquo;écrire quelque chose de ce type, qui ne lèverait pas de notice si `$_GET['user']` n&rsquo;existe pas :

<pre>$username = $_GET['user'] ?? 'nobody';</pre>

Les échanges que nous avons eu sur la mailing-list `php-internals@afup` ayant montré que notre avis était plutôt positif et qu&rsquo;un tel opérateur apporterait une valeur à PHP, j&rsquo;ai [posté en ce sens sur internals@](http://news.php.net/php.internals/77685).

La RFC correspondante à été acceptée et ce nouvel opérateur `??` devrait arriver avec PHP 7 !

Notons que l&rsquo;ajout d&rsquo;un opérateur d&rsquo;affectation `??=` n&rsquo;a pour l&rsquo;instant pas été jugé utile. Il pourra, bien sûr, être ajouté dans le futur, s&rsquo;il s&rsquo;avère qu&rsquo;il est nécessaire.