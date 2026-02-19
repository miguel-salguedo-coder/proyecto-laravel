# 🚀 Laravel
Una aplicación web moderna y completa construida con **Laravel 12**, **React 19**, **Inertia.js** y **Tailwind CSS**. Incluye autenticación robusta con **Fortify/Jetstream**, gestión de equipos, API tokens y mucho más.

## 📸 Características Principales

- ✅ **Autenticación Completa**: Login, registro, verificación de email
- 🔐 **Seguridad Avanzada**: Autenticación de dos factores, gestión de sesiones
- 👥 **Gestión de Equipos**: Crear equipos, invitar miembros, roles y permisos
- 🔑 **API Tokens**: Generar y gestionar tokens de acceso para API
- 📱 **Responsive Design**: Interfaz mobile-friendly con Tailwind CSS
- ⚡ **Hot Reload**: Vite con recarga automática en desarrollo
- 🧪 **Testing**: Tests automatizados con Pest + PHPUnit
- 🌙 **Modern Stack**: React 19, TypeScript, componentes reutilizables
- 🗄️ **Base de Datos**: SQLite (configurable a MySQL/PostgreSQL)
- 🚀 **Performance**: Lazy loading, optimización de assets

---

## 🛠️ Stack Tecnológico

### Backend
- **Laravel 12** - Framework PHP moderno
- **Laravel Fortify** - Autenticación sin interfaz
- **Laravel Jetstream** - Dashboard y gestión de perfil
- **Laravel Sanctum** - Autenticación de API
- **Pest** - Testing framework elegante

### Frontend
- **React 19** - Librería UI moderna
- **Inertia.js** - Puente Laravel-React sin API REST
- **Tailwind CSS v4** - Utilidades CSS
- **TypeScript** - Type safety
- **Vite** - Build tool ultra-rápido

---

## 📋 Requisitos Previos

Antes de empezar, asegúrate de tener instalado:

| Requisito | Versión | Descripción |
|-----------|---------|-------------|
| **PHP** | 8.2+ | Lenguaje backend |
| **Composer** | Latest | Gestor de dependencias PHP |
| **Node.js** | 18+ | Runtime JavaScript |
| **npm** | 9+ | Gestor de paquetes JavaScript |
| **Git** | Latest | Control de versiones |

### Verificar instalaciones:
```bash
php --version
composer --version
node --version
npm --version
git --version
```

---

## 🚀 Instalación Paso a Paso

### **Paso 1: Clonar el Repositorio**

```bash
git clone https://github.com/miguel-salguedo-coder/proyecto-laravel.git
cd proyecto-laravel
```

### **Paso 2: Instalación Automática (Recomendado)**

Si ya clonaste el repositorio en la carpeta del proyecto:

```bash
# Para instalar todas las dependencias y configurar el proyecto
composer install
npm install
```

Luego, configura el archivo `.env`:

```bash
# Copiar archivo de ejemplo
cp .env.example .env

# Generar application key
php artisan key:generate
```

### **Paso 3: Configurar Base de Datos**

La aplicación usa **SQLite** por defecto. Para crear la base de datos:

```bash
# Crear archivo SQLite
touch database/database.sqlite

# Ejecutar migraciones
php artisan migrate

# (Opcional) Ejecutar seeders para datos de prueba
php artisan db:seed
```

**Para usar MySQL/PostgreSQL**, edita el archivo `.env`:

```env
# Para MySQL
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel_proyecto
DB_USERNAME=root
DB_PASSWORD=

# Para PostgreSQL
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=laravel_proyecto
DB_USERNAME=postgres
DB_PASSWORD=
```

### **Paso 4: Compilar Assets Frontend**

```bash
# Compilación de desarrollo (con Vite)
npm run build

# O para desarrollo con hot-reload
npm run dev
```

---

## 🏃 Ejecutar la Aplicación

### **Opción 1: Ejecutar Todo Junto**

```bash
# En una terminal, ejecuta ambos servidores
npm run dev
```

Este comando ejecuta:
- **Laravel Server**: http://localhost:8000
- **Vite Dev Server**: Recarga automática de cambios

### **Opción 2: Ejecutar Servidores por Separado**

Terminal 1 - Backend:
```bash
php artisan serve
```

Terminal 2 - Frontend:
```bash
npm run dev
```

### **Opción 3: Con Más Servidores (Desarrollo Completo)**

```bash
# Ejecuta Laravel, Queue, Logs y Vite simultáneamente
npm run dev
```

**Accede a la aplicación**: http://localhost:8000

---

## 🔑 Credenciales de Prueba

Después de ejecutar `php artisan migrate`, puedes usar:

```
Email: test@example.com
Contraseña: password
```

O crear un nuevo usuario:

```bash
php artisan tinker

# En la consola Tinker:
User::create([
    'name' => 'Tu Nombre',
    'email' => 'tu@email.com',
    'password' => bcrypt('password')
])
```

---

## 📁 Estructura del Proyecto

