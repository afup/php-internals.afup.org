---
id: 221
title: 'RFC: Remove PHP 4 Constructors'
date: 2015-03-11T08:30:52+00:00
author: Guillaume
layout: post
guid: http://php-internals.afup.org/?p=221
permalink: /2015/03/11/rfc-remove-php-4-constructors/
categories:
  - Non classé
---
La [RFC: Remove PHP 4 Constructors](https://wiki.php.net/rfc/remove_php4_constructors), comme son nom l&rsquo;indique, visait à supprimer les constructeurs introduits dans la version 4 de PHP, où la méthode de construction des objets était appelée comme la classe elle-même :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    class Filter
    {
        // Constructor as introduced in PHP 4
        function filter() {}
    }

[/pastacode]

Ce comportement, qui induit souvent en erreur les développeurs, est depuis longtemps vu par beaucoup comme indésirable. Néanmoins, sa suppression visant (initialement) la version 7 de PHP fut génératrice d&rsquo;interrogations, notamment à cause de son utilisation récurrente dans les extensions PEAR ou même sur WordPress.

Ce sujet a également animé les débats sur `internals@` et la RFC a évolué pour passer en deux phases :

  * PHP 7 : les anciens constructeurs génèreront un avertissement de type `E_DEPRECATED`
  * PHP 8 : suppression des anciens constructeurs qui deviendront alors de simples méthodes.

Suite à cette mise à jour, les derniers doutes furent levés et nous avons majoritairement approuvé cette RFC, [postant dans ce sens sur `internals@`](http://news.php.net/php.internals/84361).

Avec 49 voix pour  et seulement 4 contre, la dernière version de la RFC a été acceptée, devenant la toute première RFC validée ayant comme version cible PHP 8 !

&nbsp;