---
id: 251
title: 'RFC: Make empty() a Variadic'
date: 2015-03-25T08:30:23+00:00
author: Pascal MARTIN
layout: post
guid: http://php-internals.afup.org/?p=251
permalink: /2015/03/25/rfc-make-empty-a-variadic/
categories:
  - Non classé
---
Voici une courte RFC autour de la construction `empty()` :

  * Nom : Make `empty()` a Variadic
  * URL : <https://wiki.php.net/rfc/variadic_empty>
  * Version cible : PHP 7

Cette RFC partait de l&rsquo;idée qu&rsquo;il est commun de vouloir utiliser `empty()` sur plusieurs variables, en vue de déterminer si l&rsquo;une d&rsquo;entre elles est vide ou si aucune ne l&rsquo;est ; ce qui passe actuellement par une portion de code de ce type :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    if (empty($a) || empty($b) || empty($c)) {
        // Une des variable est vide
    }
    
    if (!empty($a) && !empty($b) && !empty($c)) {
        // Aucune variable vide
    }

[/pastacode]

Pour simplifier l&rsquo;écriture de ce type de test, cette RFC proposait de rendre `empty()` variadique (comme l&rsquo;est déjà `isset()`), ce qui permettrait d&rsquo;utiliser l&rsquo;écriture suivante :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    if (empty($a, $b, $c)) {
        // Une des variable est vide
    }
    
    if (!empty($a, $b, $c)) {
        // Aucune variable vide
    }

[/pastacode]

Passer plusieurs expressions à `empty()` reviendrait à effectuer un OR entre `empty()` de chaque expression.

Les votes ont été ouverts le 7 mars 2015 pour être clôturés le 21 mars. Considérant que cette proposition apporterait un fort risque de confusion (est-ce qu&rsquo;on vérifie qu&rsquo;_au moins une_ donnée est _vide_ ? Ou est-ce qu&rsquo;on vérifie que _toutes_ les données sont _vides_ ?), nous avons exprimé [un avis négatif sur `internals@`](http://news.php.net/php.internals/85347).

Une majorité des 2/3 était requise pour l&rsquo;adoption de cette RFC et elle a été rejetée, avec 26 votes &laquo;&nbsp;pour&nbsp;&raquo; et 26 votes &laquo;&nbsp;contre&nbsp;&raquo;.