```
proyecto-laravel/
├── app/                          # Código de la aplicación
│   ├── Actions/                  # Acciones reutilizables
│   │   ├── Fortify/             # Acciones de autenticación
│   │   └── Jetstream/           # Acciones de equipos
│   ├── Models/                   # Modelos Eloquent
│   │   ├── User.php             # Modelo de usuario
│   │   ├── Team.php             # Modelo de equipo
│   │   └── TeamInvitation.php   # Invitaciones de equipo
│   ├── Providers/                # Service Providers
│   │   ├── FortifyServiceProvider.php
│   │   └── JetstreamServiceProvider.php
│   ├── Policies/                 # Políticas de autorización
│   │   └── TeamPolicy.php
│   └── Events/                   # Eventos de aplicación
│
├── routes/                       # Definición de rutas
│   ├── web.php                  # Rutas web (Inertia)
│   ├── api.php                  # Rutas API (Sanctum)
│   └── console.php              # Comandos Artisan
│
├── resources/                    # Recursos frontend
│   ├── js/                      # Componentes React
│   ├── css/                     # Estilos Tailwind
│   ├── views/                   # Vistas Blade
│   │   ├── auth/               # Vistas de autenticación
│   │   ├── dashboard.blade.php # Panel principal
│   │   ├── profile/            # Gestión de perfil
│   │   └── teams/              # Gestión de equipos
│   └── markdown/               # Documentos en Markdown
│
├── database/                     # Base de datos
│   ├── migrations/              # Migraciones SQL
│   ├── factories/               # Factories para tests
│   ├── seeders/                 # Datos iniciales
│   └── database.sqlite          # Archivo SQLite
│
├── config/                       # Configuración
│   ├── fortify.php             # Config de autenticación
│   ├── jetstream.php           # Config de equipos
│   └── sanctum.php             # Config de API
│
├── tests/                        # Tests automatizados
│   ├── Feature/                 # Tests funcionales
│   ├── Unit/                    # Tests unitarios
│   └── Pest.php                # Configuración de Pest
│
├── storage/                      # Almacenamiento
│   ├── app/                     # Archivos de aplicación
│   ├── framework/               # Cache y vistas compiladas
│   └── logs/                    # Logs de la aplicación
│
├── public/                       # Archivos públicos
│   ├── index.php               # Punto de entrada
│   ├── build/                  # Assets compilados
│   └── storage/                # Enlace simbólico
│
├── bootstrap/                    # Bootstrap del framework
├── vendor/                       # Dependencias PHP
├── node_modules/               # Dependencias JavaScript
├── .env.example                # Variables de entorno
├── composer.json               # Dependencias PHP
├── package.json                # Dependencias JavaScript
├── postcss.config.js           # Configuración PostCSS
├── tailwind.config.js          # Configuración Tailwind
└── README.md                   # Este archivo
```

---

## 🔧 Comandos Útiles

### **Desarrollo**

```bash
# Iniciar servidor de desarrollo
npm run dev

# Compilar assets para producción
npm run build

# Compilar con SSR (Server-Side Rendering)
npm run build:ssr

# Hot reload solo del frontend
npm run dev

# Ejecutar artisan tinker (REPL)
php artisan tinker
```

### **Base de Datos**

```bash
# Crear tabla en base de datos
php artisan migrate

# Revertir última migración
php artisan migrate:rollback

# Revertir todas las migraciones
php artisan migrate:reset

# Revertir y ejecutar nuevamente
php artisan migrate:refresh

# Ejecutar seeders
php artisan db:seed

# Crear migración nueva
php artisan make:migration create_tabla_table
```

### **Testing**

```bash
# Ejecutar todos los tests
composer test

# Ejecutar solo Feature tests
php artisan test tests/Feature

# Ejecutar solo Unit tests
php artisan test tests/Unit

# Tests con salida detallada
php artisan test --verbose

# Tests con reporte de coverage
php artisan test --coverage
```

### **Linting y Formateo**

```bash
# Verificar errores de código (Pint)
composer lint

# Formatear código automáticamente
npm run format

# Verificar formateo sin cambios
npm run format:check

# ESLint
npm run lint

# Type checking (TypeScript)
npm run types
```

### **Artisan Útiles**

```bash
# Listar todas las rutas
php artisan route:list

# Limpiar caché
php artisan cache:clear
php artisan config:clear
php artisan view:clear

# Optimizar para producción
php artisan config:cache
php artisan route:cache

# Generar symlink para storage
php artisan storage:link
```

---

## 🔐 Autenticación y Seguridad

### **Características de Autenticación**

1. **Registro de Usuarios**: Validación de email y contraseña
2. **Verificación de Email**: Confirmación antes de acceder
3. **Recuperación de Contraseña**: Reset link por email
4. **Autenticación de Dos Factores**: TOTP/SMS
5. **Gestión de Sesiones**: Control de dispositivos activos
6. **API Tokens**: Para acceso programático

### **Rutas Protegidas**

Las siguientes rutas requieren autenticación:

```php
// Rutas disponibles después de login
/dashboard                    // Panel de control
/profile                      // Gestión de perfil
/teams                        // Gestión de equipos
/api/user                     // Info del usuario actual
/api/teams                    // Equipos del usuario
```

