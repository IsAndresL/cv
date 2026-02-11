# Cómo subir tu proyecto a Vercel

Existen dos formas principales de subir tu sitio web a Vercel:

1.  **Conectando tu repositorio de GitHub (Recomendado)**.
2.  **Usando Vercel CLI** (desde la terminal).

Aquí te explico ambos métodos.

---

## Opción 1: Usando GitHub (La mejor opción)

Esta opción es la mejor porque cada vez que guardes cambios y los subas a GitHub (`git push`), Vercel actualizará tu sitio web automáticamente.

### Paso 1: Subir tu código a GitHub

1.  Ve a [GitHub](https://github.com) y crea un **New Repository** (Nuevo Repositorio).
2.  Ponle un nombre (ej: `mi-hoja-de-vida`) y déjalo "Public".
3.  En tu computadora, abre la terminal en la carpeta de tu proyecto y ejecuta:

```bash
git init
git add .
git commit -m "Primer commit: Sitio listo"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/TU_REPOSITORIO.git
git push -u origin main
```

_(Reemplaza `TU_USUARIO` y `TU_REPOSITORIO` con tus datos reales)_.

### Paso 2: Conectar con Vercel

1.  Ve a [Vercel.com](https://vercel.com) e inicia sesión (puedes usar tu cuenta de GitHub).
2.  En el panel principal (Dashboard), haz clic en **"Add New..."** > **"Project"**.
3.  Verás una lista de tus repositorios de GitHub. Busca `mi-hoja-de-vida` y dale al botón **Import**.
4.  En la siguiente pantalla ("Configure Project"), deja todo como está. Vercel detecta automáticamente que es un sitio HTML/CSS estático.
5.  Haz clic en **Deploy**.

¡Listo! En unos segundos tendrás un link como `mi-hoja-de-vida.vercel.app`.

---

## Opción 2: Usando Vercel CLI (Más rápido, sin GitHub)

Si no quieres usar GitHub y solo quieres subirlo ya mismo desde tu PC:

1.  Abre la terminal en la carpeta de tu proyecto.
2.  Ejecuta el siguiente comando (si tienes Node.js instalado):
    ```bash
    npx vercel
    ```
3.  La terminal te hará unas preguntas. Responde así (dale Enter a casi todo):
    - `Log in to Vercel`: Te pedirá loguearte en el navegador.
    - `Set up and deploy?`: **Y** (Yes)
    - `Which scope do you want to deploy to?`: Selecciona tu cuenta.
    - `Link to existing project?`: **N** (No)
    - `What’s your project’s name?`: (Dale Enter para usar el nombre de la carpeta o escribe uno nuevo).
    - `In which directory is your code located?`: **./** (Dale Enter).
    - `Want to modify these settings?`: **N** (No).

4.  ¡Listo! Al final te dará un link de "Production" (ej: `https://mi-proyecto.vercel.app`).

---

## Recomendación

Usa la **Opción 1 (GitHub)**. Es más profesional y te sirve como portafolio real para mostrar que sabes usar Git, lo cual es fundamental para un Ingeniero de Sistemas.
