---
title: GetPlayerAnimFlags
description: Get the player animation flags.
tags: ["player", "animation"]
---

<VersionWarn version='omp v1.1.0.2612' />

## Description

Get the player animation flags.

| Name     | Description                              |
| -------- | ---------------------------------------- |
| playerid | The player id you want to get the animation flags from |

## Returns

Returns the player animation flags as integer.

## Examples

In order to get each flag separately, bit masking is used.

```c
public OnPlayerCommandText(playerid, cmdtext[])
{
    if (!strcmp(cmdtext, "/myanimflags"))
    {
        new messageString[128];
        new flags = GetPlayerAnimFlags(playerid);

        new bool:freeze  =   (flags & ANIME_FREEZE_FLAG) != 0 ? true : false;
        new bool:lockx   =   (flags & ANIME_LOCK_X_FLAG) != 0 ? true : false;
        new bool:locky   =   (flags & ANIME_LOCK_Y_FLAG) != 0 ? true : false;
        new bool:loop    =   (flags & ANIM_LOOP_FLAG) != 0 ? true : false;

        format(messageString, sizeof(messageString), "You anim flags are: [freeze:%i] [lockx:%i] [locky:%i] [loop:%i]", freeze, lockx, locky, loop);
        SendClientMessage(playerid, -1, messageString);

        return 1;
    }

    return 0;
}
```

:::warning

If the player is in a vehicle, all returned flags will be 0.

:::

## Related Functions

- [ApplyAnimation](ApplyAnimation): Apply an animation to a player.
