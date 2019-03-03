---
id: 45
title: 'RFC: Safe Casting Functions'
date: 2015-01-20T08:30:23+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=45
permalink: /2015/01/20/rfc-safe-casting-functions/
categories:
  - Non classé
---
[Cette RFC](https://wiki.php.net/rfc/safe_cast) partait du constat que les opérateurs de transtypage existant, explicites, n&rsquo;échouent jamais et ne lèvent jamais d&rsquo;erreur &#8212; ce qui peut être dangereux (surtout s&rsquo;ils sont utilisés sur des saisies utilisateurs), puisqu&rsquo;ils retourneront un peu n&rsquo;importe quoi si les données sur lesquelles on les utilise correspondent elles-mêmes à un peu n&rsquo;importe quoi.

Elle proposait donc d&rsquo;ajouter trois fonctions, qui auraient validé leur entrée, au lieu de transtyper aveuglément. Initialement, elles auraient retourné `false` en cas d&rsquo;erreur (ce retour aurait pu être soumis à un vote complémentaire) :

  * `to_int()` : n&rsquo;aurait accepté que des entiers, des flottants contenant des entiers et pouvant être représentés par des entiers, ou des chaînes contenant la représentation textuelle d&rsquo;entiers.
  * `to_float()` : n&rsquo;aurait accepté que des flottants, des entiers et des chaînes représentant des flottants.
  * `to_string()` : n&rsquo;aurait accepté que des chaînes, des entiers, des flottants et des objets transtypables en chaînes.

[La RFC](https://wiki.php.net/rfc/safe_cast) entre plus en détail sur le pourquoi de pas mal de choix et donne un long tableau d&rsquo;exemples.

Les votes ont été ouverts le 19 novembre 2014 et ont été clos le 29 novembre 2014. Nous avons [posté un _timide +0.5_ sur `internals@`](http://news.php.net/php.internals/79314), en considérant que ces fonctions n&rsquo;allaient pas assez loin vers un réel typage plus strict.  
Cette RFC a finalement été rejetée par 16 votes contre 5.