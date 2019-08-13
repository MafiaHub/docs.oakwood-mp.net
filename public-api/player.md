---
description: This page describes the player API
---

# Player

## Spawn

`playerSpawn(player)` 

Spawns the player.

{% tabs %}
{% tab title="Details" %}
#### Remarks

Subsequent calls will re-spawn the player.

Make sure you set health to a valid value, since Spawn method doesn't take care of that.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
oak.event('playerConnect', async pid => {
    console.log('[info] player connected', pid)

    oak.playerPositionSet(pid, [-1774.59301758, -4.88487052917, -2.40491962433])
    oak.playerHealthSet(pid, 200)
    oak.playerSpawn(pid)
})
```
{% endtab %}
{% endtabs %}

## ​Despawn

`playerDespawn(player)` 

Removes the player from the map.

{% tabs %}
{% tab title="Details" %}
#### Remarks

Useful when you want to create a spectator mode in your game.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('spectator', async pid => {
    oak.playerDespawn(pid)
})
```
{% endtab %}
{% endtabs %}

## Invalid

`playerInvalid(player)` 

Checks whether the player ID is invalid.

{% tabs %}
{% tab title="Details" %}
#### Remarks

None.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns

0 if invalid
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('respawn', async pid => {
    if (await oak.playerInvalid(pid)) {
        oak.log('Not happy ;1')
        return
    }

    oak.playerDespawn(pid)
})
```
{% endtab %}
{% endtabs %}

## Kick

`playerKick(player, string)` 

Kicks the player from the game.

{% tabs %}
{% tab title="Details" %}
#### Remarks

Useful when you want to create a spectator mode in your game.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| string | Reason |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('kickme', async pid => {
    oak.playerKick(pid, 'You were a bad boy!')
})
```
{% endtab %}
{% endtabs %}

## Kill

`playerKill(player)` 

Force kills the player.

{% tabs %}
{% tab title="Details" %}
#### Remarks

Kills the player naturally.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('suicide', async pid => {
    oak.playerKill(pid)
})
```
{% endtab %}
{% endtabs %}

## Play anim

`playerDespawn(player, string)` 

Removes the player from the map.

{% tabs %}
{% tab title="Details" %}
#### Remarks

There is no animation list provided, search game folder for possible animation names.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| string | Animation file name |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Set model

`playerModelSet(player, string)` 

Changes the player model.

{% tabs %}
{% tab title="Details" %}
#### Remarks

You can use models from the [following](../assets/asset-player-models.md) listing.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| string | Model name |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('tommy', async pid => {
    oak.playerModelSet(pid, 'Tommy')
})
```
{% endtab %}
{% endtabs %}

## Set health

`playerHealthSet(player, float)` 

Sets the player health.

{% tabs %}
{% tab title="Details" %}
#### Remarks

{% hint style="warning" %}
At the moment, this method expects a raw value the game uses to specify health. Maximum health is based off of the mission data, so some maps use value 200, while others can be over 600.

We will make sure health is uniform on the server-side, but right now, you need to set health to 200 if you want full health on freeride map.
{% endhint %}

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| float | Health value |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('healme', async pid => {
    oak.playerHealthSet(pid, 200)
})
```
{% endtab %}
{% endtabs %}

## Set position

`playerPositionSet(player, vec3)` 

Sets the player position.

{% tabs %}
{% tab title="Details" %}
#### Remarks

None.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| vec3 | Array of 3 float values |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('setpos', async (pid, _x, _y, _z) => {
    const x = parseFloat(_x)
    const y = parseFloat(_y)
    const z = parseFloat(_z)

    oak.playerPositionSet(pid, [x, y, z])
})
```
{% endtab %}
{% endtabs %}

## Set direction

`playerDirectionSet(player, vec3)` 

Sets the player's forward direction vector.

{% tabs %}
{% tab title="Details" %}
#### Remarks

None.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| vec3 | Array of 3 float values |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('setdir', async (pid, _x, _y, _z) => {
    const x = parseFloat(_x)
    const y = parseFloat(_y)
    const z = parseFloat(_z)

    oak.playerDirectionSet(pid, [x, y, z])
})
```
{% endtab %}
{% endtabs %}

## Set heading

`playerHeadingSet(player, float)` 

Sets the player heading angle.

{% tabs %}
{% tab title="Details" %}
#### Remarks

Uses a ±180 degree format.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| float | ±180 degree angle |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('rotateto', async (pid, angle) => {
    oak.playerHeadingSet(pid, parseFloat(angle))
})
```
{% endtab %}
{% endtabs %}

## Get name

`playerNameGet(player)` 

Retrieves the player name.

{% tabs %}
{% tab title="Details" %}
#### Remarks

None.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns

`string` player name
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('alert', async pid => {
    const name = await oak.playerNameGet(pid)
    oak.chat_broadcast('Guess who is back: ' + name)
})
```
{% endtab %}
{% endtabs %}

## Get model

`playerModelGet(player)` 

Retrieves the player's model.

{% tabs %}
{% tab title="Details" %}
#### Remarks

None.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns

`string` player model name
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Get health

`playerHealthGet(player)` 

Retrieves the current player's health.

{% tabs %}
{% tab title="Details" %}
#### Remarks

{% hint style="warning" %}
At the moment, this method returns a raw value the game uses to specify health. Maximum health is based off of the mission data, so some maps use value 200, while others can be over 600.

We will make sure health is uniform on the server-side, but right now, you need to be aware that full health differs per mission and freeride uses value of 200.
{% endhint %}

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns

`float` player health
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('printhp', async pid => {
    const hp = parseFloat(await oak.playerHealthGet(pid))
    oak.chat_send('Current HP: ' + hp)
})
```
{% endtab %}
{% endtabs %}

## Get heading

`playerHeadingGet(player)` 

Retrieves the player's heading angle.

{% tabs %}
{% tab title="Details" %}
#### Remarks

Uses a ±180 degree format.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns

`float` heading angle
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Get position

`playerPositionGet(player)` 

Retrieves the player position.

{% tabs %}
{% tab title="Details" %}
#### Remarks

None.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns

`vec3` array of 3 float values
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('getpos', async pid => {
    const pos = await oak.playerPositionGet(pid)
    oak.chat_send(pid, 'My position: ' + pos)
})
```
{% endtab %}
{% endtabs %}

## Get direction

`playerDirectionGet(player)` 

Retrieves the player direction.

{% tabs %}
{% tab title="Details" %}
#### Remarks

Retrieves the player's forward vector direction.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

#### Returns

`vec3` array of 3 float values
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

## Visibility

There are several visibility options you can set for the player:

| Name | Description |
| :--- | :--- |
| VISIBILITY\_NAME | Player nameplate visibility |
| VISIBILITY\_ICON | Player's blip visibility on the map |

### Get visibility

`playerVisibilityGet(player, visibility_type)` 

Retrieves the current player's visibility.

{% tabs %}
{% tab title="Details" %}
#### Remarks

None.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| visibility\_type | Visibility option |

#### Returns

`int` player visibility option value
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

### Set visibility

`playerVisibilitySet(player, visibility_type, int)` 

Sets the current player's visibility setting.

{% tabs %}
{% tab title="Details" %}
#### Remarks

None.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| visibility\_type | Visibility option |
| int | Visibility state |

#### Returns

0 if successful
{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}

