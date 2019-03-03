---
id: 171
title: 'RFC : Skipping optional parameters for functions'
date: 2015-02-24T08:30:09+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=171
permalink: /2015/02/24/rfc-skipping-optional-parameters-for-functions/
categories:
  - Non classé
---
Ce n&rsquo;est pas tout à fait la première fois que le sujet était évoqué, mais avec PHP 7 en approche, voici une RFC qui est revenue sur le devant de la scène : **Skipping optional parameters for functions**.

  * URL : <https://wiki.php.net/rfc/skipparams>
  * Version cible : PHP 7

Aujourd&rsquo;hui, lorsque l&rsquo;on souhaite appeler une fonction qui accepte des paramètres optionnels, il est impératif de spécifier la valeur de tous les paramètres jusqu&rsquo;au dernier qui nous intéresse &#8212; y compris si nous voulons utiliser la valeur par défaut des précédents.

Par exemple, considérons une fonction définie ainsi :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    function ma_fonction($premier, $second = &#034;world&#034;, $troisieme = false) {
        // la la la
    }

[/pastacode]

Pour appeler cette fonction en passant `true` en dernier paramètre, en conservant la valeur par défaut pour le second, nous devons écrire ceci :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    ma_fonction(&#034;Hello&#034;, &#034;world&#034;, true);

[/pastacode]

Nous devons ainsi, lors de l&rsquo;appel, passer la valeur `"world"` en second paramètre, alors que ce que nous voulions réellement faire était passer la valeur par défaut.

Cette RFC vise à répondre à cette problématique en permettant l&rsquo;usage du mot-clef `default` à la place du passage de paramètres optionnels, pour ceux dont nous souhaitons utiliser la valeur par défaut.

L&rsquo;exemple d&rsquo;appel reproduit plus haut deviendrait donc :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    ma_fonction(&#034;Hello&#034;, default, true);

[/pastacode]

Les votes pour cette RFC ont été ouverts le 08 février 2015 et clôturés le 21 février 2015.  
[Nous avons exprimé notre avis, négatif, sur `internals@`](http://news.php.net/php.internals/83389) : principalement, l&rsquo;approche proposée nous semblait trop _bidouille_ et nous préférerions bénéficier de paramètres nommés, même si ceux-ci n&rsquo;arriveront probablement pas pour PHP 7.0 (et que la RFC citée ici n&rsquo;était pas incompatible avec cette idée).  
Cette RFC a finalement été rejetée, avec 17 votes &laquo;&nbsp;pour&nbsp;&raquo; et 27 votes &laquo;&nbsp;contre&nbsp;&raquo;.