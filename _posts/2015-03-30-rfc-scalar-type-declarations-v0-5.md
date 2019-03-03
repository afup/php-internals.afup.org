---
id: 247
title: 'RFC: Scalar Type Declarations (v0.5)'
date: 2015-03-30T08:30:09+00:00
author: Pascal MARTIN
layout: post
guid: http://php-internals.afup.org/?p=247
permalink: /2015/03/30/rfc-scalar-type-declarations-v0-5/
categories:
  - Non classé
---
L&rsquo;idée d&rsquo;introduire des _type-hints_ scalaires pour les paramètres de fonctions et méthodes est revenue plusieurs fois sur le devant de la scène ces dernières années.

[Une première RFC &laquo;&nbsp;Scalar Type Hints&nbsp;&raquo;](https://wiki.php.net/rfc/scalar_type_hints) a récemment été jusqu&rsquo;à la phase de votes (ceux-ci étant particulièrement serrés avec un nombre record de participants), mais a été retirée suite au départ de son auteur.

La demande de _type-hints_ scalaires étant visiblement forte au niveau de la communauté (au vu des échanges sur twitter, du nombre de blog-posts sur le sujet, des réactions sur reddit, &#8230;), Anthony Ferrara a relancé l&rsquo;idée quelques jours plus tard, avec une RFC forkée depuis celle d&rsquo;Andrea :

  * Scalar Type Declarations v0.5
  * URL : [https://wiki.php.net/rfc/scalar\_type\_hints_v5](https://wiki.php.net/rfc/scalar_type_hints_v5)

Cette nouvelle version de la RFC introduisait quelques différences relativement mineures par rapport à la précédente version 0.3, qui était en cours de vote une semaine avant :

  * L&rsquo;instruction `declare()` doit désormais être la première du fichier.
  * Elle ne peut plus être utilisée en mode bloc ; seulement en mode fichier entier.
  * Les aliases `integer` et `boolean` ont été supprimés.
  * Et un entier est maintenant considéré comme valide pour le type-hint `float` ; y compris en mode strict.

Une longue section [&laquo;&nbsp;Discussion points&nbsp;&raquo;](https://wiki.php.net/rfc/scalar_type_hints_v5#discussion_points) a également été ajoutée, visant à répondre à de nombreuses questions habituelles sur le sujet et la proposition.

L&rsquo;adoption de cette RFC demandait une majorité des 2/3 des voix. Les votes ouvert le 26 février ont été clôturés le 13 mars 2015. Comme pour la version précédente de cette proposition, [nous avons exprimé un avis positif sur `internals@`](http://news.php.net/php.internals/84658).

Finalement, avec 108 votes &laquo;&nbsp;pour&nbsp;&raquo; et 48 votes &laquo;&nbsp;contre&nbsp;&raquo; (un tel nombre de votes, c&rsquo;est un record !), cette RFC a été acceptée ! PHP 7.0 disposera donc de type-hints scalaires !
