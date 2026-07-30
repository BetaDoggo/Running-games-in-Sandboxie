# Running-games-in-Sandboxie
My ongoing personal documentation for more complex issues encountered while running games in Sandboxie sandboxes. If this document helps you solve a problem with one of your games please open an issue (or contact me on discord if you know where) about the game so that I can add it to the "Effected Games" section of each fix. Reported instances will include an asterisk since I can't easily verify them myself.

# Common Issues:
## A game gets "stuck", either loading forever or outright crashing when networking is blocked, but works when networking is allowed, even when not connected to the internet.
This is caused by sandboxie's default network blocking. Add `NetworkEnableWFP=y` to the [Global] section of your sandboxie.ini, then toggle network blocking on and off for the sandbox in sandman to make sure that the change applies. The sandbox's .ini should have the line `AllowNetworkAccess=!<InternetAccess>,n`, and should **NOT** have a line like `ClosedFilePath=!<InternetAccess>,InternetAccessDevices` (this line is from the old blocking method).

Effected games: Baldur's Gate 3

# Obscure issues:
## Prerendered cinematics/cutscenes don't play or cause a crash.
In the cases I've seen this has been due to a failure to access codec packs (usually vp9) installed via the windows store. This is the most complicated issue I've encountered so far. The fix requires some custom dlls to route the game to a copy of the codec that it can actually access. See my repo here: https://github.com/BetaDoggo/Sandboxie-VP9-Workaround. Because of how specific this issue is it might not work on every game, even if the root issue is the same. I haven't done extensive testing with many games since finding examples (especially in my library) is hard.

Effected Games: Returnal
