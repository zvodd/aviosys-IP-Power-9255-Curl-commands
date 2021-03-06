# IP Power 9255 Pro curl commands

Curl commands to control `IP Power 9255` by `aviosys`

## Assumptions
Device IP: `192.168.0.90` 
Default login :
   - username: `admin`
   - password: `12345678` 

### windows env ##
Line endings in `on`/`off.input` seems to need be `\r\n` aka `0x0d0a` on windows
Turn ON
```
curl --data-binary "@on.input" -b"admin=12345678; Taifatech=yes"  -H "Content-Type: text/plain" -XPOST "192.168.0.90/tgi/iocontrol.tgi" > NUL
```

Turn OFF
```
curl --data-binary "@off.input" -b"admin=12345678; Taifatech=yes"  -H "Content-Type: text/plain" -XPOST "192.168.0.90/tgi/iocontrol.tgi" > NUL
```
### *nix env 
Turn ON
```
curl --data-binary "pw1Name=PSU_DEV_1\nP60=On\nP60_TS=0\nP60_TC=Off\nButtonName=Apply\n" -b"admin=12345678; Taifatech=yes"  -H "Content-Type: text/plain" -XPOST "192.168.0.90/tgi/iocontrol.tgi"
```
Turn OFF
```
curl --data-binary "pw1Name=PSU_DEV_1\nP60=Off\nP60_TS=0\nP60_TC=Off\nButtonName=Apply\n" -b"admin=12345678; Taifatech=yes"  -H "Content-Type: text/plain" -XPOST "192.168.0.90/tgi/iocontrol.tgi"
```
