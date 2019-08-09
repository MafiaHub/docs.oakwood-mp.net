---
description: This page describes how to setup the server.
---

# Server Setup

### Download server binaries

We need to download server binaries for our operating system:

* Windows: `TODO: Add link`
* Linux: `TODO: Add link`

Once you have the respective archive downloaded, unpack it to an empty folder.

### Server configuration

After your first server launch, several folders will get generated. One of which is our `config` folder which contains `server.json` SJSON config file. Check it out to see possible options you can set up:

```javascript
max_players     = 64
name            = "<name>"
host            = "<ip-to-bind-to>|<empty>"
password        = "<password-or-empty>"
visible         = true
port            = 27010
mapname         = "freeride"
bridge_inbound  = "ipc://oakwood-inbound"
bridge_outbound = "ipc://oakwood-outbound"
whitelist       = false
```

### Setting up your resources

Your server is now ready and running. However, we need to provide a resource which will define the gameplay logic. The server alone only takes care of game sync and state control, but does not contribute to the gameplay itself.

If we'd like the players to join our server, shoot each other, spawn vehicles or even chat, we need to code a resource which will take care of that. Oakwood does this intelligently, as it exposes a public API of methods your resources can call \(and also triggers events you subscribe to\) by remote process communication.
