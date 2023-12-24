Group skript with easily addable groups.
```
options:
	Spectator: {Spectators::*}
	Survivor: {Survivors::*}
	NonSurvivor: {NonSurvivors::*}

on join:
	if player has permission "sk.staff":
		add player to {@NonSurvivor}
	else:
		add player to {@Survivor}

command "changegroup" <text>:	
	trigger:
		remove player from {@Spectator}
		remove player from {@Survivor}
		remove player from {@NonSurvivor}
		if arg-1 is "Spectator":
			add player to {@Spectator}
		else if arg-1 is "Survivor":
			add player to {@Survivor}
		else if arg-1 is "NonSurvivor":
			add player to {@NonSurvivor}
		else:
			send "&cIncorrect argument. Assigned to Survivors."
			add player to {@Survivor}

every 30 seconds:
	loop {@Survivor}:
		teleport loop-value to {warps::arena}
	loop {@Spectator}:
		teleport loop-value to {warps::spectate}
```
