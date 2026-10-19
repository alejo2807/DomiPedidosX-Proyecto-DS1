# DomiPedidosX

Aplicación web para la gestión de pedidos de restaurantes, desarrollada como proyecto académico para la asignatura **Desarrollo de Software I**.

El proyecto utiliza una arquitectura con frontend y backend separados:

- **Frontend:** React, Vite, Axios y Tailwind CSS.
- **Backend:** Python y Django.
- **Base de datos prevista:** PostgreSQL mediante Supabase.
- **Control de versiones:** Git y GitHub.

> **Estado actual:** la estructura inicial de Django y React está creada. La configuración de PostgreSQL/Supabase y el desarrollo de las funcionalidades del sistema se realizarán progresivamente durante los sprints.

---

## 1. Requisitos previos

Antes de comenzar, instala las siguientes herramientas.

| Herramienta | Uso |
|---|---|
| Git | Descargar el repositorio y gestionar los cambios. |
| Python 3.14.x | Ejecutar el backend. |
| pip | Instalar las dependencias de Python. |
| Node.js 22 LTS (22.12 o posterior) | Ejecutar las herramientas del frontend. |
| npm | Instalar las dependencias de JavaScript. |
| Editor de código | Se recomienda Visual Studio Code, aunque puedes utilizar otro. |

### 1.1. Instalar las herramientas en Linux

#### EndeavourOS y Arch Linux

Actualiza el sistema e instala las herramientas:

```bash
sudo pacman -Syu
sudo pacman -S --needed git python python-pip nodejs-lts-jod npm
```

El paquete `nodejs-lts-jod` proporciona Node.js 22 LTS.

#### Ubuntu y Debian

```bash
sudo apt update
sudo apt install -y git python3 python3-venv python3-pip
```

Después, instala una versión compatible de Node.js desde la página oficial:

https://nodejs.org/

Comprueba que la versión instalada sea compatible con Vite 8.

#### Fedora

```bash
sudo dnf install git python3 python3-pip
```

Asegúrate de contar también con `python3-venv` o el soporte de entornos virtuales que proporcione tu instalación de Python, y con una versión compatible de Node.js y npm.

Puedes obtener Node.js desde:

https://nodejs.org/

### 1.2. Instalar las herramientas en Windows

Abre PowerShell y utiliza WinGet para instalar las herramientas:

```powershell
winget install --id Git.Git -e
winget install --id Python.Python.3.14 -e
winget install --id OpenJS.NodeJS.LTS -e
```

Si Windows no reconoce los comandos después de instalar, cierra y vuelve a abrir la terminal.

### 1.3. Instalar las herramientas en macOS

Si tienes Homebrew instalado:

```bash
brew install git python@3.14
brew install node@22
```

Si algún paquete no está disponible para tu versión de Homebrew, consulta las instrucciones oficiales:

- Git: https://git-scm.com/downloads
- Python: https://www.python.org/downloads/
- Node.js: https://nodejs.org/
- Homebrew: https://brew.sh/

### 1.4. Verificar las instalaciones

Ejecuta los comandos disponibles en tu sistema:

```bash
git --version
python --version
python3 --version
node --version
npm --version
```

En Windows también puedes comprobar Python con:

```powershell
py --version
```

**Importante:** las versiones de Python disponibles dependen del sistema operativo y de sus repositorios. El backend se preparó inicialmente con Python 3.14.8. Si utilizas otra versión de Python 3.14, verifica que las dependencias se instalen correctamente.

---

## 2. Clonar el repositorio

Abre una terminal y ejecuta:

```bash
git clone https://github.com/alejo2807/DomiPedidosX-Proyecto-DS1.git
cd DomiPedidosX-Proyecto-DS1
```

La rama de integración del equipo es `develop`.

Para obtener los cambios más recientes:

```bash
git switch develop
git pull origin develop
```

Si ya tienes el repositorio descargado, entra en su carpeta y ejecuta los comandos de actualización anteriores.

---

## 3. Configurar el backend

El backend se encuentra en la carpeta `backend/`.

### 3.1. Crear el entorno virtual

Ejecuta el comando correspondiente a tu sistema operativo desde la raíz del repositorio.

**Linux y macOS:**

```bash
python3 -m venv backend/.venv
```

**Windows — PowerShell:**

```powershell
py -3.14 -m venv backend/.venv
```

Si tu instalación de Windows utiliza `python` en lugar de `py`, puedes probar:

```powershell
python -m venv backend/.venv
```

No necesitas crear el entorno virtual si ya existe uno funcional en `backend/.venv/`. Cada integrante debe tener su propio entorno virtual local.

### 3.2. Activar el entorno virtual

**Linux y macOS:**

```bash
source backend/.venv/bin/activate
```

**Windows — PowerShell:**

```powershell
.\backend\.venv\Scripts\Activate.ps1
```

**Windows — Símbolo del sistema (CMD):**

```bat
backend\.venv\Scripts\activate.bat
```

Al activarse, normalmente aparecerá `(.venv)` al comienzo de la línea de comandos.

Si PowerShell bloquea la activación del entorno, puedes utilizar CMD o ejecutar Python directamente desde el entorno virtual.

### 3.3. Instalar las dependencias

Desde la raíz del repositorio, con el entorno virtual activado:

```bash
python -m pip install --upgrade pip
python -m pip install -r backend/requirements.txt
```

### 3.4. Verificar Django

Comprueba que Django está instalado:

```bash
python -m django --version
```

Después, ejecuta el servidor de desarrollo desde la raíz:

```bash
python backend/manage.py runserver
```

El backend estará disponible normalmente en:

http://127.0.0.1:8000/

