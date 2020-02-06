# Comment configurer son git pour qu'il fonctionne avec webstorm:

<strong><em>really important! à faire qu'une seule fois</em></strong>

:one: . ouvrir le terminal 

:two: . Google taper git set usernam and password ->site atlassian

:three: . prendre     ` git config --global user.name "farid djadda" `

:four: . file :arrow_right: settings :arrow_right: pluggins gitlab install et redemarrer webstorm

:five: . Add new gitlab server, 3 infos à mettre <br/>
+ premiere ligne :https://gitlab.com
+ deuxieme ligne :gitlab.com
+ troisième ligne :mettre son Token d'ID <br/>
<strong><em>really important! bien cacher son Token </em></strong>

#### comment reccuperer son Token :

cliquer sur Token page :arrow_right: connexion gitlab 

+ donner un name :arrow_right: Webstorm
+ mettre une date d'expiration 
+ Scopes cocher `api`
+ cliquer sur create personnal access token <br/>
<strong><em>really important! ne quitter pas la page ,le Token n'est disponible qu'une seule fois </em></strong>