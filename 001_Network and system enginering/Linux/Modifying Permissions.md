---
Category: Information
tags:
  - information
  - linux
  - open
---
---
###### External links
- 
---
## Description


---
## Modifying Permissions
### Chmod
---
- Первый вариант записи: `cmod [u, g, o, a][+-][r, w, x] file`.
- Числовой вариант записи `chmod 777 file`: 
	- `r = 4`, `w = 2`, `x = 1`
	- Складываются для каждой категории

### Modify ownership
---
- #### chown

	`sudo chown alice file.txt`

	*Можно вообще к папке, например и через двоеточие групу овенеров:*
	`sudo chown bob:developers project/`

	*Если через двоеточие пусто оставить то група будет юзера, который указан.*

- #### chgr
	
	`sudo chgrp staff file.txt`





---
## Notes


---
