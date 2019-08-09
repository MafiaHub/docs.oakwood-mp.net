---
description: This page describes the player API
---

# Player

## Spawn

`player_spawn(player)` 

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
oak.event('player_connect', async pid => {
    console.log('[info] player connected', pid)

    oak.player_position_set(pid, [-1774.59301758, -4.88487052917, -2.40491962433])
    oak.player_health_set(pid, 200)
    oak.player_spawn(pid)
})
```
{% endtab %}
{% endtabs %}

## ​Despawn

`player_despawn(player)` 

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
    oak.player_despawn(pid)
})
```
{% endtab %}
{% endtabs %}

## Invalid

`player_invalid(player)` 

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
    if (await oak.player_invalid(pid)) {
        oak.log('Not happy ;1')
        return
    }
    
    oak.player_despawn(pid)
})
```
{% endtab %}
{% endtabs %}

## Kick

`player_kick(player, string)` 

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
|  |  |

#### Returns

0 if successful, -1 if failed
{% endtab %}

{% tab title="Example" %}
```javascript
oak.cmd('kickme', async pid => {
    oak.player_kick(pid, 'You were a bad boy!')
})
```
{% endtab %}
{% endtabs %}

## Kill

`player_kill(player)` 

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
    oak.player_kill(pid)
})
```
{% endtab %}
{% endtabs %}

## Play anim

`player_despawn(player, string)` 

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

`player_model_set(player, string)` 

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
    oak.player_model_set(pid, 'Tommy')
})
```
{% endtab %}
{% endtabs %}

## Set health

`player_health_set(player, float)` 

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
    oak.player_health_set(pid, 200)
})
```
{% endtab %}
{% endtabs %}

## Set position

`player_position_set(player, vec3)` 

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
    
    oak.player_position_set(pid, [x, y, z])
})
```
{% endtab %}
{% endtabs %}

## Set direction

`player_direction_set(player, vec3)` 

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
    
    oak.player_direction_set(pid, [x, y, z])
})
```
{% endtab %}
{% endtabs %}

## Set heading

`player_heading_set(player, float)` 

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
    oak.player_heading_set(pid, parseFloat(angle))
})
```
{% endtab %}
{% endtabs %}

## Get name

`player_name_get(player)` 

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
    const name = await oak.player_name_get(pid)
    oak.chat_broadcast('Guess who is back: ' + name)
})
```
{% endtab %}
{% endtabs %}

## Get model

`player_model_get(player)` 

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

`player_health_get(player)` 

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
    const hp = parseFloat(await oak.player_health_get(pid))
    oak.chat_send('Current HP: ' + hp)
})
```
{% endtab %}
{% endtabs %}

## Get heading

`player_heading_get(player)` 

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

`player_position_get(player)` 

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
    const pos = await oak.player_position_get(pid)
    oak.chat_send(pid, 'My position: ' + pos)
})
```
{% endtab %}
{% endtabs %}

## Get direction

`player_direction_get(player)` 

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

`player_visibility_get(player, visibility_type)` 

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

`player_visibility_set(player, visibility_type, int)` 

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

