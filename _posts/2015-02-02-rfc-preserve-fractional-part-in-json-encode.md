---
id: 115
title: 'RFC: Preserve Fractional Part in JSON encode'
date: 2015-02-02T08:30:51+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=115
permalink: /2015/02/02/rfc-preserve-fractional-part-in-json-encode/
categories:
  - Non classé
---
[Cette RFC](https://wiki.php.net/rfc/json_preserve_fractional_part) proposait d&rsquo;ajouter une option (un flag) supplémentaire à `json_encode()`.

Elle partait en effet du constat que `json_encode()` encode le flottant `10.0` (côté PHP) vers l&rsquo;entier `10` (côté JSON). L&rsquo;opération inverse JSON → PHP donnait donc l&rsquo;entier `10` (côté PHP) &#8212; et, donc, encoder puis décoder une donnée ne menait pas à la même information que celle de départ.

{% highlight php %}
    // Actuellement
    echo json_encode(10.0); // Affiche 10
    echo json_encode(10.1); // Affiche 10.1
    var_dump(json_decode(json_encode(10.0))); // Affiche int(10)
    var_dump(10.0 === json_decode(json_encode(10.0))); // Affiche bool(false)
{% endhighlight %}

Par conséquent, il était proposé d&rsquo;ajouter un nouveau flag `JSON_PRESERVE_FRACTIONAL_PART` qui entraînerait la conservation de cette information.

{% highlight php %}
    // Proposé
    echo json_encode(10.0); // Affiche 10
    echo json_encode(10.1); // Affiche 10.1
    echo json_encode(10.0, JSON_PRESERVE_ZERO_FRACTION); // Affiche 10.0
    echo json_encode(10.1, JSON_PRESERVE_ZERO_FRACTION); // Affiche 10.1
    var_dump(json_decode(json_encode(10.0, JSON_PRESERVE_ZERO_FRACTION))); // Affiche double(10)
    var_dump(10.0 === json_decode(json_encode(10.0, JSON_PRESERVE_ZERO_FRACTION))); // Affiche bool(true)
{% endhighlight %}

## Note

Stocker `10.0` sous la forme `10` ou sous la forme `10.0` en JSON est conforme à la spécification JSON, qui ne différencie pas les différents types de nombres &#8212; et certains langages convertissent en `10.0` alors que d&rsquo;autres, comme PHP aujourd&rsquo;hui, convertissent vers `10`.

  * URL : [https://wiki.php.net/rfc/json\_preserve\_fractional_part](https://wiki.php.net/rfc/json_preserve_fractional_part)
  * Version cible : PHP 5.x.x

Les votes ont été ouverts sur cette RFC le 11 janvier 2015 pour être clôturés le 18 janvier 2015 et [nous avons exprimé un avis favorable sur `internals@`](http://news.php.net/php.internals/80710).  
Cette proposition a été adoptée par 14 voix contre aucune.
