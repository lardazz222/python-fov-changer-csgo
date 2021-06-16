# fov.py
fov.py - change FOV in csgo using very few lines. The method is most likely to not get detected by VAC.





## Usage

```python
import pymem
import requests

proc = pymem.Pymem("csgo.exe")
client = pymem.process.module_from_name(proc.process_handle, "client.dll").lpBaseOfDll
engine = pymem.process.module_from_name(proc.process_handle, "engine.dll" ).lpBaseOfDll

offsets = requests.get('https://raw.githubusercontent.com/frk1/hazedumper/master/csgo.json').json()
dwLocalPlayer = int(offsets['signatures'['dwLocalPlayer']])

player= proc.read_int(client + dwLocalPlayer)
proc.write_int( player + 0x332C, 120)

```
