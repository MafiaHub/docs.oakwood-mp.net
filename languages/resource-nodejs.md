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

oak.event('playerConnect', async pid => {
    console.log('[info] player connected', pid)

    oak.playerPositionSet(pid, [-1774.59301758, -4.88487052917, -2.40491962433])
    oak.playerHealthSet(pid, 200)
    oak.playerSpawn(pid)
})

oak.cmd('goto', async (pid, targetid) => {
    const tid = parseInt(targetid)

    if (tid === NaN) {
        return oak.chatSend(pid, `[error] provided argument should be a valid number`)
    }

    if (await oak.playerInvalid(tid)) {
        return oak.chatSend(pid, `[error] player you provided was not found`)
    }

    /* get target position */
    const pos = await oak.playerPositionGet(tid)

    /* set our player position */
    oak.playerPositionSet(pid, pos)
})
```

You can look up the [example code](https://github.com/MafiaHub/oakwood-node/example.js) to see how to use the package.

### Things to note

All public API calls are asynchronous due to the nature of the communication. However, you can `await` the response of the call if you expect a return value.

Check out this primer on how to work with such environment: [Medium: Javascript Async/Await and Promises](https://medium.com/javascript-in-plain-english/javascript-async-await-and-promises-explained-like-youre-five-years-old-61733751e9a5)

