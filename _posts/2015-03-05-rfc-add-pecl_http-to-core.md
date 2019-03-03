---
id: 206
title: 'RFC: Add pecl_http to core'
date: 2015-03-05T08:30:16+00:00
author: Guillaume
layout: post
guid: http://php-internals.afup.org/?p=206
permalink: /2015/03/05/rfc-add-pecl_http-to-core/
categories:
  - Non classé
---
La [RFC: Add `pecl_http` to core](https://wiki.php.net/rfc/pecl_http) avait pour objectif d&rsquo;intégrer nativement à PHP 7 l&rsquo;extension [`pecl_http`](http://devel-m6w6.rhcloud.com/mdref/http). Cette extension permet de gérer des communications HTTP grâce à une implémentation orientée objet.

Néanmoins, la présence de `curl` permettant l&rsquo;accès à la couche HTTP à bas-niveau ainsi que l&rsquo;existence de bibliothèques comme [Guzzle](https://github.com/guzzle/guzzle)  apportant une implémentation orientée objet (en espace utilisateur, donc non liée au cycle de versions et de maintenance de PHP) nous a paru suffisant en l&rsquo;état. De plus, l&rsquo;extension `pecl_http` embarquait des dépendances qui seraient venues s&rsquo;ajouter au cycle de maintenance de PHP. Nous avons donc [posté en ce sens sur `internals@`](http://news.php.net/php.internals/84030).

Avec 9 voix pour et 23 voix contre, cette RFC a finalement été refusée : l&rsquo;extension `pecl_http` restera disponible depuis PECL pour les intéressés, et ne sera pas distribuée avec PHP.