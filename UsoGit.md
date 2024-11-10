Uso de Git
===
Aquí explica el uso de los principales comandos de Git.

# Principales Comandos de Git

## Configuración inicial
- `git config --global user.name "Tu Nombre"`: Configura tu nombre de usuario globalmente.
- `git config --global user.email "tuemail@example.com"`: Configura tu correo electrónico globalmente.

## Inicializar un repositorio
- `git init`: Inicializa un nuevo repositorio Git en el directorio actual.

## Comandos básicos de archivos
- `git add <archivo>`: Añade un archivo específico al área de preparación (staging area).
- `git add .`: Añade todos los archivos cambiados en el directorio al área de preparación.
- `git commit -m "Mensaje del commit"`: Crea un commit con un mensaje que describe los cambios.

## Ver el estado y el historial
- `git status`: Muestra el estado actual del repositorio (archivos en staging, sin seguimiento, cambios pendientes).
- `git log`: Muestra el historial de commits en el repositorio.
- `git log --oneline`: Muestra el historial de commits en una sola línea por commit.

## Trabajar con ramas
- `git branch <nombre_rama>`: Crea una nueva rama.
- `git branch`: Lista todas las ramas en el repositorio.
- `git checkout <nombre_rama>`: Cambia a la rama especificada.
- `git checkout -b <nombre_rama>`: Crea una nueva rama y cambia a ella inmediatamente.

## Fusionar ramas
- `git merge <nombre_rama>`: Fusiona la rama especificada en la rama actual.
  - **Nota**: Resuelve conflictos manualmente si ocurren durante la fusión y realiza un commit adicional.

## Comandos de sincronización con un repositorio remoto
- `git remote add origin <url_repositorio>`: Vincula el repositorio local a un repositorio remoto.
- `git push -u origin <nombre_rama>`: Sube los cambios de la rama especificada al repositorio remoto y establece el seguimiento.
- `git pull`: Descarga los cambios del repositorio remoto y los fusiona con la rama actual.
- `git clone <url_repositorio>`: Crea una copia local de un repositorio remoto.

## Deshacer cambios
- `git checkout -- <archivo>`: Descarta los cambios en un archivo en el área de trabajo.
- `git reset HEAD <archivo>`: Quita un archivo del área de staging pero conserva los cambios en el área de trabajo.
- `git reset --hard <commit>`: Restablece el repositorio al estado de un commit anterior, eliminando todos los cambios posteriores.

---

Estos comandos básicos de Git te ayudarán a realizar las operaciones esenciales de administración de versiones en tus proyectos.



