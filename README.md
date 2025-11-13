# Frontend - Gestión de Tareas# React + TypeScript + Vite

Aplicación frontend construida con React, TypeScript y Vite. Este proyecto se implementa en AWS (S3 + CloudFront) mediante Terraform y GitHub Actions.

## 🚀 Tecnologías

- **React 18.x**
- **TypeScript**
- **Vite**
- **React Router**
- **Axios**
- **ESLint**
- **AWS S3**
- **CloudFront**
- **Terraform**

## 📋 Requisitos previos

- `Node.js` 18.x o superior
- `npm` o `pnpm`
- `AWS CLI` configurado (opcional para despliegues manuales)
- `Terraform` 1.6.0 o superior (si vas a gestionar infraestructura)
- Cuenta de AWS con permisos para S3, CloudFront y (opcional) IAM

## 🛠️ Configuración local

1. Instala dependencias:

```bash
npm install
```

2. Crea un archivo `.env` en la raíz con la URL de la API:

```
VITE_API_URL=http://localhost:3000
```

3. Ejecuta el servidor de desarrollo:

```bash
npm run dev
```

La aplicación estará disponible en `http://localhost:5173`.

## 🏗️ Build y deploy

Construir la aplicación:

```bash
npm run build
```

El despliegue se puede automatizar con GitHub Actions. En este repositorio, el flujo de trabajo por defecto despliega cuando se hace push a la rama `main`.

### Secrets de GitHub necesarios para el deploy

- `AWS_ACCESS_KEY_ID` — Access Key ID de AWS
- `AWS_SECRET_ACCESS_KEY` — Secret Access Key de AWS

## 📁 Estructura del proyecto

```
src/
├── components/
│   ├── atoms/
│   ├── molecules/
│   ├── organisms/
│   └── templates/
├── pages/
├── services/
├── types/
├── App.tsx
└── main.tsx
terraform/
public/
```

## 🎨 Componentes principales

- Atoms: `Button`, `Input`, `Modal`, `ThemeToggle`
- Molecules: `LoginForm`, `RegisterForm`, `TaskForm`, `EditTaskForm`, `TaskCard`
- Organisms: `TaskList`
- Templates: `AuthTemplate`, `DashboardTemplate`
- Pages: `LoginPage`, `RegisterPage`, `DashboardPage`

## 🧪 Pruebas

Ejecuta las pruebas unitarias:

```bash
npm test
```

## 📦 Infraestructura (AWS)

La infraestructura incluida en `terraform/` gestiona:

- Un bucket S3 para alojar los archivos estáticos
- Una distribución CloudFront para CDN y HTTPS
- Políticas de cache optimizadas para assets
- (Opcional) OAI para restringir acceso al bucket

## 🔄 CI/CD

El pipeline de GitHub Actions generalmente realiza:

1. Instalar dependencias
2. Compilar la aplicación con Vite
3. Aplicar cambios de infraestructura con Terraform (opcional)
4. Sincronizar el `build/` con el bucket S3
5. Invalidar la caché de CloudFront

## 🌐 Funcionalidades principales

- Autenticación con JWT
- CRUD completo de tareas
- Estados de tareas: pendiente, en progreso, completada
- Prioridades de tareas: baja, media, alta
- Tema claro/oscuro y diseño responsive

## 🎯 Acciones sobre tareas

- Crear: añadir nuevas tareas con título, descripción y prioridad
- Leer: listar tareas
- Actualizar: editar tareas y cambiar su estado
- Eliminar: eliminar tareas
- Filtrar: filtrar por estado o prioridad

## 🔒 Seguridad

- Tokens JWT almacenados de forma segura
- Uso de refresh tokens para sesiones persistentes
- Validación de entradas en formularios
- Rutas protegidas para usuarios autenticados
- HTTPS en producción (via CloudFront)

## 📝 Notas importantes

- Considerar usar un backend remoto para el estado de Terraform (ej. S3) en entornos de equipo
- CloudFront puede tardar varios minutos en propagarse
- Las invalidaciones de CloudFront tienen coste después de cierto número

