---
description: This page describes server-side events
---

# Events

## Gamemode start

`start()`

Gamemode start

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |

{% endtab %}

{% tab title="Example" %}
```javascript
oak.event('start', () => {
    console.log('[info] connection started')
    oak.log('[info] oakwood-node connected')
})
```
{% endtab %}
{% endtabs %}

## Unknown chat command

`unknownCommand(pid, text)`

Unknown chat command

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| string | Command Used |

{% endtab %}

{% tab title="Example" %}
```javascript
oak.event('unknownCommand', (pid, text) => {
    oak.chatSend(pid, `[error] unknown command: ${text}`)
})
```
{% endtab %}
{% endtabs %}

## Gamemode stop

`stop()`

Gamemode stop

{% tabs %}
{% tab title="Details" %}
#### Remarks

Happens when the server is shut down.

#### Arguments

| Type | Description |
| :--- | :--- |

{% endtab %}

{% tab title="Example" %}
```javascript
oak.event('start', () => {
    console.log('[info] connection stopped')
})
```
{% endtab %}
{% endtabs %}

## Player connect

`playerConnect(pid)`

Player connection

{% tabs %}
{% tab title="Details" %}
#### Remarks

Best place to spawn the player.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

{% endtab %}

{% tab title="Example" %}
```javascript
oak.event('playerConnect', async pid => {
    console.log('[info] player connected', pid)
    oak.chatBroadcast(`[info] player ${await oak.playerNameGet(pid)} connected.`)
    oak.playerModelSet(pid, "Tommy.i3d")
    oak.playerPositionSet(pid, [-1774.59301758, -4.88487052917, -2.40491962433 ])
    oak.playerHealthSet(pid, 200)
    oak.hudFadeout(pid, 1, 500, 0xFFFFFF)
    oak.hudFadeout(pid, 0, 500, 0xFFFFFF)
    oak.playerSpawn(pid)
})
```
{% endtab %}
{% endtabs %}

## Player disconnect

`playerDisconnect(pid)`

Player disconnection

{% tabs %}
{% tab title="Details" %}
#### Remarks

Happens when the player disconnects or times out.

{% hint style="warning" %}
    There's no way to find out if the player timed out as of right now. This will be added later on.
{% endhint %}

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

{% endtab %}

{% tab title="Example" %}
```javascript
oak.event('playerDisconnect', async pid => {
    oak.chatBroadcast(`[info] player ${await oak.playerNameGet(pid)} disconnected.`)
})
```
{% endtab %}
{% endtabs %}

## Player death

`playerDeath(pid)`

Player death

{% tabs %}
{% tab title="Details" %}
#### Remarks

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |

{% endtab %}

{% tab title="Example" %}
```javascript
oak.event('playerDeath', async pid => {
    oak.chatSend(pid, `[info] you died! Get a new life!`)
    oak.playerModelSet(pid, "Tommy.i3d")
    oak.playerPositionSet(pid, [-1774.59301758, -4.88487052917, -2.40491962433 ])
    oak.playerHealthSet(pid, 200)
    oak.hudFadeout(pid, 1, 500, 0xFFFFFF)
    oak.hudFadeout(pid, 0, 500, 0xFFFFFF)
    oak.playerSpawn(pid)
})
```
{% endtab %}
{% endtabs %}

## Player hit

`playerhit(pid, atkr, float)`

Player death

{% tabs %}
{% tab title="Details" %}
#### Remarks

Happens when attacker lands a hit on another player.

#### Arguments

| Type | Description |
| :--- | :--- |
| player | Player ID |
| player | Attacker ID |
| float | Damage Dealt |

{% endtab %}

{% tab title="Example" %}
```javascript
// TODO
```
{% endtab %}
{% endtabs %}


## Vehicle player use

`vehicleUse(veh, pid, success, seatId, enterOrLeave)`

Vehicle player use

{% tabs %}
{% tab title="Details" %}
#### Remarks

Success is true if car is unlocked, we can also provide which seat he wants to enter or
whether he wants to enter or leave the vehicle.

#### Arguments

| Type | Description |
| :--- | :--- |
| vehicle | Vehicle ID |
| player | Player ID |
| int | Success State |
| int | Seat ID |
| int | Enter or Leave State |

{% endtab %}

{% tab title="Example" %}
```javascript
oak.event("vehicleUse", async (veh, pid, success, seatId, enterOrLeave) => {
    if (success) return;

    oak.hudMessage(pid, "This vehicle is locked!", 0xff0000)
})
```
{% endtab %}
{% endtabs %}

