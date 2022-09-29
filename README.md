# fov.py
Change FOV in csgo using very few lines. ~~The method is most likely to not get detected by VAC.~~
## Important
Due to recent changes to CSGO, this cheat may be detected by VAC. 
Please use this at your own risk.




## Usage

```python
import pymem
import requests

fov = 120

proc = pymem.Pymem("csgo.exe")
client = pymem.process.module_from_name(proc.process_handle, "client.dll").lpBaseOfDll
engine = pymem.process.module_from_name(proc.process_handle, "engine.dll" ).lpBaseOfDll

offsets = requests.get('https://raw.githubusercontent.com/frk1/hazedumper/master/csgo.json').json()
dwLocalPlayer = int(offsets['signatures']['dwLocalPlayer']])

player= proc.read_int(client + dwLocalPlayer)
proc.write_int( player + 0x332C, fov)

```
