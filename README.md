# SOCIAL OPLESK
### 🏴‍☠️ HACKS 
<br/>

## ⚡️ Hack Github Actions ⚡️

<br />
<br />


**Requisitos previos**
<br/>

```diff
- NOTA HACER LAS PRÁCTICAS MEDIANTE LA CONSOLA - TERMINAL  
- Debes tener cuenta en vercel y usar la terminal de wsl en caso de emplear windows, ideal sobre debian / ubuntu / fedora.
```
|Hacks | Details | 
|----------|---------|
| H-1      | saludo desde terminal |
| H-2      | comandos linux |
<br/> 


## 🏆 H-2 

```

📁hack_gh_2/
├── .github/workflows/flow.yml

```

1. Crear un directorio el archivo flow.yml en un repositorio

2. Dentro del flow.yml pegar eL script

3. Debes crear aplicar los ajustes necesarios

4. Cuando ejecutas multiples comandos con el tag "- run" de forma consecutiva,<br/>
   es posibles si aplicas el tag "- name" una sola vez

```
💡tips

❌ Mal (no si es para - de 2 ramas/items)
    branches: [main]

---

✅ Bien (ideal si es para + de 2 ramas/items)
    branches:
        - main

```

<br/>

```
💡tips
Cada step debe tener al menos una clave como name, run, uses

steps:
  - name: comandos    # ← Esto es un step sin comando
  - run: whoami       # ← Esto es otro step
  - run: pwd          # ← Otro step más

---
❌ Forma incorrecta de usar name:

steps:
  - name: comandos    # ← Esto es un step sin comando
  - run: whoami       # ← Esto es otro step

---

✅ Forma correcta de usar name:
   
steps:
  - name: comandos    # ← Esto es un step con comando run
    run: whoami       # ← El run que acompaña al step - name


✅ Forma correcta de usar name: con varios comandos en un solo step

steps:
  - name: Comandos Linux
    run: |
      whoami
      pwd
      date
      uname -a
      echo "Varios comandos en un solo step"
      ls -la

✅ Forma correcta de usar un step:
   Cada - run: es un step completo y válido, aunque no tenga name <br/>
   El name es opcional, si no lo pones, GitHub usa el comando como nombre por defecto

steps:
  - run: whoami      # Step 1: ejecuta whoami
  - run: pwd         # Step 2: ejecuta pwd
  - run: date        # Step 3: ejecuta date
```


<br/>
🟢 Script github/actions del hack-2 a resolver 🟢

```yaml

name: Comandos Linux
on: [❓]

jobs:
  comandos:
    runs-on: ubuntu-latest
    steps:
      - run: whoami
      - run: pwd
      - run: date
      - run: uname -a
      - run: |
          echo "Varios comandos en un solo step"
          ls -la
```

---

