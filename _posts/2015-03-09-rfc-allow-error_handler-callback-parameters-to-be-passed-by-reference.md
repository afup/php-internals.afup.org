---
id: 204
title: 'RFC: Allow error_handler callback parameters to be passed by reference'
date: 2015-03-09T08:30:30+00:00
author: Guillaume
layout: post
guid: http://php-internals.afup.org/?p=204
permalink: /2015/03/09/rfc-allow-error_handler-callback-parameters-to-be-passed-by-reference/
categories:
  - Non classé
---
La [RFC: Allow error_handler callback parameters to be passed by reference](https://wiki.php.net/rfc/error_handler_callback_parameters_passed_by_reference) avait pour objectif de permettre aux gestionnaires d&rsquo;erreurs configurés via `set_error_handler()` de modifier les informations de l&rsquo;erreur gérée, en passant ses valeurs par référence.

L&rsquo;objectif était de pouvoir y passer des informations contextuelles de type identifiant stocké en session, URL parcourue lors de l&rsquo;erreur, etc. de la manière suivante:

[pastacode lang=&nbsp;&raquo;php&nbsp;&raquo; message=&nbsp;&raquo;&nbsp;&raquo; highlight=&nbsp;&raquo;&nbsp;&raquo; provider=&nbsp;&raquo;manual&nbsp;&raquo;]

    $_SESSION[&#039;username&#039;] = &#039;john&#039;;
     
    function myErrorHandler($errno, &$errstr, $errfile, $errline)
    {
      if (isset($_SESSION[&#039;username&#039;])) {
        $errstr .= &#039;, username: &#039;.$_SESSION[&#039;username&#039;];
      }
      return false; // continue normal error handler
    }
     
    set_error_handler(&#039;myErrorHandler&#039;);

[/pastacode]

La RFC n&rsquo;a pas convaincu et nos avis furent tous négatifs, principalement dû au fait que cette gestion pouvait être très facilement déléguée à la fonction utilisateur sans forcément avoir recours à des paramètres passés par référence. Nous avons donc posté en ce sens sur [internals@](http://news.php.net/php.internals/84028).

La RFC proposait deux choix possibles : passer uniquement le message d&rsquo;erreur par référence, ou bien l&rsquo;ensemble des paramètres. Quoi qu&rsquo;il en soit, avec 19 voix contre et 4 pour, la RFC a été rejetée.