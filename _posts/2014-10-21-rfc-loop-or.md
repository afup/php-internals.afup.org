---
id: 35
title: 'RFC: Loop&#8230; or'
date: 2014-10-21T07:05:07+00:00
author: Pascal MARTIN
layout: post
guid: http://php-internals.afup.org/?p=35
permalink: /2014/10/21/rfc-loop-or/
categories:
  - Non classé
---
La RFC [Loop&#8230; or&#8230;](https://wiki.php.net/rfc/loop_or) proposait d&rsquo;ajouter un bloc, optionnel, aux structures de boucles (`for`, `while` et `foreach`) de PHP, exécuté dans le cas où on n&rsquo;entre jamais dans la boucle &#8212; la condition n&rsquo;étant pas vérifiée, dès le premier passage. Ce bloc aurait été introduit par le mot-clef `or`, afin d&rsquo;éviter d&rsquo;ajouter un nouveau mot réservé.

Il est ressorti de nos échanges que la majorité d&rsquo;entre nous était plutôt _pour_ cette fonctionnalité, même si n&rsquo;étions pas à 100% de _oui_ et que plusieurs auraient aimé pouvoir utiliser `else` plutôt que `or`, ou disposer de quelque chose de plus complet répondant à plus de cas. J&rsquo;ai donc [posté en ce sens sur internals@](http://news.php.net/php.internals/77835).

Arrivée au moment de la phase de votes, cette RFC a été quelque peu mise de côté et elle n&rsquo;a pas été acceptée. À voir si une solution plus complète, répondant à plus de cas que le seul _&laquo;&nbsp;on n&rsquo;est jamais entré dans la boucle&nbsp;&raquo;_ reviendra sur le devant de la scène dans le futur !