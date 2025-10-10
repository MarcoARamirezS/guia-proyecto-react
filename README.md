# ⚛️ Frontend React + TailwindCSS v3 + DaisyUI v4  
**Con rutas públicas/protegidas, layouts y módulo Empleados**

Este documento te guía paso a paso desde la instalación hasta dejar todo funcionando.  
Incluye la estructura de carpetas y archivos fuente listos para copiar/pegar.

---

## 🔗 Backend base
- **URL:** `http://localhost:5050/api/v1`

### 🛣️ Rutas disponibles
| Método | Ruta                          | Descripción                  |
|-------:|-------------------------------|------------------------------|
| POST   | `/empleados/create`           | Crear empleado               |
| POST   | `/empleados/login`            | Iniciar sesión               |
| GET    | `/empleados/getall`           | Listar empleados             |
| PUT    | `/empleados/update/:id`       | Actualizar empleado          |
| DELETE | `/empleados/delete/:id`       | Eliminar empleado            |

---

## 1) ✅ Requisitos

- **Node.js 18+** *(recomendado **20+**)*
- **npm 9+** *(o **pnpm** / **yarn**)*

> Verifica tu entorno:
```bash
node -v
npm -v
```

---

## Guia de Instalación

- 👉 [Creación e Instalación de Dependencias](./Instalacion/Dependencias.md)
- 👉 [Estructura del Proyecto](./Estructura/Estructura.md)
- 👉 [Configuración del Proyecto](./Configuracion/Configuracion.md)