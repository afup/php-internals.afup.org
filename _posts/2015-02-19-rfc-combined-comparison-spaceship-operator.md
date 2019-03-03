---
id: 142
title: 'RFC: Combined Comparison (Spaceship) Operator'
date: 2015-02-19T08:30:32+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=142
permalink: /2015/02/19/rfc-combined-comparison-spaceship-operator/
categories:
  - Non classé
---
Voici un autre sujet qui avait été discuté il y a quelques temps et qui est revenu en avant dernièrement, profitant certainement de l&rsquo;approche de PHP 7, avec une mise à jour de la RFC au passage : **Combined Comparison (Spaceship) Operator**.

  * URL : <https://wiki.php.net/rfc/combined-comparison-operator>
  * Version cible : PHP 7

Cette RFC proposait d&rsquo;ajouter un nouvel opérateur `<=>` de comparaison combinée &#8212; opérateur fréquemment appelé _spaceship operator_, de par sa forme. Cet opérateur, sur le modèle déjà utilisé pour des fonctions de comparaison comme `strcmp()`, retournerait trois valeurs :

  * `` si les deux opérandes sont égaux,
  * `1` si l&rsquo;opérande de gauche est plus grand que celui de droite
  * `-1` si l&rsquo;opérande de gauche est plus petit que celui de droite.

Il fonctionnerait sur tous les types de données génériques de PHP, en suivant les règles déjà en place pour `<`, `>` et `==`.

Toute [une série d&rsquo;exemples est donnée dans la RFC](https://wiki.php.net/rfc/combined-comparison-operator#proposal), que ce soit pour des comparaison simples, des comparaisons un peu plus avancées, ou un usage avec des fonctions dépendant d&rsquo;un tri utilisateur (cet opérateur simplifierait souvent l&rsquo;écriture des fonctions de comparaison utilisées par ces fonctions).

Voici cependant un exemple basique :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    // Integers
    echo 1 <=> 1; // 0
    echo 1 <=> 2; // -1
    echo 2 <=> 1; // 1

[/pastacode]

Les votes ont été ouverts le 02 février 2015 pour être clôturés le 16 février 2015 et [nous avons exprimé notre avis positif sur `internals@`](http://news.php.net/php.internals/82758).  
Cette proposition a été acceptée avec 43 votes _pour_ et 11 votes _contre_.