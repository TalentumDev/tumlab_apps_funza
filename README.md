# Tumlab API Frontend

Este es un proyecto [Next.js](https://nextjs.org) creado con [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app).

---

## Tabla de Contenidos
- [Introducción](#introducción)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Requisitos Previos](#requisitos-previos)
- [Ejecución en Local](#ejecución-en-local)
- [Ejecución con Docker](#ejecución-con-docker)
- [Ejecución con Docker Compose](#ejecución-con-docker-compose)
- [Problemas Comunes](#problemas-comunes)
- [Recursos Adicionales](#recursos-adicionales)

---

## Introducción

Este proyecto es el frontend de Tumlab, una aplicación construida con Next.js. Proporciona una interfaz para interactuar con el backend y gestionar diversas funcionalidades.

---

## Estructura del Proyecto

La estructura de carpetas del proyecto es la siguiente:

```plaintext
tumlab-api-frontend/
├── app/                     # Directorio principal de páginas y rutas
│   ├── [lang]/              # Rutas dinámicas basadas en el idioma
│   ├── layout.tsx           # Layout principal de la aplicación
│   └── page.tsx             # Página principal
├── components/              # Componentes reutilizables
│   ├── NavbarPublic/        # Navbar público
│   ├── ListApps/            # Listado de aplicaciones
│   ├── Combobox/            # Selector de idioma
│   └── ui/                  # Componentes de UI (botones, popovers, etc.)
├── public/                  # Archivos estáticos (imágenes, fuentes, etc.)
├── styles/                  # Archivos de estilos globales
├── auth.ts                  # Configuración de autenticación
├── auth.config.ts           # Configuración adicional de autenticación
├── docker-compose.yml       # Configuración de Docker Compose
├── Dockerfile               # Configuración de Docker
├── README.md                # Documentación del proyecto
└── package.json             # Dependencias y scripts del proyecto
```

---

## Requisitos Previos

Antes de comenzar, asegúrate de tener instalados los siguientes programas:

- [Node.js](https://nodejs.org/) (versión 16 o superior)
- [npm](https://www.npmjs.com/) o [yarn](https://yarnpkg.com/)
- [Docker](https://www.docker.com/) y [Docker Compose](https://docs.docker.com/compose/)

---

## Ejecución en Local

Sigue estos pasos para ejecutar el proyecto en tu máquina local:

1. Clona el repositorio:
   ```bash
   git clone https://github.com/tu-usuario/tumlab-api-frontend.git
   cd tumlab-api-frontend
   ```

2. Instala las dependencias:
   ```bash
   npm install
   # o
   yarn install
   ```

3. Crea un archivo `.env.local` en la raíz del proyecto y configura las variables de entorno necesarias.

4. Inicia el servidor de desarrollo:
   ```bash
   npm run dev
   # o
   yarn dev
   ```

5. Abre [http://localhost:3000](http://localhost:3000) en tu navegador para ver la aplicación.

---

## Ejecución con Docker

Sigue estos pasos para construir y ejecutar el proyecto con Docker:

1. Construye la imagen de Docker:
   ```bash
   docker build -t tumlab-api-frontend:1.0.0 .
   ```

2. Ejecuta el contenedor:
   ```bash
   docker run -p 3000:3000 tumlab-api-frontend:1.0.0
   ```

3. Accede a la aplicación en [http://localhost:3000](http://localhost:3000).

### Vincular contenedores

Si necesitas conectar este contenedor con otros (como el backend), puedes usar una red de Docker:

```bash
docker network create tumlab-network
docker network connect tumlab-network tumlab_api
docker network connect tumlab-network tumlab-api-frontend
```

---

## Ejecución con Docker Compose

Si prefieres usar Docker Compose para gestionar los contenedores, sigue estos pasos:

1. Construye y ejecuta los contenedores:
   ```bash
   docker-compose up --build
   ```

2. Accede a la aplicación en [http://localhost:3000](http://localhost:3000).

---

## Problemas Comunes

### Problema de CORS con el Backend
Si encuentras problemas de CORS al interactuar con el backend, puedes probar el siguiente comando para verificar la configuración:

```bash
curl -I http://localhost:5000/api/get_json_config
```

---

## Recursos Adicionales

- [Documentación de Next.js](https://nextjs.org/docs) - Aprende sobre las características y la API de Next.js.
- [Tutorial interactivo de Next.js](https://nextjs.org/learn) - Un tutorial interactivo para aprender Next.js.
- [Repositorio de Next.js en GitHub](https://github.com/vercel/next.js) - Contribuye o reporta problemas.

---