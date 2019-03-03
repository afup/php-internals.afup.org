---
id: 138
title: 'RFC: Removal of dead or not yet PHP7 ported SAPIs and extensions'
date: 2015-02-12T08:30:34+00:00
author: Jean Molliné
layout: post
guid: http://php-internals.afup.org/?p=138
permalink: /2015/02/12/rfc-removal-of-dead-or-not-yet-php7-ported-sapis-and-extensions/
categories:
  - Non classé
---
[Cette RFC](https://wiki.php.net/rfc/removal_of_dead_sapis_and_exts) n&rsquo;a pas été énormément discutée sur `internals@`, ni sur notre mailing-list au départ, d&rsquo;ailleurs&#8230; Ce qui signifie généralement que tout le monde est à peu près d&rsquo;accord.

  * URL :  [https://wiki.php.net/rfc/removal\_of\_dead\_sapis\_and_exts](https://wiki.php.net/rfc/removal_of_dead_sapis_and_exts)
  * Version cible : PHP 7

L&rsquo;objectif de cette RFC était de supprimer de l&rsquo;arbre de code de PHP :

  * Les SAPIs (les &laquo;&nbsp;modules&nbsp;&raquo; qui permettent, typiquement, de brancher PHP au sein d&rsquo;un serveur Web) qui ne sont plus maintenues et probablement très peu utilisées
  * Des extensions qui ne sont plus maintenues (ou dont les dépendances ne le sont plus), éventuellement en les déplaçant vers PECL pour ceux qui en auraient encore besoin (à eux de les porter vers PHP 7, a priori)

Ceux qui portent cette RFC ont tenté de joindre les mainteneurs des extensions qui ne sont plus maintenues. Suite à quelques retours, quelques extensions ont été sauvées (la SAPI `nsapi` et l&rsquo;extension `interbase`, par exemple).

La RFC s&rsquo;est orientée sur un vote pour chacune des SAPIs (50% +1 pour supprimer) suivantes : `sapi/aolserver`, `sapi/apache`, `sapi/apache_hooks`, `sapi/apache2filter`, `sapi/caudium`, `sapi/continuity`, `sapi/isapi`, `sapi/milter`, `sapi/phttpd`, `sapi/pi3web`, `sapi/roxen`, `sapi/thttpd`, `sapi/tux` et `sapi/webjames`.

Et sur un vote pour chaque extension (50% +1 pour supprimer de PHP &#8212; quitte, éventuellement, à déplacer vers PECL si quelqu&rsquo;un s&rsquo;en charge) suivantes :

  * `ext/imap`
  * `ext/mcrypt`
  * `ext/mssql`
  * `ext/pdo_dblib`
  * `ext/sybase_ct`

Les votes ont été ouverts le 02 février 2015 pour être clôturés le 09 février 2015 et [nous avons indiqué sur `internals@`](http://news.php.net/php.internals/82296) être pour la suppression de la quasi-totalité des points listés.  
Les résultats sont les suivants :

<table summary="Résultat des votes">
  <tr>
    <th>
      SAPI
    </th>
    
    <th>
      Supprimer
    </th>
    
    <th>
      Conserver
    </th>
    
    <th>
      Résultat
    </th>
  </tr>
  
  <tr>
    <td>
      <code>sapi/aolserver</code>
    </td>
    
    <td>
      31
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/apache</code>
    </td>
    
    <td>
      32
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/apache_hooks</code>
    </td>
    
    <td>
      31
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/apache2filter</code>
    </td>
    
    <td>
      23
    </td>
    
    <td>
      1
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/caudium</code>
    </td>
    
    <td>
      30
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/continuity</code>
    </td>
    
    <td>
      28
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/isapi</code>
    </td>
    
    <td>
      28
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/milter</code>
    </td>
    
    <td>
      10
    </td>
    
    <td>
      9
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/phttpd</code>
    </td>
    
    <td>
      26
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/pi3web</code>
    </td>
    
    <td>
      24
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/roxen</code>
    </td>
    
    <td>
      23
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/thttpd</code>
    </td>
    
    <td>
      25
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/tux</code>
    </td>
    
    <td>
      25
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>sapi/webjames</code>
    </td>
    
    <td>
      25
    </td>
    
    <td>
    </td>
    
    <td style="background-color: #afa">
      SAPI supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ext/imap</code>
    </td>
    
    <td>
      14
    </td>
    
    <td>
      19
    </td>
    
    <td style="background-color: #fcc">
      Extension conservée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ext/mcrypt</code>
    </td>
    
    <td>
      15
    </td>
    
    <td>
      18
    </td>
    
    <td style="background-color: #fcc">
      Extension conservée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ext/pdo_oci</code> et ext/oci8
    </td>
    
    <td>
      n/a
    </td>
    
    <td>
      n/a
    </td>
    
    <td>
      Retiré du vote *
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ext/mssql</code>
    </td>
    
    <td>
      17
    </td>
    
    <td>
      3
    </td>
    
    <td style="background-color: #afa">
      Extension supprimée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ext/pdo_dblib</code>
    </td>
    
    <td>
      4
    </td>
    
    <td>
      18
    </td>
    
    <td style="background-color: #fcc">
      Extension conservée
    </td>
  </tr>
  
  <tr>
    <td>
      <code>ext/sybase_ct</code>
    </td>
    
    <td>
      17
    </td>
    
    <td>
      1
    </td>
    
    <td style="background-color: #afa">
      Extension supprimée
    </td>
  </tr>
</table>

_ (*) Les extensions `ext/pdo_oci` et `ext/oci8` ont été retirées du vote, Oracle prévoyant d&rsquo;en assurer la maintenance dans le futur._