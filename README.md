# SOCIAL OPLESK
### 🏴‍☠️ HACKS 
<br/>

## ⚡️ Hack Github Actions 1⚡️

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
| H-3      | detectar eventos |
| H-4      | condiciones |
| H-5      | uses |
| H-5     | comandos linux |
<br/> 


## 🏆 H-1

```

📁hack_gh_1/
├── .github/workflows/flow.yml

```

1. Crear un directorio el archivo flow.yml en un repositorio

2. Dentro del flow.yml pegar eL script

3. Debes crear aplicar los ajustes necesarios

4. Ejecutar el workflow con el evento push

```
💡tips

❌ Mal (no, si es para - de 3 items)
    on: [push, pull_request, fork, schedule, workflow_dispatch, create, release]

---

✅ Bien (ideal si es para - de 3 items)
    on: [push, pull_request, fork]


✅ Bien (ideal si es para + de 3 items)
    on:
      - push
      - pull_request
      - fork
      - schedule
      - workflow_dispatch
      - create   
      - release

```

<br/>
🟢 Script github/actions del hack-1 a resolver 🟢

```yaml

name: Saludo
on: ❓

jobs:
  saludo:
    runs-on: ubuntu-latest
    steps:
      - name: Decir hola
        run: echo "Hola mundo desde GitHub Actions"
```

<br />
<br />


## 🏆 H-2

```

📁hack_gh_2/
├── .github/workflows/flow.yml

```

1. Crear un directorio el archivo flow.yml en un repositorio

2. Dentro del flow.yml pegar eL script

3. Debes crear aplicar los ajustes necesarios

4. Ejecutar el workflow con el evento push y pull_request


```
💡tips

Autor del commit:
    ${{ github.actor }}

---

Workflow se disparó por:
    ${{ github.event_name }}

```

<br/>
🟢 Script github/actions del hack-2 a resolver 🟢

```yaml

name: Eventos
on: [❓, ❓]

jobs:
  detectar-evento:
    runs-on: ubuntu-latest
    steps:
      - name: Mostrar tipo de evento
        run: echo "El autor es: ❓"

      - name: Mostrar tipo de evento
        run: echo "El evento que me activó fue: ❓"
```

<br />
<br />

## 🏆 H-3

```

📁hack_gh_3/
├── .github/workflows/flow.yml

```

1. Crear un directorio el archivo flow.yml en un repositorio

2. Dentro del flow.yml pegar eL script

3. Debes crear aplicar los ajustes necesarios

4. Ejecutar el workflow con el evento push

```
💡tips

# ✅ Recomendado por GitHub para if:
if: github.event_name == 'push'


# ✅ Necesario para bash script (SIEMPRE con ${{ }})
run: echo "${{ github.event_name }}"

```

<br/>
🟢 Script github/actions del hack-3 a resolver 🟢

```yaml

name: Condiciones

on: [push, ❓]

jobs:
  ejemplo:
    runs-on: ubuntu-latest
    steps:
      - name: detectar push con if
        if: github.event_name == '❓'
        run: echo "Ejecutando solo en push"

      - name: detectar pull_request con if
        if: ❓ == 'pull_request'
        run: echo "Ejecutando solo en PR"

      - name: Otra forma
        run: |
          if [ "${{ github.event_name }}" == "❓" ]; then
            echo "Se detectó un push desde script bash"
          fi
```

<br />
<br />

## 🏆 H-4

```

📁hack_gh_4/
├── .github/workflows/flow.yml

```

1. Crear un directorio el archivo flow.yml en un repositorio

2. Dentro del flow.yml pegar eL script

3. Debes crear aplicar los ajustes necesarios

4. Ejecutar el workflow con el evento push

```
💡tips

 El step: "uses" se emplea cuando no quieres escribir comandos de terminal desde cero, <br/>
 sino que prefieres utilizar una "Acción" ya creada (un bloque de código reutilizable <br/>
 empaquetado por GitHub, la comunidad o tu propio equipo).


❌ Descargar el código del repositorio 
- name: Clonar repositorio
  run: git clone https://github.com/usuario/repositorio.git .

---

✅ Descargar el código del repositorio 
 - name: Clonar repositorio 
   uses: actions/checkout@v4   


✅ Genera un archivo ".zip" descargable con todo el contenido del proyecto.
 - name: Descargar proyecto
   uses: actions/upload-artifact@v4
     with:
       name: mi-proyecto-completo   # ← Nombre del artefacto (verás este nombre al descargar)     
       path: .                      # ← Qué archivos incluir (. = todo el proyecto)     
       retention-days: 7            # ← Cuántos días estará disponible para descargar

 En el run puedes busar una url como la del ejemplo y al dar click descargar el proyecto
 output =>  Artifact download URL: https://github.com/...

```

<br/>
🟢 Script github/actions del hack-4 a resolver 🟢

```yaml

name: Descargar repositorio
on: [❓]

jobs:
  checkout:
    runs-on: ubuntu-latest
    steps:
      - name: Descargar código
        uses: ❓
      - run: ls -la

      - name: Descargar proyecto
        uses: ❓
        with:
          name: ❓       
          path: .                          
          retention-days: 7    
```

<br />
<br />

## 🏆 H-5 

```

📁hack_gh_5/
├── .github/workflows/flow.yml

```

1. Crear un directorio el archivo flow.yml en un repositorio

2. Dentro del flow.yml pegar eL script

3. Debes crear aplicar los ajustes necesarios

4. Ejecutar el workflow con el evento push

5. Adicional debes buscar el detalle oculto que no permite ejecutar el script del hack-5


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
    run: |    # ← La barra conocida como "pipe" permite encadenar comandos en el step run
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
🟢 Script github/actions del hack-5 a resolver 🟢

```yaml

name: Comandos Linux
on: ❓

jobs:
  comandos:
    runs-on: ubuntu-latest
    steps:
      - name: comandos
      - run: whoami
      - run: pwd
      - run: date
      - run: uname -a
      - run: |
          echo "Varios comandos en un solo step"
          ls -la
```

<br />
<br />

---

