#Set NetSuite security options in appsettings.json to point to produuction

# numeric script id
NsRestPush.exe 1234 payloads.json

# or use aliases (when configured)
NsRestPush.exe truck payloads-truck.json
NsRestPush.exe rail  payloads-rail.json