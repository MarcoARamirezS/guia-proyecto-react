## ⚙️ Crea el proyecto e instala dependencias

Este bloque detalla la creación inicial del proyecto con **Vite + React + TypeScript**,  
así como la instalación de las dependencias necesarias para la ejecución y el entorno de estilos con **TailwindCSS** y **DaisyUI**.

---

### 🏗️ **1. Crear el proyecto base**

```bash
# Crear un nuevo proyecto React + TypeScript con Vite
npm create vite@latest frontend-empleados -- --template react-ts

# Entrar en la carpeta del proyecto
cd frontend-empleados
```

---

## 🧩 Explicación:

- vite@latest → descarga la versión más reciente de Vite, un empaquetador moderno y rápido.

- --template react-ts → configura el proyecto con React + TypeScript desde el inicio.

- El nombre del proyecto será frontend-empleados, aunque puedes cambiarlo libremente.

## ⚛️ 2. Instalar dependencias de ejecución (runtime)

---

```bash
npm i react-router-dom axios jwt-decode zod
```

### 🧠 Explicación — Dependencias de ejecución (runtime)

| Paquete                | Función                                                                       |
| ---------------------- | ----------------------------------------------------------------------------- |
| **`react-router-dom`** | Maneja las rutas y navegación entre páginas (Login, Dashboard, etc.).         |
| **`axios`**            | Cliente HTTP para comunicar el frontend con el backend (`/api/v1/empleados`). |
| **`jwt-decode`**       | Permite decodificar tokens JWT y obtener información del usuario.             |
| **`zod`**              | Biblioteca para validar esquemas y formularios con tipado TypeScript.         |

---

## 🎨 3. Instalar TailwindCSS + DaisyUI

```bash
npm i -D tailwindcss@3 postcss autoprefixer daisyui@4
npx tailwindcss init -p
```

### 🎨 Explicación — TailwindCSS + DaisyUI

| Paquete                       | Tipo          | Función                                                                                          |
| ----------------------------- | ------------- | ------------------------------------------------------------------------------------------------ |
| **`tailwindcss@3`**           | DevDependency | Framework CSS basado en utilidades, rápido y personalizable.                                     |
| **`postcss`**                 | DevDependency | Permite procesar CSS y agregar compatibilidad entre navegadores.                                 |
| **`autoprefixer`**            | DevDependency | Añade automáticamente prefijos CSS (`-webkit`, `-moz`, etc.).                                    |
| **`daisyui@4`**               | DevDependency | Plugin UI para Tailwind con componentes predefinidos y temas personalizables.                    |
| **`npx tailwindcss init -p`** | —             | Genera los archivos `tailwind.config.js` y `postcss.config.js` necesarios para la configuración. |

---

## Home

👉 [Home](./../README.md)