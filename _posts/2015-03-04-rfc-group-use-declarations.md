---
id: 176
title: 'RFC: Group Use Declarations'
date: 2015-03-04T08:30:29+00:00
author: Pascal MARTIN
layout: post
guid: http://php-internals.afup.org/?p=176
permalink: /2015/03/04/rfc-group-use-declarations/
categories:
  - Non classé
---
Voici une RFC qui proposait d&rsquo;ajouter une possibilité syntaxique à PHP, visant à faciliter l&rsquo;utilisation d&rsquo;espaces de noms : Group Use Declarations

  * URL : [https://wiki.php.net/rfc/group\_use\_declarations](https://wiki.php.net/rfc/group_use_declarations)
  * Version cible : PHP 7

Pour résumer, cette RFC partait du constat qu&rsquo;écrire de multiples utilisations d&rsquo;espaces de noms à plusieurs niveaux de profondeur entraîne une longueur de code impressionnante. Elle proposait donc l&rsquo;introduction d&rsquo;une nouvelle syntaxe, qui permettrait de réduire l&rsquo;espace utilisé par ces `use` multiples et de rendre le code moins verbeux.

Par exemple, la portion de code suivante :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    use Doctrine\Common\Collections\Expr\Comparison;
    use Doctrine\Common\Collections\Expr\Value;
    use Doctrine\Common\Collections\Expr\CompositeExpression;

[/pastacode]

Pourrait être ré-écrite de la manière suivante :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    use Doctrine\Common\Collections\Expr\{ Comparison, Value, CompositeExpression };

[/pastacode]

La RFC présente d&rsquo;autres cas d&rsquo;exemples, avec des &laquo;&nbsp;`use ... as ...`&laquo;&nbsp;, des `use function` ou `const` et montre que la syntaxe n&rsquo;est pas limitée au dernier niveau de chaque espace de noms. Elle répond également à certains retours &laquo;&nbsp;communs&nbsp;&raquo; sur la proposition et sa syntaxe.

Les votes ont été ouverts le 11 février 2015 et pour être clôturés le 25 février, avec deux options :

  * &laquo;&nbsp;Oui&nbsp;&raquo;, avec un `\` à la fin de l&rsquo;inclusion (le dernier : dans l&rsquo;exemple reproduit plus haut `...\Expr\{}` ),
  * &laquo;&nbsp;Oui&nbsp;&raquo;, sans cet `\` à la fin de l&rsquo;inclusion &#8212; on aurait donc `...\Expr{}`
  * Et, bien sûr, &laquo;&nbsp;non&nbsp;&raquo;

Les discussions que nous avons menées sur notre mailing-list ne nous ont pas permis d&rsquo;atteindre un consensus et [nous avons exprimé sur `internals@`](http://news.php.net/php.internals/83770) les principaux arguments auxquels nous étions arrivés.

Une majorité de 2/3 était requise pour son adoption, et cette RFC a été approuvée avec les résultats suivants :

  * Oui, avec un \ à la fin de l&rsquo;inclusion : 32 voix;
  * Oui, sans le \ à la fin de l&rsquo;inclusion : 7 voix;
  * Non : 19 voix