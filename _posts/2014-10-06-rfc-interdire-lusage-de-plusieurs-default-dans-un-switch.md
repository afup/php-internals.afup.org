---
id: 18
title: 'RFC: Interdire l&rsquo;usage de plusieurs &lsquo;default&rsquo; dans un &lsquo;switch&rsquo;'
date: 2014-10-06T06:35:11+00:00
author: Pascal MARTIN
layout: post
guid: http://php-internals.afup.org/?p=18
permalink: /2014/10/06/rfc-interdire-lusage-de-plusieurs-default-dans-un-switch/
categories:
  - Non classé
---
La RFC [Make defining multiple default cases in a switch a syntax error](https://wiki.php.net/rfc/switch.default.multiple) partait du constat qu&rsquo;il est aujourd&rsquo;hui possible, en PHP, de placer plusieurs sections `default` dans un bloc `switch`.

Par exemple, en PHP 5.6, il est possible d&rsquo;écrire ceci :

<pre>$a = 10;
switch ($a) {
    case 1:
        echo "cas 1\n";
        break;
    default:
        echo "premier default\n";
        break;
    default:
        // C'est dans ce second default qu'on passe, pas dans le premier
        echo "second default\n";
        break;
}</pre>

Dans ce cas, c&rsquo;est la dernière section `default` qui est utilisée par PHP (là où, différences d&rsquo;implémentation oblige, HHVM utilise la première).

Bien sûr, les discussions sur la mailing-list `php-internals@afup` ont montré que nous étions tous d&rsquo;accord sur le fait qu&rsquo;utiliser deux cas `default` dans une même structure `switch` n&rsquo;a pas de sens et devrait donc être interdit et lever une erreur de syntaxe (en PHP 7). De plus, si PHP 5.7 sort un jour, cela devrait lever un avertissement `E_DEPRECATED`, pour préparer l&rsquo;arrivée de PHP 7.  J&rsquo;ai donc [posté en ce sens sur internals@](http://news.php.net/php.internals/77216).

Cette RFC ayant été acceptée quelques jours après, PHP 7 sera plus cohérent sur ce point.