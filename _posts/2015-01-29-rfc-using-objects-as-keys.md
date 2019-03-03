---
id: 85
title: 'RFC: Using objects as keys'
date: 2015-01-29T08:30:15+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=85
permalink: /2015/01/29/rfc-using-objects-as-keys/
categories:
  - Non classé
---
Voici [une RFC](https://wiki.php.net/rfc/objkey) qui avait été évoquée pendant les discussions à propos de `UString` : Using objects as keys.

L&rsquo;idée de cette RFC était de permettre (de façon détournée) à des objets d&rsquo;être utilisés comme clefs de tableaux &#8212; les tableaux PHP ne supportant en interne, comme clefs, que des entiers ou des chaînes.

Pour cela, une nouvelle méthode magique (qui pourrait être nommée `__hash()` &#8212; le nom proposé n&rsquo;étant pas nécessairement définitif) serait mise en place : elle serait appelée lorsque l&rsquo;on essayerait d&rsquo;utiliser un objet comme clef d&rsquo;un tableau, pour retourner la chaîne de caractères ou l&rsquo;entier à réellement employer.

Par exemple, il deviendrait possible d&rsquo;écrire quelque chose de ce type :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;Exemple&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    $obj = new MaClasse(); // implémentant une méthode __hash()
    $arr = [];
    $arr[$obj] = /* ici, quelque chose stocké dans le tableau, à l&#039;index $obj->hash() */

[/pastacode]

  * URL  :  <https://wiki.php.net/rfc/objkey>
  * Version cible : PHP 7

Les votes se sont tenus entre le 16 décembre 2014 et le 6 janvier 2015 et requéraient une majorité de 2/3. Nous avons exprimé [notre opinion, défavorable du fait que cette proposition n&rsquo;aille pas _assez loin_, sur `internals@`](http://news.php.net/php.internals/80200).  
Cette proposition a été rejetée à 24 voix contre 6.