# New-SA-MP-callbacks

[![sampctl](https://img.shields.io/badge/sampctl-New--SA--MP--callbacks-2f2f2f.svg?style=for-the-badge)](https://github.com/Luxinity-Roleplay/New-SA-MP-callbacks)

<!--
Short description of your library, why it's useful, some examples, pictures or
videos. Link to your forum release thread too.

Remember: You can use "forumfmt" to convert this readme to forum BBCode!

What the sections below should be used for:

`## Installation`: Leave this section un-edited unless you have some specific
additional installation procedure.

`## Testing`: Whether your library is tested with a simple `main()` and `print`,
unit-tested, or demonstrated via prompting the player to connect, you should
include some basic information for users to try out your code in some way.

And finally, maintaining your version number`:

* Follow [Semantic Versioning](https://semver.org/)
* When you release a new version, update `VERSION` and `git tag` it
* Versioning is important for sampctl to use the version control features

Happy Pawning!
-->

## Installation

Simply install to your project:

```bash
sampctl package install Abielfrl/New-SA-MP-callbacks
```

Include in your code and begin using the library:

```pawn
#include <callbacks>
```

## List of Callbacks
The following callbacks are included with this library:
```
// Called when a player pauses their game.
forward OnPlayerPause(playerid);
// Called when a player resumes their game.
forward OnPlayerResume(playerid, time);
// Called when a player starts holding a key.
forward OnPlayerHoldingKey(playerid, keys);
// Called when a player releases a key.
forward OnPlayerReleaseKey(playerid, keys, time);
// Called when a player falls and loses damage.
forward OnPlayerFall(playerid, Float:damage);
// Called when a player experiences packet loss.
forward OnPlayerPacketLoss(playerid, Float:oldloss, Float:newloss);
// Called when a player crashes their vehicle.
forward OnPlayerCrashVehicle(playerid, vehicleid, Float:damage);
// Called when a player uses a vending machine.
forward OnPlayerUseVending(playerid);
// Called when a player's FPS change.
forward OnPlayerFPSChange(playerid, oldfps, newfps);
// Called when a player jacks another player's vehicle.
forward OnPlayerJackVehicle(playerid, targetid, vehicleid);
// Called when a player completely uses up all ammo in their weapon.
forward OnPlayerEmptyWeapon(playerid, weaponid);
// Called when a player shoots another player in their team.
forward OnPlayerFriendlyFire(playerid, targetid, weaponid);
// Called when a player aims at another player.
forward OnPlayerTargetPlayer(playerid, targetid, weaponid);
// Called when a player explicitly disables textdraw selection mode.
forward OnPlayerHideCursor(playerid, hovercolor);
// Called when a player shoots more ammo than their weapon's clip can hold.
forward OnPlayerAntiReload(playerid, weaponid);
// Called when an animation is finished.
forward OnPlayerAnimationPlay(playerid, animlib[], animname[]);
// Called when a player is reloading their weapon.
forward OnPlayerReloadWeapon(playerid, weaponid, ammo);
// Called when a player starts or stops burning from fire.
forward OnPlayerBurn(playerid, status);
// Called when a player starts or stops aiming a weapon.
forward OnPlayerAiming(playerid, weaponid, status);
// Called when a player's action changes.
forward OnPlayerActionChange(playerid, oldaction, newaction);
// Called when a player rams another player.
forward OnPlayerRamPlayer(playerid, driverid, vehicleid, Float:damage);
// Called when a player uses a camera to take a picture.
forward OnPlayerUseCamera(playerid);
// Called when a player sprays a spraycan towards a vehicle.
forward OnPlayerSprayAtVehicle(playerid, vehicleid);
// Called when a player jumps by pressing the jump key.
forward OnPlayerJump(playerid);
// Called when a player starts or stops sprinting.
forward OnPlayerSprint(playerid, status);
```
## Functions
External functions for this library:
```
// Returns 1 if the player is paused.
stock IsPlayerPaused(playerid);
// Returns 1 if the player is holding the key.
stock IsPlayerHoldingKey(playerid, keys);
// Returns 1 if the player is skydiving.
stock IsPlayerSkydiving(playerid);
// Returns 1 if the player is swimming.
stock IsPlayerSwimming(playerid);
// Returns 1 if the player is burning.
stock IsPlayerBurning(playerid);
// Returns 1 if the player is aiming.
stock IsPlayerAiming(playerid);
// Returns 1 if the player is jumping.
stock IsPlayerJumping(playerid);
// Returns 1 if the player is sprinting.
stock IsPlayerSprinting(playerid);
// Returns 1 if the player is near any vending machine.
stock IsPlayerNearVending(playerid);
// Returns 1 if the player is spraying at a vehicle with a spraycan.
stock IsPlayerSprayingVehicle(playerid, vehicleid);
// Returns the player's action.
stock GetPlayerAction(playerid);
// Returns the player's packet loss.
stock Float:GetPlayerPacketLoss(playerid);
// Returns the time that the player has been paused.
stock GetPlayerPausedTime(playerid);
// Returns the player's FPS amount.
stock GetPlayerFPS(playerid);
```
## Example
```
public OnPlayerResume(playerid, time)
{
    new
        str[48];
    format(str, sizeof(str), "You've been paused for %d milliseconds.", time);
    return SendClientMessage(playerid, -1, str);
}
public OnPlayerCrashVehicle(playerid, vehicleid, Float:damage)
{ 
    SendClientMessage(playerid, 0xFF0000FF, "You have crashed your vehicle!");
    SendClientMessage(playerid, 0xFF0000FF, "Learn how to drive, please!");
    return 1;
}
