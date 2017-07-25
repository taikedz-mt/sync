# MTSync-Web Schema

Schema for SQL database backend.

A server has a name and a secret (the API key)

A player has any number of named inventories, each inventory can hold an arbitrary number of items.

A player has a single meatadata table ; each entry in the table can hold data on the player, as well as be specifically owned by a server or be shared amongst all.

A queue system allows servers to push a notification to all servers, and to receive notifications of changes. When a server pushes a notification, each server receives their own copy of the item.

Each queued item has a creation date. Queued items are cleared after a given amount of time, except items marked `must_consume`

           +------------------------------+
	   | Server
	   +------------------------------+
	   |
	   | int          : serverid
	   | varchar(32)  : servername
	   | varchar(128) : serversecret
	   |
	   +------------------------------+

           +--------------------------------+
	   | Player
	   +--------------------------------+
	   |
	   | int          : playerid
	   | varchar(128) : playername
	   | bool         : banned
	   |
	   +--------------------------------+


           +------------------------------+
	   | Inventory
	   +------------------------------+
	   |
	   | int          : inventoryid
	   | int          : playerid  
	   | varchar(32)  : inventoryname
	   |
	   +------------------------------+

           +------------------------------+
	   | InventorySlot
	   +------------------------------+
	   |
	   | int          : slotid
	   | int          : inventoryid
	   | varchar(128) : itemstring
	   | int          : quantity
	   |
	   +------------------------------+


           +------------------------------+
	   | PlayerMetaTable
	   +------------------------------+
	   |
	   | int          : metaid
	   | int          : playerid  
	   |
	   +------------------------------+

           +------------------------------+
	   | MetaDataEntry
	   +------------------------------+
	   |
	   | int          : entryid
	   | int          : serverid
	   | int          : metatableid
	   | varchar(128) : datastring
	   |
	   +------------------------------+


	   +------------------------------+
	   | QueuedItem
	   +------------------------------+
	   |
	   | int             : queueditemid
	   | int             : serverid
	   | varchar(4096)   : data
	   | varchar(32)     : itemtype
	   | datetime (auto) : creationdate
	   | bool            : must_consume
	   |
	   +-----------------------------+
