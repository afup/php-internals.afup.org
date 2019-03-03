---
id: 32
title: 'RFC: Suppression des tags alternatifs'
date: 2014-10-20T07:05:03+00:00
author: Pascal MARTIN
layout: post
guid: http://php-internals.afup.org/?p=32
permalink: /2014/10/20/rfc-suppression-des-tags-alternatifs/
categories:
  - Non classé
---
La RFC [Remove alternative PHP tags](https://wiki.php.net/rfc/remove_alternative_php_tags) partait du principe que les tags _alternatifs_ (tags &laquo;&nbsp;ASP&nbsp;&raquo; `<%` ou `<%=` et `%>`, ainsi que `<script language="php">` et `</script>`) ne sont quasiment jamais utilisés &#8212; sans compter qu&rsquo;ils entrent parfois en conflit avec certains langages de templating.

Nous avons été assez nombreux à échanger sur le sujet, majoritairement d&rsquo;accords sur le fait que ces tags ne sont quasiment jamais utilisés et qu&rsquo;il serait acceptable de les supprimer, pour ne laisser que les balises `<?php`, `<?` et `<?=` les plus connues. J&rsquo;ai donc [posté en ce sens sur internals@](http://news.php.net/php.internals/77732).

Cette RFC a été acceptée, avec une large majorité. Les tags _alternatifs_ disparaitront donc, pour PHP 7.