---
Category: Instruction
tags:
  - instruction
  - draft
  - linux
---
---
###### External links
- 
## Description


---
## Manual
---ssh-keygen -t ed25519 -C "your_email@example.com"
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

cat ~/.ssh/id_ed25519.pub

**GitHub**:  
Зайди в [https://github.com/settings/keys](https://github.com/settings/keys)  
→ **"New SSH key"**  
→ вставь туда ключ.

---
## Notes

