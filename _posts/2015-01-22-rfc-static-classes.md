---
id: 55
title: 'RFC: Static classes'
date: 2015-01-22T08:30:22+00:00
author: Guillaume
layout: post
guid: http://php-internals.afup.org/?p=55
permalink: /2015/01/22/rfc-static-classes/
categories:
  - Non classé
---
La RFC [Static classes](https://wiki.php.net/rfc/abstract_final_class) partait du constat qu&rsquo;il est aujourd&rsquo;hui possible de créer des classes avec propriétés et méthodes statiques uniquement, mais qu&rsquo;il est impossible de les définir comme non instanciables sans passer par un constructeur privé, ce qui rend notamment ces classes non testable.

Le but de cette RFC était d&rsquo;ajouter un mot clef `static` au niveau de la classe afin de définir l&rsquo;intégralité de son comportement comme tel :

<pre><span style="color: #339966"><strong>static class</strong></span> Environment
{
    <span style="color: #339966"><strong>private</strong></span> <strong>$rootDirectory</strong> = '<em>/var/www/project</em>';
    <strong><span style="color: #339966">public</span> <span style="color: #339966">function</span></strong> getRootDirectory()
    {
        <span style="color: #339966"><strong>return</strong> <strong>self</strong></span>::<strong>$rootDirectory</strong>;
    }
}</pre>

Notons toutefois qu&rsquo;aujourd&rsquo;hui, un tel comportement est presque possible en utilisant une classe abstraite :

<pre><span style="color: #339966"><strong>abstract class</strong></span> Environment
{
    <span style="color: #339966"><strong>static private</strong></span> <strong>$rootDirectory</strong> = '<em>/var/www/project</em>';
    <span style="color: #339966"><strong>static public function</strong></span> getRootDirectory()
    {
        <span style="color: #339966"><strong>return self</strong></span>::<strong>$rootDirectory</strong>;
    }
}</pre>

Néanmoins, cette syntaxe présente plusieurs limites que la RFC souhaitait couvrir :

  * il est possible d&rsquo;oublier un mot-clef `static<br />
` 
  * la classe peut être étendue et donc instanciée par le biais d&rsquo;une classe fille, la rendant non statique : il faudrait y ajouter le mot clef `final`.

C&rsquo;est pour cette raison que la RFC fut lancée sous le nom de **Abstract Final class.** Le but premier était de donner la possibilité de rendre une classe abstraite finale.

Le principe fut rejeté car une classe abstraite a pour but même d&rsquo;être étendue alors qu&rsquo;une classe finale ne peut pas l&rsquo;être !  
C&rsquo;est pour cette raison qu&rsquo;après moult échanges en interne, la RFC fut proposée une nouvelle fois sous son nouveau nom, afin d&rsquo;ajouter un nouveau mot clef pour lever toute incompréhension.

S&rsquo;il est vrai que définir une classe comme statique dès sa déclaration à l&rsquo;avantage indéniable de clarifier son rôle, il est toutefois ressorti de nos échanges qu&rsquo;il semblerait que la plupart des cas d&rsquo;utilisation étaient des collections de fonctions, parfois appelées _helpers_. La majorité fut contre cette demande, principalement car les classes statiques ne sont pas reconnues comme une pratique à encourager. Nous avons donc posté en ce sens sur [`internals@`](http://news.php.net/php.internals/79809).

La RFC a été rejetée par 12 voix contre 5. Toutefois,  même si cette proposition voulait couvrir un périmètre plus large, le [chargement automatique des fonctions](https://wiki.php.net/rfc/function_autoloading) est un sujet qui est ressorti plusieurs fois au cours de nos discussions. Un souhait visiblement partagé par de nombreux développeurs.