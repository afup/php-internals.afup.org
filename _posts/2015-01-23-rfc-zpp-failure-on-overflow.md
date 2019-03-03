---
id: 50
title: 'RFC: ZPP Failure on Overflow'
date: 2015-01-23T08:30:07+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=50
permalink: /2015/01/23/rfc-zpp-failure-on-overflow/
categories:
  - Non classé
---
Aujourd&rsquo;hui, lorsqu&rsquo;un nombre flottant trop grand pour tenir dans les valeurs supportées pour les entiers est passé en paramètre d&rsquo;une fonction **interne** (fonction exposée par PHP ou une extension PHP) qui attend un entier, il est reçu par la fonction sous la forme&#8230; d&rsquo;un entier&#8230; ce qui entraîne une perte d&rsquo;information.

Note technique : une fonction **interne** spécifie de quel type (au sens C du terme, donc avec du typage strict) chaque paramètre reçu doit être. Il n&rsquo;y a pas, en C, de type _fourre-tout_ comme c&rsquo;est le cas pour les variables de PHP, avec utilisation automatique de flottants lorsque des nombres sont trop grands pour tenir sur des entiers.

[Cette RFC](https://wiki.php.net/rfc/zpp_fail_on_overflow) proposait donc que, dans le cas où un paramètre entier est attendu et que la valeur reçue est un flottant trop grand pour tenir dans un entier, l&rsquo;analyse des paramètres de la fonction interne appelée échoue, que la fonction retourne sans s&rsquo;exécuter, et qu&rsquo;un avertissement soit levé.

Impact pour les utilisateurs de PHP : appeler une fonction interne attendant un entier en passant une valeur trop grande pour tenir dans un entier entraînera la levée d&rsquo;un avertissement et la non-exécution de la fonction &#8212; au lieu de son exécution avec une valeur tronquée.

Cette RFC visait la version 7 de PHP.

Les votes ont été ouverts le 2 Décembre 2014 et on été clos le 12 décembre 2014. Cette RFC touchant plus à de l&rsquo;implémentation qu&rsquo;à des fonctionnalités, nous avons timidement [exprimé notre opinion sur `internals@`](http://news.php.net/php.internals/79579), en considérant qu&rsquo;il valait mieux un avertissement clair qu&rsquo;un comportement _étrange_.  
La RFC a été adoptée à l&rsquo;unanimité (16 pour, 0 contre).