# Minetest Server Sync

This is a suite of tools that allow two or more distinct servers to share data.

Notably:

* When one server registers a new player, other servers will automatically also register the same player.
* A player can save certain items to their Shared Space
* A player can import items from their Shared Space
* Each server can determine what items players are allowed to import/export on any given server.

Other information that can be sync'd :

* Player ban status
* Arbitrary player metadata
