---
description: This page describes how to use the NodeJS package.
---

# NodeJS

### Set up your NodeJS environment

This small guide assumes you're already familiar with NodeJS environment.

The first step is to install the [oakwood](https://github.com/MafiaHub/oakwood-node) package via npm.

Afterwards, we need to create our resource script we plan to start in `node`:

```javascript
const {createClient} = require('oakwood')
const oak = createClient()

oak.event('start', async () => {
    console.log("[info] connected to the server")
    oak.log("[info] hello world from nodejs")
})

oak.event('player_connect', async pid => {
    console.log('[info] player connected', pid)

    oak.player_position_set(pid, [-1774.59301758, -4.88487052917, -2.40491962433])
    oak.player_health_set(pid, 200)
    oak.player_spawn(pid)
})

oak.cmd('goto', async (pid, targetid) => {
    const tid = parseInt(targetid)

    if (tid === NaN) {
        return oak.chat_send(pid, `[error] provided argument should be a valid number`)
    }

    if (await oak.player_invalid(tid)) {
        return oak.chat_send(pid, `[error] player you provided was not found`)
    }

    /* get target position */
    const pos = await oak.player_position_get(tid)

    /* set our player position */
    oak.player_position_set(pid, pos)
})
```

You can look up the [example code](https://github.com/MafiaHub/oakwood-node/example.js) to see how to use the package.

### Things to note

All public API calls are asynchronous due to the nature of the communication. However, you can `await` the response of the call if you expect a return value.

