---
id: 81
title: 'RFC: Unicode Codepoint Escape Syntax'
date: 2015-01-26T08:30:49+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=81
permalink: /2015/01/26/rfc-unicode-codepoint-escape-syntax/
categories:
  - Non classé
---
[Cette RFC](https://wiki.php.net/rfc/unicode_escape) proposait de permettre l&rsquo;utilisation de séquences Unicode dans les chaînes de caractères (à double-guillemets et heredoc) de PHP.

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;Exemple&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    $str = &#034;Un caractère unicode : \u{1F602}&#034;;

[/pastacode]

La RFC proposait d&rsquo;autres exemples et expliquait pourquoi il avait été choisi de positionner `{` et `}` autour du code du caractère : lisibilité et pas de limite en dur au nombre de caractères attendus pour spécifier le code.

<li style="padding-left: 30px">
  Version cible : PHP 7
</li>
<li style="padding-left: 30px">
  URL de la RFC : <a href="https://wiki.php.net/rfc/unicode_escape">https://wiki.php.net/rfc/unicode_escape</a>
</li>

Les votes se sont tenus du 8 décembre 2014 au 18 décembre 2014 et nous avons [exprimé notre opinion positive sur `internals@`](http://news.php.net/php.internals/79793).  
La RFC a été adoptée à 23 voix contre 2.