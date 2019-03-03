---
id: 223
title: 'RFC: Exceptions in the engine'
date: 2015-03-12T08:46:35+00:00
author: Guillaume
layout: post
guid: http://php-internals.afup.org/?p=223
permalink: /2015/03/12/rfc-exceptions-in-the-engine/
categories:
  - Non classé
---
La [RFC: Exceptions in the engine](https://wiki.php.net/rfc/engine_exceptions_for_php7) visait à généraliser l&rsquo;utilisation d&rsquo;exceptions dans le moteur PHP ainsi qu&rsquo;à transformer en exceptions la plupart des erreurs fatales, ce afin de laisser aux applications la possibilité de contrôler ces erreurs.

Cette RFC introduisait pour cela deux nouveaux types d&rsquo;exceptions :

  * `EngineException` : type d&rsquo;exception générique générée par le moteur PHP
  * `ParseException` : exception générée lorsque le code PHP ne peut être traité

À cela s&rsquo;ajoute une classe de base, abstraite, `BaseException`, qui viendrait se mettre en place dans la hiérarchie des exceptions comme suit :

    BaseException (abstract)
     +- EngineException
     +- ParseException
     +- Exception
         +- ErrorException
         +- RuntimeException
             +- ...
         +- ...

Les blocs attrapant les exceptions de type `Exception` n&rsquo;attraperaient pas ces nouvelles exceptions, ne générant ainsi aucun effet de bord côté utilisateur.

Il est ressorti de nos échanges que nous étions en très large majorité en faveur de cette RFC et avons donc [posté en ce sens sur internals@](http://news.php.net/php.internals/84416).

Avec 60 voix pour et seulement 2 contre, cette RFC a été accepté et sera mise en place dans la version 7 de PHP.