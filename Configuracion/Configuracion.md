## 🎨 3) Configurar TailwindCSS + DaisyUI

Una vez instalado Tailwind y DaisyUI, edita el archivo `tailwind.config.js` para definir el contenido, los temas y los plugins que usará tu proyecto.

---

### 📄 Archivo: `tailwind.config.js`

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    './index.html',
    './src/**/*.{ts,tsx}',
  ],
  theme: {
    extend: {},
  },
  plugins: [require('daisyui')],
  daisyui: {
    themes: [
      {
        proyecto: {
          primary: '#2563EB',   // Azul corporativo principal
          secondary: '#1E293B', // Azul oscuro para contraste
          accent: '#22C55E',    // Verde acento (botones o indicadores)
          neutral: '#111827',   // Color base para textos y navbar
          'base-100': '#FFFFFF', // Fondo base principal
          'base-200': '#F3F4F6', // Fondo alternativo
          info: '#0EA5E9',
          success: '#22C55E',
          warning: '#F59E0B',
          error: '#EF4444',
        },
      },
      'light',
      'dark',
    ],
  },
}
```

### 🎨 Desglose del tema `proyecto`

| Variable      | Valor      | Descripción                                                |
| -------------- | ----------- | ---------------------------------------------------------- |
| `primary`      | `#2563EB`  | Azul corporativo principal (botones, acentos primarios).   |
| `secondary`    | `#1E293B`  | Azul oscuro complementario (headers o sidebars).           |
| `accent`       | `#22C55E`  | Verde brillante para elementos destacados o confirmaciones.|
| `neutral`      | `#111827`  | Color base para texto o fondo de navbar.                   |
| `base-100`     | `#FFFFFF`  | Fondo principal (superficies claras).                      |
| `base-200`     | `#F3F4F6`  | Fondo secundario para secciones o tarjetas.                |
| `info`         | `#0EA5E9`  | Color informativo (alertas o etiquetas informativas).      |
| `success`      | `#22C55E`  | Color de éxito (validaciones, confirmaciones).             |
| `warning`      | `#F59E0B`  | Color de advertencia.                                     |
| `error`        | `#EF4444`  | Color de error o peligro.                                 |


### 🧩 Explicación del archivo `tailwind.config.js`

| Propiedad            | Descripción                                                                                                                       |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **`content`**        | Define los archivos donde Tailwind buscará clases CSS. Incluye todo el código dentro de `/src` y `index.html`.                    |
| **`theme.extend`**   | Permite agregar o sobreescribir valores de diseño como colores, fuentes o tamaños.                                                |
| **`plugins`**        | Agrega extensiones adicionales; en este caso, **DaisyUI** para usar componentes con temas personalizables.                        |
| **`daisyui.themes`** | Lista los temas disponibles. Aquí se define un tema personalizado llamado `flexflow` más los temas predefinidos `light` y `dark`. |

---

## ⚙️ Archivo `postcss.config.js`

El archivo **PostCSS** define los plugins que procesarán el CSS final del proyecto.  
Se genera automáticamente al ejecutar `npx tailwindcss init -p` y es esencial para que TailwindCSS y Autoprefixer funcionen correctamente.

---

### 📄 Código base

```js
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

### 🧩 Explicación del archivo `postcss.config.js`

| Propiedad          | Descripción                                                                                                    |
| ------------------ | -------------------------------------------------------------------------------------------------------------- |
| **`tailwindcss`**  | Activa el framework **TailwindCSS**, permitiendo usar sus clases utilitarias en todo el proyecto.              |
| **`autoprefixer`** | Añade automáticamente los prefijos necesarios (`-webkit`, `-moz`, etc.) para compatibilidad entre navegadores. |

---

## 🎨 Archivo `src/index.css`

Este archivo define los estilos base del proyecto.  
Incluye las directivas principales de **TailwindCSS** y algunos estilos globales personalizados para el layout general.

---

### 📄 Código base

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

/* Estilos base opcionales */
html, body, #root { 
  height: 100%; 
}
body { 
  @apply bg-base-200 text-neutral; 
}
```

### 🧩 Explicación del archivo `src/index.css`

| Propiedad / Directiva      | Descripción                                                                                                        |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **`@tailwind base`**       | Carga los estilos base de Tailwind (normaliza márgenes, tipografía y estilos predeterminados del navegador).       |
| **`@tailwind components`** | Importa los componentes de Tailwind y DaisyUI predefinidos (botones, modales, inputs, etc.).                       |
| **`@tailwind utilities`**  | Habilita todas las clases utilitarias (`flex`, `grid`, `text-center`, `p-4`, etc.) disponibles en Tailwind.        |
| **`html, body, #root`**    | Asegura que toda la aplicación ocupe el 100% del alto de la ventana.                                               |
| **`body { @apply ... }`**  | Usa la directiva `@apply` de Tailwind para aplicar utilidades directamente en CSS (`bg-base-200`, `text-neutral`). |

---

### 🧩 Archivo ENV `.env`

```bash
VITE_API_BASE_URL=http://localhost:5050/api/v1
```

---

## ⚙️ Archivo `vite.config.ts`

El archivo `vite.config.ts` define la configuración principal del entorno de desarrollo y build del proyecto.  
Controla los **plugins**, el **servidor local**, los **alias de rutas** y variables globales para compatibilidad con librerías.

---

### 📄 Código base

```ts
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  server: {
    port: 5173,           // Puedes cambiarlo si lo necesitas
    open: true,           // Abre automáticamente en el navegador
  },
  define: {
    'process.env': {}     // Evita errores con librerías que usan process.env
  },
  resolve: {
    alias: {
      '@': '/src',        // Para importar con @/ en lugar de rutas largas
    },
  },
})
```

### 🧩 Explicación del archivo `vite.config.ts`

| Propiedad           | Descripción                                                                                                          |
| ------------------- | -------------------------------------------------------------------------------------------------------------------- |
| **`plugins`**       | Define los complementos que usará Vite. Aquí se incluye `@vitejs/plugin-react` para soporte completo de React y JSX. |
| **`server`**        | Configura el servidor de desarrollo local (`vite dev`). Permite definir puerto, CORS, apertura automática, etc.      |
| **`define`**        | Agrega variables globales. Aquí se usa `'process.env': {}` para evitar errores con librerías que esperan Node.js.    |
| **`resolve.alias`** | Crea atajos para rutas. El alias `@` apunta a `/src`, facilitando importaciones como `@/components/Button`.          |

---

## Home

👉 [Home](./../README.md)
👉 [Tipos](./../src/types/Empleado.md)