## Non-UPL Packet format:
{'cmd':(Command), 'name':(Variable name), 'id':(A user's ID), 'val':(Payload), 'origin':(User ID originally transmitting from)}

## CloudLink
ds - Handles server soft-shutdown disconnect request
 > parameters: none

 > Sends from server to all clients

ulist - Handles username list data
 > parameters: val (String as primitive array split by ";")

 > Sends from server to all clients

setid - Defines the ID of a user
 > parameters: val - String

 > Sends from any client to server

gmsg - Sends global message data
 > parameters: val (String/Int/Bool/JSON)

 > Sent by both parties (server & clients)

pmsg - Sends private message data
 > parameters: val (String/Int/Bool/JSON), id (String)

 > Sent by both parties (server & clients)

gvar - Sends global variable data
 > parameters: val (String/Int/Bool/JSON), name (String)

 > Sent by both parties (server & clients)

pvar - Sends private variable data
 > parameters: val (String/Int/Bool/JSON), id (String), name (String)

 > Sent by both parties (server & clients)


link - Connects to a webserver

unlink - Disconnects from a webserver

fetchid - Uses CLNS to find linked Plugins

checkid - Reads status of user/webserver (online, version)

host - Presents the plugin publically for access via CLNS

unhost - Removes plugin from CLNS

prtclchk - Checks CloudLink server/client version & protcols supported

prtclupg - Upgrades protcols for CloudLink client/server

omni - Experimental CloudLink to Scratch Cloud Variable Server bridge (powered by scratchclient)


## CloudAccount:
auth2fa - Authenticate using 2FA
 > parameters: none

 > Sends from client to server

 > Returns JSON w/ key for authenticator service

auth - Authenticate using password

 > parameters: val - String

 > Sends from client to server

 > Returns JSON

deauth - Logout
 > parameters: none

 > Sends from client to server

 > Returns "OK"

checkauth - Return account info
 > parameters: none

 > Sends from client to server

 > Returns JSON

checkkeys - Check 2FA state and authenticate
 > parameters: none

 > Sends from client to server

 > Returns JSON

## CloudDisk:
auth - Verify access using an authentication token provided by CloudAccount
 > Parameters: val - String

 > Sends from client to server

 > Returns JSON

deauth - Removes access when finished
 > Parameters: none

 > Sends from client to server

 > Returns "OK"

getftpdir - Gets a list of all files/folders available in a directory within CFTP
 > Parameters: Parameters: val - String (Directory format: "/folder1/folder2")

 > Sends from client to server

 > Returns String (String as primitive array split by ",")

getftpfile - Downloads a file from a server using CFTP (CloudLink FTP)
 > Parameters: Parameters: val - String (Directory format: "/folder1/folder2/file.extension")

 > Sends from client to server

 > Returns String or JSON

putftp - Uploads a file to a server
 > Parameters: Parameters: val - JSON

 > JSON format: 

{

"filename": (File's name (String, Directory format: "/folder1/folder2/file.extension")),

"data": (File's contents (String, JSON, etc.))

}
 > Sends from client to server

 > Returns "OK"

ftpmkdir - Creates directories.
 > Parameters: Parameters: val - String (Directory format: "/folder1/folder2")

 > Sends from client to server
 
 > Returns "OK"

ftprmdir - Deletes directories (only works if there are no files present in a directory)
 > Parameters: Parameters: val - String (The location of where the directory is to be deleted.)
 
 > Sends from client to server
 
 > Returns "OK"

ftprmfile - Deletes files
 > Parameters: Parameters: val - JSON

 > JSON format: 

{

"dir": (The directory of where the file is located.),

"name": (The filename to be deleted.)

}
 > Sends from client to server

 > Returns "OK"

fetchslot - Reads data stored in a slot

putslot - Writes data into a slot

setftpconfig - Configure a directory/file's permissions, access, visibility, and security settings

getftpinfo - Gets a file/folder's metadata from a server

## CloudCoin:
auth - Verify access using an authentication token provided by CloudAccount
 
 > Parameters: val - String
 
 > Sends from client to server
 
 > Returns JSON

deauth - Removes access when finished
 > Parameters: none
 
 > Sends from client to server
 
 > Returns "OK"

checkassets - Checks how many coins are in circulation

getinfo - Get account info

mine - Sends a mine check

spend - Uses x amount of coins
