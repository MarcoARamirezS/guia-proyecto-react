# 🧭 Estructura del Proyecto — Frontend Empleados

Proyecto **React + TypeScript + TailwindCSS + DaisyUI**  
con rutas públicas/protegidas, layouts reutilizables y un módulo completo para **gestionar empleados**.

---

## 📂 Estructura general

```plaintext
frontend-empleados/
├─ .env
├─ index.html
├─ package.json
├─ postcss.config.js
├─ tailwind.config.js
├─ tsconfig.json
└─ src/
   ├─ index.css
   ├─ main.tsx
   ├─ App.tsx
   ├─ router/
   │  ├─ ProtectedRoute.tsx
   │  └─ PublicRoute.tsx
   ├─ layouts/
   │  ├─ AuthLayout.tsx
   │  └─ DashboardLayout.tsx
   ├─ components/
   │  ├─ Sidebar.tsx
   │  └─ ui/
   │     ├─ Button.tsx
   │     ├─ Input.tsx
   │     └─ FormError.tsx
   ├─ pages/
   │  ├─ auth/
   │  │  ├─ Login.tsx
   │  │  └─ Register.tsx
   │  ├─ dashboard/
   │  │  └─ Home.tsx
   │  └─ empleados/
   │     ├─ EmpleadosList.tsx
   │     └─ EmpleadoForm.tsx
   ├─ services/
   │  ├─ api.ts
   │  └─ empleados.service.ts
   ├─ hooks/
   │  └─ useAuth.ts
   ├─ context/
   │  └─ AuthContext.tsx
   └─ types/
      └─ empleado.ts
```

---

### 🧭 Estructura general del proyecto

| Ruta / Archivo            | Descripción                                                                                                                      |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **`frontend-empleados/`** | Carpeta raíz del proyecto React creado con Vite. Contiene configuración, dependencias y código fuente.                           |
| **`.env`**                | Archivo de variables de entorno accesibles desde el frontend (solo las que comienzan con `VITE_`). Ejemplo: `VITE_API_BASE_URL`. |
| **`index.html`**          | Archivo HTML principal donde Vite inyecta tu aplicación React. Solo debe contener el `<div id="root"></div>`.                    |
| **`package.json`**        | Define dependencias, scripts (`npm run dev`, `npm run build`), nombre y versión del proyecto.                                    |
| **`postcss.config.js`**   | Configuración de PostCSS que usa TailwindCSS y Autoprefixer para procesar tus estilos.                                           |
| **`tailwind.config.js`**  | Configura Tailwind y DaisyUI (colores, temas, paths, etc.). Personaliza la UI de todo el proyecto.                               |
| **`tsconfig.json`**       | Configura TypeScript: rutas, strict mode, target, alias, etc.                                                                    |
| **`vite.config.js`**      | Configura Vite (plugins, alias `@`, puerto, entorno). Permite importar archivos como `@/components/...`.                         |


### 📁 Estructura de la carpeta `src/`

