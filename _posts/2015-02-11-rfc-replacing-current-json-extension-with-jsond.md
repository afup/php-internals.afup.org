---
id: 125
title: 'RFC: Replacing current json extension with jsond'
date: 2015-02-11T08:30:21+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=125
permalink: /2015/02/11/rfc-replacing-current-json-extension-with-jsond/
categories:
  - Non classé
---
[Cette RFC](https://wiki.php.net/rfc/jsond) proposait une modification tournant autour des extensions de manipulation de JSON.

En effet, le parser JSON actuellement utilisé par l&rsquo;extension `ext/json` a une licence non-libre, qui pose problème à certaines distributions, et l&rsquo;extension `ext/json` en elle-même est vieille, pas optimale et peu maintenue.

Cette RFC proposait donc de remplacer l&rsquo;extension `ext/json` par du code basé sur l&rsquo;extension `ext/jsond`, actuellement disponible via PECL.

La RFC donnait quelques points isolés qui vont partir en BC-break (notamment au niveau des flottants) ainsi qu&rsquo;un lien vers des résultats de benchmarks.

  * URL : <https://wiki.php.net/rfc/jsond>
  * Version cible : PHP 7

Les votes ont été ouverts le 26 janvier 2015 pour être clôturés le 1<sup>er</sup> février 2015. Corriger les problèmes de licence nous semblant important pour un logiciel libre, [nous avons exprimé un avis positif sur `internals@`](http://news.php.net/php.internals/81526).  
La RFC a été adoptée à l&rsquo;unanimité, avec 32 voix contre 0.