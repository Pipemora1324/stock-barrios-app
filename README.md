# StockBarrio

Aplicación completa de inventario para mercados y tiendas de barrio. El frontend está en Angular 20 y el backend usa Node.js, Express, TypeScript, Zod y PostgreSQL.

## Funcionalidades

- Catálogo de productos con búsqueda, filtrado por categoría y stock.
- Operaciones de administración para crear, modificar y eliminar productos.
- Cálculo de stock total, valor de inventario, descuentos y productos agotados.
- Autenticación JWT con acceso administrativo.
- Recomendaciones de compra locales y opcionales con OpenAI-compatible.
- API REST con validación de entrada, CORS, Helmet y limitación de peticiones.

## Requisitos

- Node.js 20 o superior.
- npm.
- Docker Desktop o PostgreSQL local.

## Configuración

Copia `.env.example` a `.env` y ajusta los valores si es necesario:

```bash
cp backend/.env.example backend/.env
```

Para ejecutar con PostgreSQL local, el valor por defecto es:

```env
DATABASE_URL=postgresql://stock:stock@localhost:5432/stock_barrios
JWT_SECRET=cambia-este-secreto-en-produccion
```

El proveedor de IA por defecto es `local`. Para usar un proveedor OpenAI-compatible, configura `AI_PROVIDER`, `OPENAI_API_KEY`, `OPENAI_BASE_URL`, `OPENAI_MODEL` y `AI_TIMEOUT_MS`.

## Arrancar con Docker

```bash
docker compose up --build
```

- Frontend: http://localhost:4200
- API: http://localhost:3000
- PostgreSQL: localhost:5432

El backend ejecuta `npm run migrate` al iniciar para crear la tabla de productos.

## Arrancar en desarrollo

```bash
cd backend
npm install
npm run dev
```

En otra terminal:

```bash
cd frontend
npm install
npm start
```

## Validación

```bash
cd backend
npm test
npm run build
npm run lint

cd ../frontend
npm test
npm run build
npx tsc -p tsconfig.app.json --noEmit
```

## Estructura

- `backend/src`: API, repositorio, autenticación, servicios y configuración.
- `backend/test`: pruebas de comportamiento del backend.
- `frontend/src/app`: componentes, rutas, servicio HTTP y pruebas.
- `docker-compose.yml`: PostgreSQL y backend.