| Carpeta / Archivo         | Descripción                                                                                                              |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **`src/index.css`**       | Estilos globales del proyecto. Importa `@tailwind base`, `@tailwind components`, y `@tailwind utilities`.                |
| **`src/main.tsx`**        | Punto de entrada del frontend. Monta la app React dentro del `#root` de `index.html`.                                    |
| **`src/App.tsx`**         | Define el sistema de rutas (`react-router-dom`), layouts y componentes principales.                                      |
| **`src/router/`**         | Contiene las rutas protegidas y públicas.                                                                                |
| ├─ `ProtectedRoute.tsx`   | Bloquea acceso a usuarios no autenticados. Redirige a `/login` si no hay token.                                          |
| └─ `PublicRoute.tsx`      | Evita que usuarios autenticados accedan a páginas públicas (por ejemplo `/login`, `/register`).                          |
| **`src/layouts/`**        | Define los **layouts** (estructuras visuales principales) para diferentes secciones de la app.                           |
| ├─ `AuthLayout.tsx`       | Layout para las páginas públicas (login/register). Centra el contenido en pantalla.                                      |
| └─ `DashboardLayout.tsx`  | Layout para la zona protegida (dashboard). Incluye menú lateral y botón “Cerrar sesión”.                                 |
| **`src/components/`**     | Componentes reutilizables de UI y navegación.                                                                            |
| ├─ `Sidebar.tsx`          | Menú lateral con navegación a secciones del dashboard (Inicio, Empleados, Logout, etc.).                                 |
| └─ `ui/`                  | Componentes reutilizables de interfaz visual.                                                                            |
|   ├─ `Button.tsx`         | Botón con estilo DaisyUI, soporte de loading (`spinner`).                                                                |
|   ├─ `Input.tsx`          | Input de formulario con label y mensaje de error integrado.                                                              |
|   └─ `FormError.tsx`      | Muestra mensajes de error generales dentro de formularios.                                                               |
| **`src/pages/`**          | Páginas o vistas del sistema, organizadas por módulo.                                                                    |
| ├─ `auth/`                | Páginas públicas relacionadas con autenticación.                                                                         |
|   ├─ `Login.tsx`          | Formulario de inicio de sesión (envía usuario/contraseña al backend).                                                    |
|   └─ `Register.tsx`       | Formulario de registro de nuevos empleados (usa el endpoint `/empleados/create`).                                        |
| ├─ `dashboard/`           | Páginas del área privada del sistema.                                                                                    |
|   └─ `Home.tsx`           | Página principal del panel, muestra mensaje de bienvenida.                                                               |
| └─ `empleados/`           | Páginas del módulo de empleados.                                                                                         |
|   ├─ `EmpleadosList.tsx`  | Tabla con CRUD (listar, crear, editar, borrar empleados).                                                                |
|   └─ `EmpleadoForm.tsx`   | Formulario dentro de modal para crear/editar empleados.                                                                  |
| **`src/services/`**       | Capa de comunicación con el backend vía Axios.                                                                           |
| ├─ `api.ts`               | Configura Axios: `baseURL`, interceptores de token, manejo de errores 401.                                               |
| └─ `empleados.service.ts` | Métodos CRUD (`getAll`, `create`, `update`, `remove`) para la colección `empleados`.                                     |
| **`src/hooks/`**          | Hooks personalizados.                                                                                                    |
| └─ `useAuth.ts`           | Devuelve el contexto de autenticación (`useContext(AuthContext)`), con estado `isAuthenticated`, `login`, `logout`, etc. |
| **`src/context/`**        | Define contextos globales React (similar a Redux).                                                                       |
| └─ `AuthContext.tsx`      | Maneja login/logout, token JWT, decodifica usuario, y mantiene sesión en `localStorage`.                                 |
| **`src/types/`**          | Define los tipos TypeScript para mayor seguridad en datos.                                                               |
| └─ `empleado.ts`          | Tipos `Empleado`, `CreateEmpleadoDto`, `UpdateEmpleadoDto` — usados en servicios, formularios y componentes.             |


### 🧠 Organización por módulos funcionales

| Módulo                       | Responsabilidad                                                                               |
| ---------------------------- | --------------------------------------------------------------------------------------------- |
| **Autenticación**            | `AuthLayout`, `Login`, `Register`, `AuthContext`, `useAuth`, `PublicRoute`, `ProtectedRoute`. |
| **Dashboard**                | `DashboardLayout`, `Sidebar`, `Home`, `EmpleadosList`, `EmpleadoForm`.                        |
| **Servicios**                | `api.ts` (Axios global) y `empleados.service.ts` (CRUD).                                      |
| **UI Reutilizable**          | `Button`, `Input`, `FormError`.                                                               |
| **Gestión de Estado Global** | `AuthContext` (mantiene token y usuario decodificado).                                        |


---


## Home

👉 [Home](./../README.md)
👉 [Configuración](./../Configuracion/Configuracion.md)