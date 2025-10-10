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

## Home

👉 [Home](./../README.md)
👉 [Configuración](./../Configuracion/Configuracion.md)