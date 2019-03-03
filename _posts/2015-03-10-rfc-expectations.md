---
id: 209
title: 'RFC: Expectations'
date: 2015-03-10T08:30:32+00:00
author: Pascal MARTIN
layout: post
guid: http://php-internals.afup.org/?p=209
permalink: /2015/03/10/rfc-expectations/
categories:
  - Non classé
---
Voici une RFC destinée à servir principalement en environnements de développement :

  * Nom : Expectations
  * URL : <https://wiki.php.net/rfc/expectations>
  * Version cible : PHP 7

L&rsquo;idée derrière cette RFC, basée sur la fonction `assert()`, est de permettre l&rsquo;exécution de code de débogage, en développement uniquement. Cela permettrait à la fois d&rsquo;identifier des problèmes (encore une fois, en environnements de développement) et de documenter le code. Plusieurs exemples illustrant les différents cas d&rsquo;usage sont donnés dans la RFC.

En cas d&rsquo;échec, la condition spécifiée en premier paramètre de `assert()` n&rsquo;étant pas vraie, une exception de type `AssertException` (soit spécifiée en second paramètre, soit générée automatiquement) sera levée &#8212; passer par une exception plutôt qu&rsquo;une erreur permettant d&rsquo;obtenir plus facilement une stacktrace.

L&rsquo;activation ou non des assertions serait paramétrée par le biais d&rsquo;une directive `.ini` nommée `zend.assertions`, qui pourrait valoir :

  * `1` : pour générer et exécuter le code correspondant aux assertions : c&rsquo;est la valeur qui sera généralement utilisée en environnement de développement
  * `0` : pour générer le code mais ne pas l&rsquo;exécuter
  * `-1` : pour ne pas du tout générer le code de l&rsquo;assertion (coût nul, à utiliser en production)

L&rsquo;API proposée par cette RFC est globalement compatible avec celle actuellement en place pour la fonction `assert()` existante : il s&rsquo;agit surtout d&rsquo;améliorer celle-ci, notamment en supprimant complétement la génération et l&rsquo;exécution du code de l&rsquo;assertion en mode &laquo;&nbsp;production&nbsp;&raquo;.

Les votes se sont tenus du 19 au 26 février et [nous avons exprimé un avis plutôt négatif sur `internals@`](http://news.php.net/php.internals/83912), considérant principalement que mélanger le code et les tests n&rsquo;était pas l&rsquo;approche qui nous semblait la meilleure et ne souhaitant donc pas encourager l&rsquo;utilisation de `assert()`.  
Les résultats ont finalement été les suivants, cette RFC est donc passée :

  * 20 &laquo;&nbsp;oui&nbsp;&raquo; avec exceptions personnalisées
  * 11 &laquo;&nbsp;oui&nbsp;&raquo; sans exception personnalisée
  * 1 seul et unique &laquo;&nbsp;non&nbsp;&raquo;
