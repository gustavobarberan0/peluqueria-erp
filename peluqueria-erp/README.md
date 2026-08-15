# Peluquería ERP - Sistema de Gestión para Peluquería Femenina

Sistema de escritorio para gestión de peluquería femenina usando Electron, PostgreSQL local y Node.js embebido, sin necesidad de Internet.

## 🚀 Características Principales

- **Dashboard** con KPIs en tiempo real
- **Gestión de Citas** con calendario interactivo
- **Clientes** con sistema de fidelidad
- **Estilistas** con seguimiento de rendimiento
- **Inventario** con alertas de stock bajo
- **Reportes** exportables a PDF/Excel
- **Backups** automáticos y manuales
- **Acceso en Red Local** desde cualquier dispositivo

## 📋 Requisitos Previos

### Para Desarrollo
- Node.js 18+
- PostgreSQL 15+
- npm o yarn

### Para Producción
- Solo se requiere el instalador generado

## 🛠️ Instalación para Desarrollo

### 1. Clonar el repositorio
```bash
git clone <repository-url>
cd peluqueria-erp
```

### 2. Instalar dependencias
```bash
npm install
```

### 3. Configurar PostgreSQL

#### Opción A: Instalación automática (recomendado)
```bash
npm run postgres:install
```

#### Opción B: Instalación manual
1. Instalar PostgreSQL 15+ desde https://www.postgresql.org/download/
2. Crear usuario y base de datos manualmente
3. Configurar el archivo `.env` con las credenciales

### 4. Configurar base de datos
```bash
npm run db:setup
npm run db:migrate
npm run db:seed
```

### 5. Ejecutar en modo desarrollo
```bash
npm run dev
```

## 📦 Generar Instaladores

### Windows
```bash
npm run dist:win
```

### macOS
```bash
npm run dist:mac
```

### Linux
```bash
npm run dist:linux
```

## 🗄️ Estructura de la Base de Datos

### Tablas Principales
- **Client**: Clientes con sistema de puntos
- **Appointment**: Citas programadas
- **Stylist**: Estilistas con especialidades
- **Product**: Productos de inventario
- **User**: Usuarios del sistema
- **CashRegister**: Caja diario

## 🔌 API Endpoints

### Autenticación
- `POST /api/auth/login` - Iniciar sesión
- `POST /api/auth/register` - Registrar usuario

### Clientes
- `GET /api/clients` - Listar clientes
- `POST /api/clients` - Crear cliente
- `PUT /api/clients/:id` - Actualizar cliente
- `DELETE /api/clients/:id` - Eliminar cliente

### Citas
- `GET /api/appointments` - Listar citas
- `POST /api/appointments` - Crear cita
- `PUT /api/appointments/:id` - Actualizar cita
- `PATCH /api/appointments/:id/status` - Cambiar estado
- `DELETE /api/appointments/:id` - Eliminar cita

### Estilistas
- `GET /api/stylists` - Listar estilistas
- `POST /api/stylists` - Crear estilista
- `PUT /api/stylists/:id` - Actualizar estilista

### Productos
- `GET /api/products` - Listar productos
- `GET /api/products/low-stock` - Productos con stock bajo
- `POST /api/products` - Crear producto
- `PUT /api/products/:id` - Actualizar producto
- `PATCH /api/products/:id/stock` - Ajustar stock

### Dashboard
- `GET /api/dashboard/kpis` - Obtener KPIs
- `GET /api/dashboard/charts` - Datos para gráficos
- `GET /api/dashboard/upcoming-appointments` - Próximas citas

### Reportes
- `GET /api/reports/sales` - Reporte de ventas
- `GET /api/reports/stylist-performance` - Rendimiento por estilista
- `GET /api/reports/top-clients` - Mejores clientes

## 🔐 Credenciales por Defecto

Después de ejecutar el seed:
- **Usuario**: admin
- **Contraseña**: admin123

## 📁 Estructura del Proyecto

```
peluqueria-erp/
├── src/
│   ├── main/              # Proceso principal de Electron
│   │   ├── main.js
│   │   └── preload.js
│   └── backend/           # Backend Express
│       ├── server.js
│       ├── routes/
│       └── services/
├── frontend/              # Interfaz de usuario
│   ├── index.html
│   ├── css/
│   └── js/
├── prisma/                # Schema y migraciones
│   ├── schema.prisma
│   └── seed.js
├── scripts/               # Scripts de instalación
└── config/                # Configuración de DB
```

## 🔧 Comandos Disponibles

| Comando | Descripción |
|---------|-------------|
| `npm start` | Iniciar aplicación en producción |
| `npm run dev` | Iniciar en modo desarrollo |
| `npm run dist` | Generar instaladores |
| `npm run postgres:install` | Instalar PostgreSQL |
| `npm run db:setup` | Configurar base de datos |
| `npm run db:migrate` | Ejecutar migraciones |
| `npm run db:seed` | Cargar datos de prueba |

## 🌐 Acceso en Red Local

El servidor se ejecuta en `0.0.0.0:3000`, permitiendo acceso desde otros dispositivos en la misma red:

```
http://<IP-del-servidor>:3000
```

## 💾 Backups

### Crear Backup Manual
1. Menú → Archivo → Crear Backup
2. O usar IPC: `window.electron.ipcRenderer.invoke('create-backup')`

### Restaurar Backup
1. Menú → Archivo → Restaurar Backup
2. Seleccionar backup de la lista

## 🎨 Personalización

Los colores y estilos pueden modificarse en `frontend/css/main.css`:

```css
:root {
  --primary-color: #9b59b6;
  --secondary-color: #3498db;
  /* ... más variables */
}
```

## 📝 Licencia

MIT License

## 👥 Soporte

Para reportar problemas o solicitar características, abra un issue en el repositorio.

---

**Versión**: 1.0.0  
**Última actualización**: 2024
