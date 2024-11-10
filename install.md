Configuración git
=========
Para configurar ejecutamos __ git config ___
![](imagenes/captura_comandos_config.png)


# Guía para Crear y Subir un Repositorio a GitHub desde Kali Linux

Esta guía explica los pasos para crear un repositorio Git en tu máquina local, configurarlo con claves SSH, y luego subirlo a GitHub.

## 1. Configuración Inicial de Git

Antes de empezar, asegúrate de tener Git configurado en tu sistema. Si no lo tienes, puedes instalarlo con:

```bash
sudo apt install git
```

Luego, configura tu nombre de usuario y correo electrónico para que Git pueda hacer los commits con tu identidad.

### Configurar Nombre y Correo Electrónico:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@example.com"
```

## 2. Configurar Claves SSH para Conexión con GitHub

Para no tener que introducir tu usuario y contraseña cada vez que subes archivos a GitHub, es recomendable usar claves SSH.

### Generar una clave SSH

1. Abre una terminal y ejecuta el siguiente comando para generar una nueva clave SSH:

```bash
ssh-keygen -t rsa -b 4096 -C "tuemail@example.com"
```

2. Cuando se te pida, elige la ubicación de la clave o presiona Enter para aceptar la predeterminada (`/home/usuario/.ssh/id_rsa`).
3. Ingresa una frase de contraseña (opcional).

### Agregar la clave SSH al agente SSH

1. Inicia el agente SSH:

```bash
eval "$(ssh-agent -s)"
```

2. Agrega la clave SSH al agente:

```bash
ssh-add ~/.ssh/id_rsa
```

### Agregar la clave SSH a GitHub

1. Copia tu clave pública con el siguiente comando:

```bash
cat ~/.ssh/id_rsa.pub
```

2. Inicia sesión en GitHub, ve a **Settings > SSH and GPG keys** y haz clic en **New SSH key**.
3. Pega la clave copiada en el campo correspondiente y haz clic en **Add SSH key**.

### Verifica la conexión SSH

Para asegurarte de que todo está configurado correctamente, prueba la conexión SSH:

```bash
ssh -T git@github.com
```

Deberías ver un mensaje como:

```
Hi tuusuario! You've successfully authenticated, but GitHub does not provide shell access.
```

## 3. Crear un Repositorio Local

1. Crea o navega al directorio donde deseas crear el repositorio:

```bash
cd /ruta/a/tu/proyecto
```

2. Inicializa el repositorio local con el comando `git init`:

```bash
git init
```

Esto creará un repositorio vacío en el directorio.

3. Si ya tienes archivos en este directorio, agrégales al área de preparación (staging):

```bash
git add .
```

Esto agrega todos los archivos del directorio al área de preparación para ser confirmados.

4. Realiza un commit para registrar estos cambios:

```bash
git commit -m "Primer commit"
```

## 4. Crear un Repositorio en GitHub

1. Inicia sesión en tu cuenta de GitHub.
2. Haz clic en **New** para crear un nuevo repositorio.
3. Ingresa el nombre del repositorio y ajusta las configuraciones (público o privado).
4. No marques la opción de "Initialize this repository with a README", ya que lo haremos desde la terminal.
5. Haz clic en **Create repository**.

## 5. Vincular el Repositorio Local con GitHub

1. Copia la URL SSH de tu repositorio en GitHub. Por ejemplo: `git@github.com:usuario/nombre-repositorio.git`.
2. Vincula el repositorio remoto de GitHub con tu repositorio local:

```bash
git remote add origin git@github.com:usuario/nombre-repositorio.git
```

## 6. Subir el Repositorio Local a GitHub

1. Sube los archivos de tu repositorio local al repositorio remoto en GitHub:

```bash
git push -u origin master
```

Si usas la nueva convención de GitHub, es posible que la rama predeterminada sea `main` en lugar de `master`. Si es así, usa:

```bash
git push -u origin main
```

2. Verifica tu repositorio en GitHub. Deberías ver los archivos que subiste desde tu máquina local.

## 7. Comandos Git Esenciales

### `git init`
Inicializa un repositorio vacío en el directorio actual.

```bash
git init
```

### `git add`
Agrega archivos al área de preparación para su inclusión en el commit. Puedes agregar todos los archivos con:

```bash
git add .
```

### `git commit`
Realiza un commit para registrar los cambios. Asegúrate de incluir un mensaje descriptivo:

```bash
git commit -m "Descripción de los cambios"
```

### `git status`
Muestra el estado actual del repositorio, incluidos los archivos modificados y pendientes de confirmar:

```bash
git status
```

### `git log`
Muestra el historial de commits del repositorio:

```bash
git log
```

### `git push`
Envía los commits de tu repositorio local a un repositorio remoto. Para la primera vez, usa `-u` para establecer la rama predeterminada:

```bash
git push -u origin master
```

### `git pull`
Obtiene los cambios del repositorio remoto y los fusiona con el repositorio local:

```bash
git pull
```

---

Con estos pasos habrás configurado Git, generado claves SSH, creado un repositorio local y lo habrás vinculado a GitHub para poder subir tus archivos. Además, has aprendido algunos de los comandos Git más utilizados en el flujo de trabajo diario.