Para detenerlo, presiona `Ctrl + C`.

> **Base de datos:** PostgreSQL/Supabase todavía debe configurarse en Django. No ejecutes migraciones hasta que el equipo complete esa configuración. La base SQLite local existente no forma parte del flujo de trabajo previsto.

---

## 4. Configurar el frontend

El frontend se encuentra en la carpeta `frontend/`.

### 4.1. Instalar las dependencias

Desde la raíz del repositorio:

```bash
cd frontend
npm ci
```

`npm ci` instala las dependencias utilizando `package-lock.json`, respetando las versiones registradas en el proyecto.

Si `npm ci` informa que falta o no coincide el archivo de bloqueo, no lo elimines ni lo regeneres automáticamente: informa al equipo para revisar el estado del repositorio.

### 4.2. Ejecutar el frontend

```bash
npm run dev
```

Vite mostrará una dirección local, normalmente:

http://localhost:5173/

Abre esa dirección en el navegador.

Para detener el servidor, presiona `Ctrl + C`.

### 4.3. Comprobar el frontend

Para verificar que el proyecto compila correctamente:

```bash
npm run build
```

Para ejecutar el análisis estático del código:

```bash
npm run lint
```

Ambos comandos deben terminar sin errores.

---

## 5. Ejecutar el proyecto durante el desarrollo

El backend y el frontend se ejecutan en terminales separadas.

1. Abre una terminal en la raíz del repositorio y activa el entorno virtual.
2. Inicia Django con `python backend/manage.py runserver`.
3. Abre otra terminal y entra en la carpeta `frontend/`.
4. Ejecuta `npm run dev`.
5. Accede a la dirección local de Vite desde el navegador.

El frontend y el backend todavía deben conectarse mediante Axios cuando se implementen los endpoints de la API.

---

## 6. Estructura del repositorio

```text
DomiPedidosX-Proyecto-DS1/
├── backend/
│   ├── config/
│   ├── manage.py
│   └── requirements.txt
├── frontend/
│   ├── public/
│   ├── src/
│   ├── package.json
│   ├── package-lock.json
│   └── vite.config.js
├── .gitignore
└── README.md
```

La estructura evolucionará conforme se incorporen las aplicaciones Django, los componentes React, las pruebas y la documentación.

---

## 7. Buenas prácticas de Git

El equipo utiliza las siguientes ramas:

- `main`: versiones estables del proyecto.
- `develop`: integración del trabajo del equipo.
- `feature/*`: desarrollo de funcionalidades o tareas concretas.

### Flujo de trabajo recomendado

1. Actualizar la rama `develop`.
2. Crear una rama de trabajo desde `develop`.
3. Implementar una tarea concreta y realizar commits pequeños.
4. Subir la rama a GitHub.
5. Abrir un Pull Request hacia `develop`.
6. Revisar y probar los cambios antes de integrarlos.

### Ejemplo de flujo

```bash
git switch develop
git pull origin develop
git switch -c feature/nombre-de-la-funcionalidad
```

Después de realizar los cambios:

```bash
git add .
git commit -m "feat(scope): describe the change"
git push -u origin feature/nombre-de-la-funcionalidad
```

Luego, abre un Pull Request en GitHub con destino a `develop`.

### Convención de commits

Utilizamos el formato:

`<type>(<optional scope>): <description>`

Ejemplos:

```text
feat(auth): add user login endpoint
fix(products): validate product price
docs(readme): add setup instructions
test(orders): add order creation tests
refactor(users): extract validation logic
build(frontend): initialize React app with Vite
chore(git): update gitignore rules
```

Procura que los commits sean pequeños, descriptivos y relacionados con una tarea concreta.

---

## 8. Archivos que no deben subirse a GitHub

No deben versionarse:

- Entornos virtuales de Python, como `.venv/`.
- Dependencias instaladas de Node.js, como `node_modules/`.
- Archivos de compilación, como `frontend/dist/`.
- Archivos `.env` con credenciales o secretos.
- Bases de datos locales y archivos generados que no formen parte del código fuente.

Los archivos `requirements.txt`, `package.json` y `package-lock.json` sí deben versionarse.

**Nunca compartas contraseñas, claves privadas ni credenciales de Supabase mediante commits o Pull Requests.**

---

## 9. Solución de problemas

### El comando `python` o `python3` no funciona

Comprueba la instalación de Python y prueba el comando disponible en tu sistema. En Windows puedes utilizar `py`.

### El comando `npm` no funciona

Instala Node.js y npm, abre una nueva terminal y verifica las versiones con:

```bash
node --version
npm --version
```

### No se encuentra una dependencia de Python

Activa el entorno virtual de `backend/` e instala las dependencias con:

```bash
python -m pip install -r backend/requirements.txt
```

### El frontend no encuentra sus dependencias

Entra en `frontend/` y ejecuta:

```bash
npm ci
```

### El puerto ya está ocupado

Revisa si existe otro proceso ejecutando el backend o el frontend. Si es necesario, detén el proceso anterior antes de iniciar otro.

### No puedo activar el entorno virtual en PowerShell

Si la política de ejecución de PowerShell impide activar el entorno, puedes utilizar CMD o ejecutar directamente el intérprete del entorno virtual:

```powershell
.\backend\.venv\Scripts\python.exe backend\manage.py runserver
```

---

## 10. Próximos pasos

- Configurar PostgreSQL/Supabase en Django.
- Definir las aplicaciones y modelos del backend a partir del diseño aprobado.
- Implementar los endpoints de la API.
- Conectar React con Django mediante Axios.
- Incorporar pruebas y documentación conforme avance cada sprint.
