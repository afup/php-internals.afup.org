---
id: 231
title: 'RFC: Context Sensitive Lexer'
date: 2015-03-24T08:30:58+00:00
author: Guillaume
layout: post
guid: http://php-internals.afup.org/?p=231
permalink: /2015/03/24/rfc-context-sensitive-lexer/
categories:
  - Non classé
---
La [RFC: Context Sensitive Lexer](https://wiki.php.net/rfc/context_sensitive_lexer) partait du constat qu&rsquo;il existe actuellement [64 mots clefs réservés](http://php.net/manual/fr/reserved.keywords.php) par PHP et que certains d&rsquo;entre eux seraient très utiles en tant que noms de méthodes, pour définir des API claires côté utilisateur.

Elle proposait donc de modifier l&rsquo;analyse du code PHP afin de disposer d&rsquo;une analyse lexicale sensible au contexte, permettant l&rsquo;utilisation de mots clefs ; en se limitant pour l&rsquo;instant au périmètre de la programmation objet :

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    // Le code suivant devient possible:
    interface Collection
    {
        public function forEach(callable $callback);
    
        public function list();
    }
    
    // Mais pas le suivant:
    function list() {/* */}

[/pastacode]

De plus, cette RFC permettrait également de limiter les problèmes de rétro-compatibilité à l&rsquo;avenir, lorsque PHP réservera de nouveaux mots clefs.

Considérant que pouvoir utiliser des mots-clefs comme noms de classes ou de méthodes était intéressant, nous avons (à l&rsquo;unanimité&nbsp;!) [posté en ce sens sur internals@](http://news.php.net/php.internals/84734).  
Cette RFC a été acceptée pour PHP 7.0, avec 36 votes &laquo;&nbsp;pour&nbsp;&raquo; et 12 votes &laquo;&nbsp;contre&nbsp;&raquo;.

&nbsp;

&nbsp;