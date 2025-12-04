# Melodía - Music Streaming Platform

<div align="center">

🎵 **Plataforma completa de streaming musical con administración avanzada** 🎵

[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)](https://golang.org/)
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)

</div>

---

## 📖 Índice

- [Descripción General](#-descripción-general)
- [Componentes de la Plataforma](#-componentes-de-la-plataforma)
- [Arquitectura del Sistema](#-arquitectura-del-sistema)
- [Microservicios](#-microservicios)
- [Tecnologías](#-tecnologías)
- [Infraestructura](#-infraestructura)
- [Documentación Detallada](#-documentación-detallada)
- [Guía Rápida](#-guía-rápida)

---

## 🎯 Descripción General

**Melodía** es una plataforma completa de streaming musical, similar a Spotify, diseñada con una arquitectura de microservicios moderna y escalable. La plataforma consta de tres componentes principales:

1. **📱 Mobile App** - Aplicación móvil para usuarios finales
2. **💼 Backoffice Admin** - Panel de administración web
3. **🔧 Backend Microservices** - APIs y servicios backend

La plataforma permite a los usuarios descubrir, reproducir y gestionar música, mientras proporciona a los artistas herramientas para gestionar su presencia y métricas. Los administradores tienen un panel completo para gestionar contenido, usuarios, políticas regionales y analytics.

### Características Principales

- 🎵 **Catálogo Musical Completo** - Álbumes, singles, EPs, playlists
- 👤 **Gestión de Usuarios** - Registro, autenticación, perfiles
- 🎤 **Perfiles de Artistas** - Biografías, discografía, redes sociales
- 📊 **Analytics en Tiempo Real** - Métricas de reproducción y engagement
- 🔔 **Sistema de Notificaciones** - Alertas y actualizaciones
- 🔍 **Búsqueda Avanzada** - Search unificado en todo el catálogo
- ❤️ **Interacciones Sociales** - Likes, saves, follows, playlists
- 🎧 **Streaming de Audio** - Reproducción en alta calidad
- 💼 **Panel de Administración** - Backoffice completo para gestión
- 🌍 **Políticas Regionales** - Control de disponibilidad por región

---

## 🏗️ Componentes de la Plataforma

### 1. 📱 Mobile App (React Native / Flutter)

**Descripción**: Aplicación móvil para usuarios finales (iOS y Android)

**Funcionalidades**:
- 🎵 Reproducción de música en streaming
- 🔍 Búsqueda de canciones, álbumes, artistas
- 📝 Creación y gestión de playlists
- ❤️ Sistema de likes y favoritos
- 👥 Follow de artistas
- 📊 Historial de reproducción
- 🎨 Interfaz intuitiva y responsive

**Tecnologías**:
- React Native / Flutter
- Redux / Context API para state management
- Axios para API calls
- AsyncStorage para persistencia local

**Comunicación**:
- Consume APIs REST a través del API Gateway
- Autenticación con JWT tokens
- WebSocket para notificaciones en tiempo real (futuro)

---

### 2. 💼 Backoffice Admin (React + TypeScript)

**Descripción**: Panel de administración web para gestión de la plataforma

**Funcionalidades Administrativas**:

#### 👥 Gestión de Usuarios
- Alta, baja, edición de usuarios
- Bloqueo/desbloqueo de cuentas
- Cambio de roles (Listener, Artist, Admin)
- Visualización detallada de perfiles
- Historial de actividad

#### 🎵 Gestión de Catálogo
- **CRUD completo** de álbumes, singles, EPs, canciones
- Gestión de playlists (públicas y privadas)
- Administración de géneros musicales
- Upload de archivos multimedia (audio, imágenes)
- Filtros avanzados y búsqueda
- Previsualización de contenido

#### 🌍 Políticas Regionales
- Creación de políticas de disponibilidad por región
- Configuración de periodos de restricción
- Interfaz visual para gestión de políticas
- Auditoría de cambios en políticas

#### 📊 Analytics y Métricas
- **Dashboard en tiempo real** con métricas clave:
    - Registros nuevos
    - Inicios de sesión
    - Reproducciones totales
    - Canciones más escuchadas
- **Filtros avanzados**:
    - Por periodo de tiempo
    - Por entorno (dev/prod)
    - Por región geográfica
    - Por tipo de usuario
    - Por método de login
- **Breakdowns por etiquetas**:
    - Distribución por región
    - Distribución por tipo de usuario
    - Análisis de métodos de autenticación
- **Exportación a CSV** para análisis externo
- Integración con DataDog para métricas avanzadas

#### 📝 Auditoría
- Registro de todas las acciones administrativas
- Historial detallado de cambios
- Filtros por usuario, fecha, tipo de acción
- Trazabilidad completa

**Tecnologías**:
- **Frontend**: React 18+ con TypeScript
- **Build Tool**: Vite
- **Styling**: CSS Modules
- **State Management**: React Context / Hooks
- **HTTP Client**: Fetch API / Axios
- **Storage**: Supabase para archivos multimedia

**Endpoints Consumidos**:
```
/api/v1/users/admin/users          # Gestión de usuarios
/api/v1/catalog                     # Gestión de catálogo
/api/v1/catalog/policy              # Políticas regionales
/api/v1/analytics/audit             # Auditoría
/api/v1/analytics/metrics           # Métricas y breakdowns
/api/v1/artists                     # Gestión de artistas
```

**Configuración**:
```env
VITE_API_URL=http://xyziverse.xyz:32260
VITE_API_URL_ARTIST=http://artist-api:8081
EXPO_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
EXPO_PUBLIC_SUPABASE_ANON_KEY=your_anon_key
```

**Características de Seguridad**:
- Autenticación JWT obligatoria
- Roles y permisos (solo Admin)
- Manejo de expiración de sesión
- Logout centralizado
- Validación de formularios
- Sanitización de inputs

---

### 3. 🔧 Backend Microservices

**Descripción**: Conjunto de microservicios independientes para lógica de negocio

---

## 🏗️ Arquitectura del Sistema

Melodía utiliza una **arquitectura de microservicios** desplegada en **Kubernetes** en una máquina virtual de Hostinger.

### Diagrama de Alto Nivel

```mermaid
graph TB
    subgraph "Client Layer"
        Mobile[📱 Mobile App<br/>React Native/Flutter]
    end

    subgraph "Kubernetes Cluster - Hostinger VM"
        Gateway[🌐 API Gateway<br/>Kong/Nginx]
        
        subgraph "Microservices Pods"
            Catalog[📚 Catalog API<br/>Port 8082]
            User[👤 User API<br/>Port 8080]
            Artist[🎤 Artist API<br/>Port 8081]
            Analytics[📊 Analytics API<br/>Port 8083]
            Notifications[🔔 Notifications API<br/>Port 8084]
        end
        
        subgraph "Data Layer"
            MySQL[(🗄️ MySQL<br/>Relational DB)]
            MongoDB[(🍃 MongoDB<br/>Analytics DB)]
        end
    end

    Mobile -->|HTTPS| Gateway
    
    Gateway --> Catalog
    Gateway --> User
    Gateway --> Artist
    Gateway --> Analytics
    Gateway --> Notifications
    
    Catalog --> MySQL
    User --> MySQL
    Artist --> MySQL
    Notifications --> MySQL
    Analytics --> MongoDB

    Catalog -.->|Auth Validation| User
    Artist -.->|Auth Validation| User
    Analytics -.->|Catalog Info| Catalog

    classDef client fill:#E1F5FE,stroke:#2196F3,stroke-width:3px
    classDef gateway fill:#FFF3E0,stroke:#FF9800,stroke-width:3px
    classDef service fill:#E8F5E9,stroke:#4CAF50,stroke-width:2px
    classDef database fill:#F3E5F5,stroke:#9C27B0,stroke-width:2px

    class Mobile client
    class Gateway gateway
    class Catalog,User,Artist,Analytics,Notifications service
    class MySQL,MongoDB database
```

### Flujo de Comunicación

```mermaid
sequenceDiagram
    participant M as 📱 Mobile App
    participant G as 🌐 Gateway
    participant U as 👤 User API
    participant C as 📚 Catalog API
    participant A as 🎤 Artist API
    participant AN as 📊 Analytics API
    
    Note over M,AN: Flujo de Autenticación
    M->>G: 1. POST /auth/login
    G->>U: Forward Request
    U-->>G: JWT Token + User Data
    G-->>M: 200 OK + Token
    
    Note over M,AN: Flujo de Búsqueda de Música
    M->>G: 2. GET /catalog/search?q=rock
    G->>C: Forward + Bearer Token
    C->>U: Validate Token
    U-->>C: Token Valid
    C-->>G: Search Results
    G-->>M: 200 OK + Results
    
    Note over M,AN: Flujo de Reproducción
    M->>G: 3. GET /catalog/songs/{id}/stream
    G->>C: Stream Request
    C-->>G: Audio Stream
    G-->>M: Audio Data
    
    M->>G: 4. POST /analytics/events/play
    G->>AN: Record Play Event
    AN->>C: Increment Play Count
    C-->>AN: Updated
    AN-->>G: Event Recorded
    G-->>M: 201 Created
```

---

## 🔧 Microservicios

### 1. 📚 Catalog API

**Responsabilidad**: Gestión completa del catálogo musical

**Funcionalidades**:
- Gestión de álbumes, singles, EPs
- Playlists (públicas y privadas)
- Géneros musicales
- Sistema de likes/saves
- Búsqueda unificada
- Streaming de audio

**Base de Datos**: MySQL  

---

### 2. 👤 User API

**Responsabilidad**: Gestión de usuarios y autenticación

**Funcionalidades**:
- Registro y login (email/OAuth)
- Gestión de perfiles
- Sistema de follow/unfollow
- Validación de tokens (JWT)
- Gestión de sesiones

**Base de Datos**: MySQL  
---

### 3. 🎤 Artist API

**Responsabilidad**: Gestión de artistas y sus perfiles

**Funcionalidades**:
- Perfiles de artistas (biografía, fotos)
- Redes sociales
- Carrusel de imágenes
- Artist Picks (contenido destacado)
- Artistas relacionados
- Métricas (monthly listeners)

**Base de Datos**: MySQL  

---

### 4. 📊 Analytics API

**Responsabilidad**: Métricas y análisis de uso

**Funcionalidades**:
- Registro de eventos de reproducción
- Historial de reproducción
- Top songs por artista
- Eventos de auditoría
- Estadísticas de engagement

**Base de Datos**: MongoDB  

---

### 5. 🔔 Notifications API

**Responsabilidad**: Sistema de notificaciones

**Funcionalidades**:
- Notificaciones push
- Notificaciones in-app
- Alertas de nuevos lanzamientos
- Notificaciones de interacciones sociales

**Base de Datos**: MySQL  

---

## 💻 Tecnologías

### Backend

| Tecnología | Uso | Versión |
|------------|-----|---------|
| **Go (Golang)** | Lenguaje principal de APIs | 1.24+ |
| **Gin** | Framework HTTP | Latest |
| **GORM** | ORM para MySQL | v2 |
| **MongoDB Driver** | Cliente MongoDB | Latest |

### Bases de Datos

| Base de Datos | Uso | Servicios |
|---------------|-----|-----------|
| **MySQL 8.0** | Datos relacionales | Catalog, User, Artist, Notifications |
| **MongoDB** | Datos de analytics | Analytics |

### Infraestructura

| Componente | Tecnología | Descripción |
|------------|------------|-------------|
| **Orquestación** | Kubernetes | Gestión de contenedores |
| **Hosting** | Hostinger VM | Máquina virtual dedicada |
| **Gateway** | Kong/Nginx | Routing y load balancing |
| **Contenedores** | Docker | Empaquetado de servicios |
| **Storage** | Supabase | Almacenamiento de archivos |

### Observabilidad

| Herramienta | Uso |
|-------------|-----|
| **DataDog APM** | Monitoreo y trazabilidad |
| **Uber Zap** | Logging estructurado |
| **Prometheus** | Métricas (opcional) |

---

## ☁️ Infraestructura

### Kubernetes Deployment


<img src="./assets/images/kube-deploy.png" alt="Deply kubernetes" width="100%">


## 📚 Documentación Detallada

### Diagramas de Arquitectura

## 📚 Documentación Detallada y Diagramas


<img src="./assets/images/architecture.jpeg" alt="Arquitectura General" width="100%">

<img src="./assets/images/deploy_kb.jpeg" alt="Infraestructura Kubernetes" width="100%">

<img src="./assets/images/backoffice_flow.jpeg" alt="Flujo Backoffice" width="100%">

<img src="./assets/images/components.jpeg" alt="Componentes" width="100%">



### Documentación por API

- **[📚 Catalog API](./docs/CATALOG_API.md)** - Gestión del catálogo musical
- **[👤 User API](./docs/USER_API.md)** - Usuarios y autenticación
- **[🎤 Artist API](./docs/ARTIST_API.md)** - Perfiles de artistas
- **[📊 Analytics API](./docs/ANALYTICS_API.md)** - Métricas y analytics
- **[🔔 Notifications API](./docs/NOTIFICATIONS_API.md)** - Sistema de notificaciones

### Guías Técnicas

- **[🚀 Guía de Deployment](./docs/DEPLOYMENT_GUIDE.md)** - Despliegue en Kubernetes
- **[⚙️ Configuración](./docs/CONFIGURATION.md)** - Variables de entorno
- **[🧪 Testing](./docs/TESTING_GUIDE.md)** - Estrategia de pruebas
- **[🔍 Troubleshooting](./docs/TROUBLESHOOTING.md)** - Resolución de problemas
- **[📈 Monitoring](./docs/MONITORING.md)** - Observabilidad y alertas

---

## 🚀 Guía Rápida

### Requisitos Previos

- Acceso a la VM de Hostinger
- kubectl configurado
- Docker (para desarrollo local)
- Go 1.24+ (para desarrollo)

### Desplegar en Kubernetes

```bash
# 1. Conectar al cluster
kubectl config use-context melodia-production

# 2. Aplicar configuraciones
kubectl apply -f k8s/namespace.yaml
kubectl apply -f k8s/configmaps/
kubectl apply -f k8s/secrets/
kubectl apply -f k8s/databases/
kubectl apply -f k8s/services/

# 3. Verificar deployments
kubectl get pods -n melodia-production

# 4. Ver logs
kubectl logs -f deployment/catalog-api -n melodia-production
```

### Desarrollo Local

```bash
# 1. Clonar repositorio
git clone https://github.com/melodia/melodia-platform.git
cd melodia-platform

# 2. Iniciar bases de datos
docker-compose up -d mysql mongodb

# 3. Iniciar un servicio (ejemplo: Catalog API)
cd catalog-api
cp .env.example .env
go run cmd/main.go

# 4. El servicio estará disponible en http://localhost:8082
```

### Endpoints Principales

| Servicio | Base URL | Health Check |
|----------|----------|--------------|
| **Gateway** | `https://api.melodia.com` | - |
| **Catalog** | `/api/v1/catalog` | `GET /health` |
| **User** | `/api/v1/users` | `GET /health` |
| **Artist** | `/api/v1/artists` | `GET /health` |
| **Analytics** | `/api/v1/analytics` | `GET /health` |
| **Notifications** | `/api/v1/notifications` | `GET /health` |

---

## 🔐 Autenticación

Todos los endpoints (excepto `/health` y endpoints públicos) requieren autenticación JWT:

```bash
# 1. Obtener token
curl -X POST https://api.melodia.com/api/v1/users/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "password123"
  }'

# 2. Usar token en requests
curl https://api.melodia.com/api/v1/catalog/albums \
  -H "Authorization: Bearer <your-jwt-token>"
```

---

## 📊 Monitoring y Observabilidad

### DataDog Dashboard

Accede a [DataDog](https://app.datadoghq.com) para ver:
- Request rates y latencias
- Error rates por servicio
- Distributed tracing
- Resource utilization

### Logs

```bash
# Ver logs de un servicio específico
kubectl logs -f deployment/catalog-api -n melodia-production

# Ver logs de todos los pods de un servicio
kubectl logs -f -l app=catalog-api -n melodia-production

# Ver logs con timestamp
kubectl logs --since=1h deployment/catalog-api -n melodia-production
```

### Métricas

```bash
# Ver métricas de pods
kubectl top pods -n melodia-production

# Ver métricas de nodos
kubectl top nodes
```

---

## 🤝 Contribuir

Para contribuir al proyecto:

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

---

## 📄 Licencia

Este proyecto es propiedad privada de Melodía. Todos los derechos reservados.

---

## 📞 Contacto

- **Email**: dev@melodia.com
- **Slack**: #melodia-dev
- **Documentación**: https://github.com/Melodia13/melodia.github.io

---

<div align="center">

**Hecho con ❤️ por el equipo de Melodía**

</div>

