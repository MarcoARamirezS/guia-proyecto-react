## 🌐 Archivo `services/api.ts`

Este archivo configura **Axios** como cliente HTTP global para todo el frontend.  
Centraliza la URL base de la API, agrega el token JWT a las peticiones, y maneja automáticamente errores de autenticación (401).

---

### 📄 Código base

```ts
import axios from "axios";

export const api = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL
})

api.interceptors.request.use((config) => {
  const token = localStorage.getItem('token')
  if (token) {
    config.headers = config.headers || {}
    config.headers.Authorization = `Bearer ${token}`
  }
  return config
})

api.interceptors.response.use(
  (res) => res,
  (err) => {
    if (err?.response?.status === 401) {
      localStorage.removeItem('token')
      window.location.href = '/login'
    }
    return Promise.reject(err)
  }
)
```

---

### 🌐 Elementos y funciones del archivo `services/api.ts`

| Elemento / Función                    | Descripción                                                                                                           |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **`axios.create()`**                  | Crea una instancia personalizada de Axios con configuración base (por ejemplo, `baseURL`).                            |
| **`baseURL`**                         | Se obtiene de `import.meta.env.VITE_API_BASE_URL`, definida en el archivo `.env`.                                     |
| **`interceptors.request.use()`**      | Intercepta cada petición saliente y agrega el encabezado `Authorization: Bearer <token>` si existe en `localStorage`. |
| **`interceptors.response.use()`**     | Escucha todas las respuestas. Si recibe un error `401`, elimina el token y redirige al usuario a `/login`.            |
| **`localStorage.getItem('token')`**   | Obtiene el token JWT almacenado localmente tras el inicio de sesión.                                                  |
| **`window.location.href = '/login'`** | Redirige manualmente al usuario al formulario de inicio de sesión cuando el token es inválido o ha expirado.          |
| **`Promise.reject(err)`**             | Devuelve el error para que el flujo del programa pueda capturarlo con `.catch()` o `try/catch`.                       |

---

## Home

👉 [Home](./../../README.md)