---

## 👥 Gestión de Equipos

### **Crear Equipo**

1. Accede a tu perfil
2. Ve a "Equipos"
3. Haz clic en "Crear Equipo"
4. Completa el formulario

### **Invitar Miembros**

```php
// En una ruta o comando:
$team->inviteTeamMember(
    auth()->user(),
    'email@example.com',
    'editor' // rol
);
```

### **Roles Disponibles**

- `admin` - Control total del equipo
- `editor` - Puede editar contenido
- `viewer` - Solo lectura

---

## 🔌 API REST con Sanctum

### **Autenticación API**

```bash
# 1. Generar token en /api/api-tokens
# 2. Usar token en headers:
curl -H "Authorization: Bearer {token}" \
     -H "Accept: application/json" \
     http://localhost:8000/api/user
```

### **Endpoints Disponibles**

```
GET    /api/user                    # Usuario actual
GET    /api/teams                   # Equipos del usuario
POST   /api/teams                   # Crear equipo
PUT    /api/teams/{team}            # Actualizar equipo
DELETE /api/teams/{team}            # Eliminar equipo
```

---

## 🧪 Testing

### **Ejecutar Tests**

```bash
# Todos los tests
composer test

# Específico de una clase
php artisan test tests/Feature/AuthenticationTest.php

# Con patrón
php artisan test --filter=login
```

### **Crear Nuevo Test**

```bash
php artisan make:test Feature/MyFeatureTest
php artisan make:test Unit/MyUnitTest
```

### **Estructura de un Test**

```php
use Tests\TestCase;

class ExampleTest extends TestCase
{
    public function test_homepage_loads()
    {
        $response = $this->get('/');
        $response->assertStatus(200);
    }
}
```

---

## 📦 Desplegar en Producción

### **Preparar para Producción**

```bash
# 1. Compilar assets
npm run build

# 2. Instalar solo dependencias de producción
composer install --no-dev --optimize-autoloader

# 3. Configurar variables de entorno
cp .env.example .env
php artisan key:generate

# 4. Optimizar la aplicación
php artisan config:cache
php artisan route:cache
php artisan view:cache

# 5. Ejecutar migraciones
php artisan migrate --force

# 6. Generar enlace de storage
php artisan storage:link
```

### **Servidores Recomendados**

- **Hosting**: Vercel, Heroku, DigitalOcean, AWS
- **Base de Datos**: PostgreSQL, MySQL 8+
- **Cache**: Redis
- **Queue**: Beanstalkd o Redis

---

## 🐛 Troubleshooting

### **Error: "APP_KEY not set"**
```bash
php artisan key:generate
```

### **Error: "Base de datos no encontrada"**
```bash
touch database/database.sqlite
php artisan migrate
```

### **Error: "npm: command not found"**
Instala Node.js desde https://nodejs.org

### **Error: "Composer not found"**
Instala Composer desde https://getcomposer.org

### **Puerto 8000 ya está en uso**
```bash
php artisan serve --port=8001
```

### **Permisos de storage**
```bash
chmod -R 775 storage bootstrap/cache
```

### **Cache corrupto**
```bash
php artisan cache:clear
php artisan config:clear
php artisan view:clear
```

---

## 📚 Documentación Oficial

- [Laravel Docs](https://laravel.com/docs)
- [Inertia.js Docs](https://inertiajs.com)
- [React Docs](https://react.dev)
- [Tailwind CSS Docs](https://tailwindcss.com)
- [Pest Testing](https://pestphp.com)
- [Jetstream Docs](https://jetstream.laravel.com)
- [Fortify Docs](https://fortify.laravel.com)

---

## 🤝 Contribuir

Las contribuciones son bienvenidas. Para contribuir:

1. **Fork** el repositorio
2. Crea una **rama** para tu feature (`git checkout -b feature/amazing-feature`)
3. **Commit** tus cambios (`git commit -m 'Add amazing feature'`)
4. **Push** a la rama (`git push origin feature/amazing-feature`)
5. Abre un **Pull Request**

### **Estándares de Código**

```bash
# Antes de hacer commit, ejecuta:
composer lint
npm run format
npm run types
composer test
```

---

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**. Ver archivo [LICENSE](LICENSE) para más detalles.

---

## 👨‍💻 Autor

**Miguel Salguedo**
- GitHub: [@miguel-salguedo-coder](https://github.com/miguel-salguedo-coder)
- Email: tu-email@example.com

---

## 💬 Soporte

¿Tienes preguntas o encuentras bugs?

- **Abre un Issue**: [GitHub Issues](https://github.com/miguel-salguedo-coder/proyecto-laravel/issues)
- **Discusiones**: [GitHub Discussions](https://github.com/miguel-salguedo-coder/proyecto-laravel/discussions)

---

## 🎉 Gracias por usar este proyecto

Si te fue útil, ¡por favor dale una ⭐ en GitHub!

---

**Última actualización**: 19 de febrero de 2026
**Versión**: 1.0.0
EOF
cat /home/Cohorte3/Descargas/Laravel-proyecto/README.md
