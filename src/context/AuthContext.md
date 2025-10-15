## 🔐 Archivo `context/AuthContext.tsx`

Este archivo define el **contexto global de autenticación** del sistema.  
Proporciona un estado centralizado para manejar el token JWT, el usuario autenticado, y las funciones de login/logout.

---

### 📄 Código base

```tsx
import { createContext, useEffect, useMemo, useState } from 'react'
import { jwtDecode } from 'jwt-decode'
import { api } from '../services/api'

type User = { id: string; usuario: string; nombre: string }

type AuthContextType = {
  token: string | null
  user: User | null
  isAuthenticated: boolean
  login: (usuario: string, password: string) => Promise<void>
  logout: () => void
}

export const AuthContext = createContext<AuthContextType>({
  token: null,
  user: null,
  isAuthenticated: false,
  login: async () => {},
  logout: () => {},
})

export function AuthProvider({ children }: { children: React.ReactNode }) {
  const [token, setToken] = useState<string | null>(() => localStorage.getItem('token'))
  const [user, setUser] = useState<User | null>(null)

  useEffect(() => {
    if (token) {
      try {
        const decoded = jwtDecode<User>(token)
        setUser(decoded)
        localStorage.setItem('token', token)
      } catch (e) {
        console.log('@@@ error => ', e)
        setUser(null)
        localStorage.removeItem('token')
      }
    } else {
      setUser(null)
      localStorage.removeItem('token')
    }
  }, [token])

  const login = async (usuario: string, password: string) => {
    const { data } = await api.post('/empleados/login', { usuario, password })
    if (!data?.ok || !data?.token) {
      throw new Error(data?.message || 'Credenciales inválidas')
    }
    setToken(data.token)
  }

  const logout = () => {
    setToken(null)
  }

  const value = useMemo(() => ({
    token,
    user,
    isAuthenticated: Boolean(token),
    login,
    logout,
  }), [token, user])

  return (
    <AuthContext.Provider value={value}>
      {children}
    </AuthContext.Provider>
  )
}
```

---

### 🔐 Propiedades y funciones del `AuthContext`

| Propiedad / Función            | Tipo                                                   | Descripción                                                                                |
| ------------------------------ | ------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **`token`**                    | `string \| null`                                       | Token JWT del usuario autenticado. Se guarda en `localStorage` y se usa en peticiones API. |
| **`user`**                     | `User \| null`                                         | Información decodificada del usuario (`id`, `usuario`, `nombre`).                          |
| **`isAuthenticated`**          | `boolean`                                              | Indica si el usuario tiene sesión activa (`true` si existe token válido).                  |
| **`login(usuario, password)`** | `(usuario: string, password: string) => Promise<void>` | Envía credenciales al backend (`/empleados/login`) y guarda el token devuelto.             |
| **`logout()`**                 | `() => void`                                           | Cierra la sesión eliminando el token y el estado del usuario.                              |
| **`AuthProvider`**             | `React.FC<{ children: React.ReactNode }>`              | Componente que provee el contexto a toda la aplicación.                                    |
| **`useEffect`**                | —                                                      | Monitorea cambios en el token y decodifica el usuario automáticamente.                     |
| **`useMemo`**                  | —                                                      | Memoriza el valor del contexto para evitar renders innecesarios.                           |

---

## Home

👉 [Home](./../../README.md)
👉 [Services](./../services/)