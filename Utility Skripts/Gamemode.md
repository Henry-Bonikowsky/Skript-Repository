### Gamemode skript including autofill:
```
options:
	p: &cPrefix &8» &f
	perm: &cError &8» &c

on tab complete of "/gmc" or "/gms" or "/gma" or "/gmsp":
	set tab completions for position 1 to all players

command gmc [<user:player>]:
	trigger:
		if player has permission "permission":
			if {_user} is set:
				setgamemode({_user}, "Creative", player)
			else:
				setgamemode(player, "Creative", player)
		else:
			nopermission(player, "permission")

command gms [<user:player>]:
	trigger:
		if player has permission "permission":
			if {_user} is set:
				setgamemode({_user}, "Survival", player)
			else:
				setgamemode(player, "Survival", player)
		else:
			nopermission(player, "permission")

command gma [<user:player>]:
	trigger:
		if player has permission "permission":
			if {_user} is set:
				setgamemode({_user}, "Adventure", player)
			else:
				setgamemode(player, "Adventure", player)
		else:
			nopermission(player, "permission")

command gmsp [<user:player>]:
	trigger:
		if player has permission "permission":
			if {_user} is set:
				setgamemode({_user}, "Spectator", player)
			else:
				setgamemode(player, "Spectator", player)
		else:
			nopermission(player, "permission")

function nopermission(p: player, perm: text):
	send "{@perm}You need the permission &e"%{_perm}%"&c to use this command!" to {_p}
	play sound "ENTITY_ENDERMAN_TELEPORT" with pitch -2 to {_p}

function setgamemode(p: player, g: text, u: player):
	set {_p}'s gamemode to {_g}
	send "{@p}Your gamemode was set to &e%{_g}%" to {_p}
	play sound "ENTITY_EXPERIENCE_ORB_PICKUP" with pitch 2 to {_p} and {_u}
	send "{@p}Set %{_p}%'s gamemode to &e%{_g}%" to {_u}
  ```
