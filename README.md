# Frontend - Gestión de Tareas# React + TypeScript + Vite



Aplicación frontend construida con React, TypeScript y Vite, desplegada en AWS S3 + CloudFront.This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.



## 🚀 TecnologíasCurrently, two official plugins are available:



- **React 18.x**- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh

- **TypeScript** - Tipado estático- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

- **Vite** - Build tool y dev server

- **React Router** - Navegación## Expanding the ESLint configuration

- **Axios** - Cliente HTTP

- **AWS S3** - Hosting de archivos estáticosIf you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

- **CloudFront** - CDN

- **Terraform** - Infraestructura como código```js

export default tseslint.config({

## 📋 Requisitos Previos  extends: [

    // Remove ...tseslint.configs.recommended and replace with this

- Node.js 20.x o superior    ...tseslint.configs.recommendedTypeChecked,

- AWS CLI configurado    // Alternatively, use this for stricter rules

- Terraform 1.6.0 o superior    ...tseslint.configs.strictTypeChecked,

- Cuenta de AWS    // Optionally, add this for stylistic rules

    ...tseslint.configs.stylisticTypeChecked,

## 🛠️ Configuración Local  ],

  languageOptions: {

### 1. Instalar dependencias    // other options...

    parserOptions: {

```bash      project: ['./tsconfig.node.json', './tsconfig.app.json'],

npm install      tsconfigRootDir: import.meta.dirname,

```    },

  },

### 2. Configurar variables de entorno})

```

Crea un archivo `.env` con la URL de tu API:

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```env

VITE_API_URL=http://localhost:3000```js

```// eslint.config.js

import reactX from 'eslint-plugin-react-x'

Para producción, usa la URL del API Gateway de AWS.import reactDom from 'eslint-plugin-react-dom'



### 3. Ejecutar en modo desarrolloexport default tseslint.config({

  plugins: {

```bash    // Add the react-x and react-dom plugins

npm run dev    'react-x': reactX,

```    'react-dom': reactDom,

  },

La aplicación estará disponible en `http://localhost:5173`  rules: {

    // other rules...

## 🏗️ Build y Deploy    // Enable its recommended typescript rules

    ...reactX.configs['recommended-typescript'].rules,

### Build local    ...reactDom.configs.recommended.rules,

  },

```bash})

npm run build```

```

### Deploy a AWS

El deploy se ejecuta automáticamente mediante GitHub Actions cuando haces push a la rama `main`.

## 🔐 Secrets de GitHub

Configura los siguientes secrets en tu repositorio de GitHub:

### AWS Credentials
- `AWS_ACCESS_KEY_ID` - Access Key ID de AWS
- `AWS_SECRET_ACCESS_KEY` - Secret Access Key de AWS

### Variables de Entorno
- `VITE_API_URL` - URL del API Gateway (ej: `https://xxxxxx.execute-api.us-east-1.amazonaws.com`)

## 📁 Estructura del Proyecto

```
frontend/
├── src/
│   ├── components/
│   │   ├── atoms/          # Componentes básicos (Button, Input, etc)
│   │   ├── molecules/      # Componentes compuestos (Forms, Cards)
│   │   ├── organisms/      # Secciones complejas (TaskList)
│   │   └── templates/      # Layouts de páginas
│   ├── pages/              # Páginas de la aplicación
│   ├── services/           # Servicios API
│   ├── types/              # Tipos de TypeScript
│   ├── App.tsx             # Componente principal
│   └── main.tsx            # Punto de entrada
├── terraform/              # Infraestructura como código
│   ├── s3.tf              # Bucket S3
│   ├── cloudfront.tf      # Distribución CloudFront
│   └── ...
├── public/                 # Archivos estáticos
└── .github/
    └── workflows/
        └── deploy.yml      # Pipeline CI/CD
```

## 🎨 Componentes

### Atoms
- **Button** - Botón reutilizable con variantes
- **Input** - Campo de entrada con validación
- **Modal** - Modal genérico
- **ThemeToggle** - Selector de tema claro/oscuro

### Molecules
- **LoginForm** - Formulario de inicio de sesión
- **RegisterForm** - Formulario de registro
- **TaskForm** - Formulario de creación de tareas
- **EditTaskForm** - Formulario de edición de tareas
- **TaskCard** - Tarjeta individual de tarea

### Organisms
- **TaskList** - Lista de tareas con filtros

### Templates
- **AuthTemplate** - Layout para páginas de autenticación
- **DashboardTemplate** - Layout para el dashboard

### Pages
- **LoginPage** - Página de inicio de sesión
- **RegisterPage** - Página de registro
- **DashboardPage** - Página principal con tareas

## 🧪 Testing

```bash
npm test
```

## 📦 Infraestructura AWS

La infraestructura incluye:

- **S3 Bucket**: Hosting de archivos estáticos
- **CloudFront Distribution**: CDN global con HTTPS
- **Cache Policy**: Optimización de cache para assets
- **OAI**: Origin Access Identity para seguridad

## 🔄 CI/CD Pipeline

El pipeline de GitHub Actions:

1. Instala dependencias
2. Compila la aplicación con Vite
3. Despliega infraestructura con Terraform
4. Sincroniza archivos build con S3
5. Invalida cache de CloudFront
6. Muestra la URL del sitio web

## 🌐 Características

- ✅ Autenticación con JWT
- ✅ CRUD completo de tareas
- ✅ Estados de tareas (pendiente, en progreso, completada)
- ✅ Prioridades de tareas (baja, media, alta)
- ✅ Tema claro/oscuro
- ✅ Diseño responsive
- ✅ Validación de formularios
- ✅ Manejo de errores
- ✅ Loading states

## 🎯 Funcionalidades de Tareas

- **Crear**: Añadir nuevas tareas con título, descripción, prioridad
- **Leer**: Ver lista de todas las tareas
- **Actualizar**: Editar tareas existentes, cambiar estado
- **Eliminar**: Borrar tareas completadas o no deseadas
- **Filtrar**: Filtrar por estado o prioridad

## 🔒 Seguridad

- Tokens JWT almacenados de forma segura
- Refresh tokens para sesiones persistentes
- Validación de entrada en formularios
- Protección de rutas autenticadas
- HTTPS en producción con CloudFront

## 📝 Notas Importantes

- El estado de Terraform se guarda localmente (considera usar S3 backend para producción)
- CloudFront puede tardar 15-20 minutos en propagarse globalmente
- La invalidación de cache es instantánea pero tiene costo después de las primeras 1000 al mes
- Los assets tienen hash en el nombre para cache-busting automático

## 🤝 Contribuir

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📄 Licencia

ISC
