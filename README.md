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

## Mod

Add the mtsync mod to your mods directory

Add `mtsync` to the list of secure trusted mods (it needs to be able to alter the auth file, and make HTTP(S) calls)

Edit minetest.conf to configure

* URL to the web api, e.g. `mtsync.api = http://localhost/stuff/mtsyncapi`
* server's secret key, e.g. `mtsync.secret = zevlise5o9seg5lh8aw0se58lase57w39ojsh`


## Web Component

### Installation

The web component is a PHP interface that exposes the store API

Add the `mtsyncapi` directory to a web server, for example at `http://localhost/stuff/mtsyncapi`

> ***If the API must be available on the Internet you MUST deploy to a HTTPS-enabled server***

Install MySQL server or MariaDB server, and add a database and user for mtsync

Edit the live `mtsyncapi/config.php` and add the details to connect to your MySQL instance, as well as an admin password.

### Configuration

Go to the web interface in a browser (Firefox, Chromium, etc): `http://localhost/stuff/mysqyncapi/`

You will see a page asking you to enter your admin password, do so. The admin password will be disabled after 3 bad attempts.

You will then see the servers configured and their keys.

Modify the keys if you need, or add servers, enter your admin password again, and submit to save changes.
