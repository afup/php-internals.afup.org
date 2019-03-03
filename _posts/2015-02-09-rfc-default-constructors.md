---
id: 121
title: 'RFC: Default constructors'
date: 2015-02-09T08:30:55+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=121
permalink: /2015/02/09/rfc-default-constructors/
categories:
  - Non classé
---
Voici une petite RFC qui visait à simplifier notre vie : [default constructors](https://wiki.php.net/rfc/default_ctor).

Cette RFC proposait que, dans le constructeur d&rsquo;une classe, il soit toujours possible d&rsquo;appeler `parent::__construct()`, quelque soit la classe parente, y compris si celle-ci ne définissait pas explicitement de constructeur.  
En somme, l&rsquo;appel de `parent::__construct()` n&rsquo;échouerait plus jamais.

Une fois cette idée implémentée, une classe enfant pourrait appeler le constructeur de sa classe parente, même si celle-ci n&rsquo;en a pas.  
Et le jour où un constructeur serait ajouté à la classe parente, il serait alors effectivement appelé &#8212; sans que nous n&rsquo;ayons à repasser sur toutes ses classes enfant pour ajouter cet appel (comme nous devons le faire aujourd&rsquo;hui).

Cela aurait également facilité les choses pour certaines classes fournies par PHP : en général, on dit que lorsqu&rsquo;une classe de PHP est étendue en espace utilisateur, la classe fille doit impérativement appeler le constructeur de la classe parente fournie par PHP&#8230; Sauf que certaines de ces classes fournies par PHP n&rsquo;ont pas de constructeur. C&rsquo;est donc au développeur d&rsquo;aller chercher, au cas par cas, s&rsquo;il doit ou non appeler celui-ci.  
Avec cette RFC, il ne serait plus nécessaire de s&rsquo;interroger, puisqu&rsquo;il deviendrait systématiquement possible d&rsquo;appeler le constructeur de la classe parente, qu&rsquo;il soit ou non défini.

  * URL : <https://wiki.php.net/rfc/default_ctor>
  * Version cible : PHP 7

Les votes ont été ouverts le 17 janvier 2015 et clôturés le 24 janvier 2015 et [nous avons exprimé un avis positif (de peu) sur `internals@`](http://news.php.net/php.internals/81076).  
Une majorité au 2/3 de _oui_ était requise pour l&rsquo;adoption de cette RFC, mais un résultat de 27 voix _pour_ et 20 _contre_ a décidé de son rejet.