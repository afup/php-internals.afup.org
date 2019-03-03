---
id: 47
title: 'RFC: Filtered unserialize()'
date: 2015-01-21T08:30:21+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=47
permalink: /2015/01/21/rfc-filtered-unserialize/
categories:
  - Non classé
---
[Cette RFC](https://wiki.php.net/rfc/secure_unserialize) partait de l&rsquo;idée que la dé-sérialisation de données n&rsquo;est pas sûre, puisqu&rsquo;il est, dans certains cas, possible d&rsquo;injecter du code qui pourrait être automatiquement exécuté (par le destructeur de classe, par exemple) &#8212; bien sûr, cela suppose qu&rsquo;on essaye de dé-sérialiser des données provenant d&rsquo;une source non réellement sûre (ce que font probablement certaines applications).

Elle proposait donc de modifier la fonction `unserialize()` de PHP pour permettre d&rsquo;interdire la dé-sérialisation d&rsquo;objets ou de limiter celle-ci à un ensemble de classes listées.

Dans le cas où on essayerait de dé-sérialiser un objet non autorisé, on obtiendrait en retour une instance de classe incomplète, comme lorsqu&rsquo;on essaye de dé-sérialiser un objet dont la classe n&rsquo;existe pas.

Exemples :

<pre class="php code php" style="padding-left: 30px"><span class="sy0"><span style="color: #99cc00"><em>// ceci va tout dé-sérialiser comme auparavant</em></span>
$data = <strong>unserialize</strong>($foo);
<span style="color: #99cc00"><em>// Ceci va convertir tous les objets en objets __PHP_Incomplete_Class</em></span>
$data = <strong>unserialize</strong>($foo, ["<em>allowed_classes</em>" =&gt; false]);
<span style="color: #99cc00"><em>// Ceci va convertir tous les objets à l'exception des instances de MyClass et de MyClass2 en objets __PHP_Incomplete_Class</em></span>
$data = <strong>unserialize</strong>($foo, ["<em>allowed_classes</em>" =&gt; ["<em>MyClass</em>", "<em>MyClass2</em>"]);
<span style="color: #99cc00"><em>// Ceci va accepter toutes les classes comme étant par défaut</em></span>
$data = <strong>unserialize</strong>($foo, ["<em>allowed_classes</em>" =&gt; true]);</span></pre>

Les votes ont été ouverts le 3 novembre 2014 et ont été clos le 10 novembre 2014. Considérant qu&rsquo;apporter un niveau de sécurité lors de la dé-sérialisation de données ne pouvait être que bénéfique, [nous avons posté en ce sens sur `internals@`](http://news.php.net/php.internals/78859).  
Cette RFC a été adoptée par 17 votes contre 6.