# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) (or [oxc](https://oxc.rs) when used in [rolldown-vite](https://vite.dev/guide/rolldown)) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.

# Añadido por mi pafra la explicacion de mi codigo 

# Kanban React con Autenticación Google

Aplicación Kanban desarrollada con React que permite gestionar tareas mediante columnas y autenticación con Google One Tap.

Este proyecto está basado en una estructura Kanban en React y ampliado con autenticación OAuth 2.0 usando Google Identity Services.

---

# Características

- Gestión de tareas tipo Kanban
- Drag & Drop de tareas
- Persistencia de tareas en localStorage
- Inicio de sesión con Google One Tap
- Manejo de JWT con `jwt-decode`
- Persistencia de sesión de usuario
- Protección del tablero para usuarios autenticados
- Asociación automática del autor a cada tarea
- Cierre de sesión

---

# Tecnologías utilizadas

- React
- Vite
- Context API
- localStorage
- Google One Tap
- JWT
- OAuth 2.0

---

# Instalación

Clonar el repositorio:

```bash
git clone https://github.com/alvaro34256manrubia-design/kanban-react.git
```

Entrar en el proyecto:

```bash
cd kanban-react
```

Instalar dependencias:

```bash
npm install
```

Instalar dependencias necesarias para autenticación:

```bash
npm install google-one-tap jwt-decode
```

Iniciar el servidor:

```bash
npm run dev
```

---

# Configuración de Google OAuth

Para que Google One Tap funcione correctamente es necesario configurar un proyecto en Google Cloud Console.

## Pasos

### 1. Crear proyecto

Ir a:

https://console.cloud.google.com/

---

### 2. Configurar OAuth Consent Screen

- Tipo: External
- Completar nombre de aplicación
- Añadir correo

---

### 3. Crear credenciales OAuth

Ir a:

```txt
APIs & Services
→ Credentials
→ Create Credentials
→ OAuth Client ID
```

Seleccionar:

```txt
Web Application
```

---

### 4. Authorized JavaScript origins

Añadir:

```txt
http://localhost
http://localhost:5173
```

---

### 5. Obtener CLIENT_ID

Google generará un CLIENT_ID parecido a:

```txt
123456789-xxxxx.apps.googleusercontent.com
```

---

# Configuración en React

En `App.jsx`:

```jsx
googleOneTap({
  client_id: "TU_CLIENT_ID_GOOGLE",
});
```

Reemplazar:

```txt
TU_CLIENT_ID_GOOGLE
```

por el CLIENT_ID generado.

---

# Estructura del proyecto

```txt
src/
│
├── components/
│   ├── UserProfile.jsx
│   ├── Header.jsx
│   └── ...
│
├── context/
│   ├── TaskContext.jsx
│   └── AuthContext.jsx
│
├── App.jsx
├── main.jsx
└── ...
```

---

# Funcionalidades implementadas

## Autenticación Google One Tap

La aplicación muestra automáticamente la ventana One Tap al cargar la página.

---

## Manejo de JWT

Se utiliza:

```bash
jwt-decode
```

para extraer:

- nombre
- email
- imagen de perfil

del token JWT devuelto por Google.

---

## Persistencia de sesión

El usuario autenticado se almacena en:

```js
localStorage
```

permitiendo mantener la sesión activa tras refrescar la página.

---

## Protección del tablero

Si el usuario no está autenticado:

- el Kanban no se muestra
- aparece un mensaje solicitando iniciar sesión

---

## Asociación de autor a tareas

Cada tarea creada almacena automáticamente:

```txt
author: user.name
```

---

# Scripts disponibles

Iniciar entorno de desarrollo:

```bash
npm run dev
```

Build producción:

```bash
npm run build
```

Preview build:

```bash
npm run preview
```

---

# Dependencias principales

```json
{
  "google-one-tap": "^1.x",
  "jwt-decode": "^4.x"
}
```

---

# Objetivos académicos cumplidos

- Implementación Google One Tap
- Integración OAuth 2.0
- Manejo de JWT
- Persistencia de sesión
- Protección de rutas
- Context API
- Gestión de estado global
- Persistencia con localStorage

---

# Referencias

## Google Identity Services

https://developers.google.com/identity/gsi/web

## JWT

https://jwt.io/

## React Context API

https://react.dev/reference/react/useContext

## MDN localStorage

https://developer.mozilla.org/es/docs/Web/API/Window/localStorage

---

# Autor

Proyecto desarrollado por Álvaro Manrubia para la práctica de Kanban con autenticación Google en React.