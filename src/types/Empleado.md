## 🧾 Archivo `types/empleado.ts`

Este archivo define los **tipos TypeScript** utilizados en el módulo de empleados.  
Los tipos ayudan a garantizar la integridad de los datos en formularios, servicios y componentes React.

---

### 📄 Código base

```ts
export type Empleado = {
  id: string
  nombre: string
  apaterno: string
  amaterno: string
  direccion: string
  telefono: string
  ciudad: string
  estado: string
  usuario: string
  rol: string
  [k: string]: any
}

export type CreateEmpleadoDto = {
  id: string
  nombre: string
  apaterno: string
  amaterno: string
  direccion: string
  telefono: string
  ciudad: string
  estado: string
  usuario: string
  password: string
  rol: string
}

export type UpdateEmpleado = Partial<Omit<CreateEmpleadoDto, 'password'>> & { password?: string }
```

---

### ⚙️ Tipos definidos en `types/empleado.ts`

| Tipo                    | Descripción                                                                                                       |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **`Empleado`**          | Representa la estructura general del empleado tal como se obtiene del backend. Incluye todos los campos visibles. |
| **`CreateEmpleadoDto`** | Define los datos necesarios para crear un nuevo empleado. Incluye `password` como campo obligatorio.              |
| **`UpdateEmpleado`**    | Tipo derivado que permite actualizar solo campos parciales del empleado. `password` es opcional.                  |
| **`[k: string]: any`**  | Permite incluir propiedades adicionales dinámicas (útil para extensiones o campos calculados).                    |

---

## Home

👉 [Home](./../../README.md)
👉 [Context](./../context/AuthContext.md)