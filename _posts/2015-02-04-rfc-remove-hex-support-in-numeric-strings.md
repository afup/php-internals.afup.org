---
id: 123
title: 'RFC: Remove hex support in numeric strings'
date: 2015-02-04T08:30:32+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=123
permalink: /2015/02/04/rfc-remove-hex-support-in-numeric-strings/
categories:
  - Non classé
---
Voici [une RFC](https://wiki.php.net/rfc/remove_hex_support_in_numeric_strings) qui proposait de supprimer le support des nombres hexadécimaux dans certains contextes.

En effet, aujourd&rsquo;hui, utiliser des nombres hexadécimaux dans une chaîne est supporté (ils sont reconnus comme des nombres) dans certains cas (`is_numeric()`, par exemple), mais pas d&rsquo;autres (casts `int` et `float`, notamment).

Cette RFC proposait donc d&rsquo;uniformiser les choses en supprimant le support des nombres hexadécimaux dans des chaînes de caractères là où ils sont aujourd&rsquo;hui reconnus :

  * Fonction `is_numeric()`
  * Opérandes des opérateurs `==`, `+`, `-`, `*`, `/`, `%`, `**`, `++` et `--`
  * Paramètres de fonctions internes convertis en entiers
  * Peut-être quelques autres cas rares.

Quelques exemples plus détaillés sont disponibles sur la page de la RFC.

  * URL : [https://wiki.php.net/rfc/remove\_hex\_support\_in\_numeric_strings](https://wiki.php.net/rfc/remove_hex_support_in_numeric_strings)
  * Version cible : PHP 7

Les votes ont été ouverts le 17 janvier 2015 pour être clôturés le 27 janvier 2015 et même si nous n&rsquo;avons été que peu nombreux à participer à la discussion, [nous avons posté favorablement sur `internals@`](http://news.php.net/php.internals/81180).  
La proposition a été adoptée à l&rsquo;unanimité (29 voix contre 0).