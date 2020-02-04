# Comment configurer son git pour qu'il fonctionne avec webstorm:

1. ouvrir le terminal <br/>
<strong><em>really important! à faire qu'une seule fois</em></strong>

2. Google taper git set usernam and password ->site atlassian

3. prendre     ` git config --global user.name "farid djadda" `

4. file -> settings -> pluggins gitlab install et redemarrer webstorm

5. Add new gitlab server, 3 infos à mettre <br/>
+ premiere ligne :https://gitlab.com
+ deuxieme ligne :gitlab.com
+ troisième ligne :mettre son Token d'ID <br/>
<strong><em>really important! bien cacher son Token </em></strong>

#### comment reccuperer son Token :

cliquer sur Token page -> connexion gitlab ->

+ donner un name :Webstorm
+ mettre une date d'expiration 
+ Scopes cocher `api`
+ cliquer sur create personnal access token <br/>
<strong><em>really important! ne quitter pas la page ,le Token n'est disponible qu'une seule fois </em></strong>