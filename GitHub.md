Git con GitHub.com
====
Aquí explica el proceso de apertura de cuenta, login, y funcionamiento de plataforma GitHub.com 

La cuenta sobre la que voy a trabajar en GitHub ya la tengo creada de 1º de ASIR. El nombre de la cuenta con la que me logeo es  vjp-raulAP  y la contraseña

para crearme la cuenta es: 

## 1. Crear una Cuenta en GitHub

### Paso 1: Accede a la Página de Registro

1. Abre tu navegador web y visita la página principal de GitHub: [https://github.com](https://github.com).
2. En la página de inicio, encontrarás el botón **Sign up** en la parte superior derecha. Haz clic en él para comenzar el proceso de registro.

### Paso 2: Completa el Formulario de Registro

GitHub te pedirá la siguiente información:

- **Username**: El nombre de usuario que deseas utilizar. Este será tu identificador en la plataforma.
- **Email Address**: La dirección de correo electrónico asociada a tu cuenta.
- **Password**: La contraseña que usarás para acceder a tu cuenta.

Asegúrate de que tu nombre de usuario y correo electrónico sean correctos, ya que esta información se usará para las notificaciones y la identificación en los repositorios.

### Paso 3: Verificación

Después de completar el formulario, GitHub te pedirá verificar tu correo electrónico:

1. Accede a tu bandeja de entrada y busca el correo de verificación de GitHub.
2. Haz clic en el enlace de verificación para confirmar tu cuenta.

### Paso 4: Plan de Suscripción

GitHub ofrece una cuenta gratuita y varias opciones de pago. Para la mayoría de los usuarios nuevos, la opción gratuita es suficiente:

1. Selecciona el plan que deseas. Para empezar, puedes elegir el plan gratuito.
2. Haz clic en **Continue**.

### Paso 5: Completa el Registro

GitHub puede pedirte que completes algunos detalles adicionales, como tus preferencias de uso. Después de llenar estos campos, haz clic en **Complete setup**.

¡Ya has creado tu cuenta en GitHub!

## 2. Iniciar Sesión en GitHub

### Paso 1: Accede a GitHub

1. Abre tu navegador y ve a [https://github.com](https://github.com).
2. En la parte superior derecha de la página de inicio, haz clic en **Sign in**.

### Paso 2: Introduce tu Nombre de Usuario y Contraseña

1. En la página de inicio de sesión, introduce tu **nombre de usuario** o **correo electrónico** y **contraseña**.
2. Haz clic en el botón **Sign in**.

### Paso 3: Autenticación de Dos Factores (si está habilitada)

Si tienes habilitada la autenticación de dos factores, GitHub te pedirá un código adicional. Este código te será enviado por SMS o generado por una aplicación de autenticación.

Introduce el código y accederás a tu cuenta.

## 3. Funcionamiento Básico de GitHub

### Repositorios en GitHub

GitHub es una plataforma para almacenar y gestionar proyectos de software que utilizan Git como sistema de control de versiones. Los elementos clave de GitHub incluyen:

- **Repositorios**: Espacios donde se almacenan los archivos de tu proyecto. Un repositorio puede ser público o privado.
- **Commits**: Registros de cambios realizados en los archivos de un repositorio.
- **Ramas**: Copias del repositorio donde puedes hacer cambios sin afectar la versión principal del proyecto.

### Crear un Nuevo Repositorio

1. Una vez que inicies sesión, ve a la página principal de tu cuenta de GitHub.
2. Haz clic en el botón **+** en la parte superior derecha y selecciona **New repository**.
3. Rellena los detalles del repositorio, como el nombre y la descripción. Puedes elegir entre un repositorio público o privado.
4. Haz clic en **Create repository**.

### Clonar un Repositorio

Para clonar un repositorio (hacer una copia local de uno en GitHub):

1. Ve al repositorio que deseas clonar en GitHub.
2. Haz clic en el botón verde **Code** y copia la URL (puede ser HTTPS o SSH).
3. Abre tu terminal y usa el siguiente comando para clonar el repositorio:

```bash
git clone <URL del repositorio>
```

### Hacer Commit y Push

1. Para hacer cambios en el repositorio, realiza los cambios en tu máquina local.
2. Usa `git add` para agregar los archivos al área de preparación.

```bash
git add .
```

3. Realiza un commit para guardar los cambios.

```bash
git commit -m "Descripción del cambio"
```

4. Empuja los cambios al repositorio remoto en GitHub.

```bash
git push origin master
```

