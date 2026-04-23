# Homelab: NAS Seguro con Synology y Tailscale

> Infraestructura de red doméstica con acceso remoto seguro sin abrir puertos en el router, implementada sobre hardware reciclado.

---

## Descripción

Este proyecto documenta la configuración de un servidor NAS casero montado sobre un PC antiguo reutilizado, ejecutando **Synology DSM** y conectado de forma segura a internet mediante **Tailscale** (basado en el protocolo WireGuard VPN).

El objetivo principal es poder acceder a los archivos, servicios y panel de administración desde cualquier lugar de forma **privada y segura**, sin necesidad de abrir puertos en el router ni exponer la IP pública.

---

## Objetivos del Proyecto

- Reutilizar hardware antiguo como servidor NAS doméstico
- Configurar acceso remoto seguro mediante Tailscale VPN (sin port forwarding)
- Aplicar bastionado de seguridad (hardening) en Synology DSM
- Gestionar almacenamiento, usuarios y permisos en red local
- Afianzar conocimientos prácticos de administración de sistemas y redes

---

## Tecnologías y Herramientas

| Herramienta | Uso |
|---|---|
| Synology DSM 7.x | Sistema operativo del NAS |
| Tailscale (WireGuard) | VPN para acceso remoto seguro |
| Linux / XPEnology | Base del servidor en el PC reciclado |
| Firewall DSM | Reglas de acceso por IP y subred |
| Autenticación de Doble Factor (2FA) | Seguridad de acceso al panel |
| Synology Active Backup | Copias de seguridad automáticas |

---

## Arquitectura de Red

```
[Internet]
    |
[Router doméstico]
    |
    +-- [NAS Synology / PC Reciclado]  <- Servidor principal
    |        +-- Tailscale (IP: 100.x.x.x)
    |
    +-- [Portatil]  <- Cliente Tailscale
    +-- [Movil]     <- Cliente Tailscale

Acceso remoto: Portatil/Movil --(Tailscale VPN)--> NAS
```

---

## Seguridad Implementada (Hardening)

- Cuenta `admin` por defecto deshabilitada
- Puerto de administración cambiado (no se usa 5000/5001)
- Autenticación de doble factor (2FA) activada para todos los usuarios
- Reglas de Firewall: acceso al panel restringido a la subred de Tailscale (`100.64.0.0/10`) y red local
- Auto Block activado: bloqueo automático tras intentos de login fallidos
- Actualizaciones automáticas de seguridad de DSM activadas

---

## Servicios Configurados

- **File Station** — Gestión de archivos desde cualquier dispositivo
- **Active Backup for Business** — Copias de seguridad automáticas del portátil
- **Jellyfin** — Servidor multimedia privado accesible vía Tailscale
- **Hyper Backup** — Backup cifrado a la nube (política de copias 3-2-1)

---

## Proceso de Configuración

### 1. Preparación del Hardware
- PC antiguo con al menos 4 GB de RAM y disco duro de 1 TB
- Instalación de XPEnology/ARC Loader para ejecutar Synology DSM en hardware no oficial

### 2. Instalación de Tailscale en Synology
- Instalación desde el Centro de Paquetes de DSM
- Autenticación con cuenta de Tailscale
- Configuración como nodo de la red privada virtual

### 3. Bastionado del Sistema
- Creación de usuario administrador personalizado
- Desactivación del usuario `admin` por defecto
- Configuración del Firewall con reglas restrictivas por IP
- Activación de 2FA para todos los usuarios con acceso

### 4. Configuración de Servicios
- Creación de carpetas compartidas con permisos diferenciados por usuario
- Configuración de tareas programadas para backups nocturnos automatizados

---

## Resultados

- Acceso remoto al NAS desde cualquier red sin exposición de puertos al exterior
- Latencia de acceso por Tailscale inferior a 2 segundos
- Sistema de backup automático 3-2-1 operativo
- Sin accesos no autorizados exitosos desde la puesta en marcha

---

## Conocimientos Adquiridos

- Administración de sistemas Linux y Synology DSM
- Configuración de redes locales y VPN basada en WireGuard
- Políticas de seguridad y bastionado de servidores
- Gestión de almacenamiento, usuarios y permisos en entorno NAS
- Diseño básico de arquitecturas de red doméstica

---

## Autor

**Miguel Hidalgo** — Estudiante de SMR | Futuro ASIR  
GitHub: [github.com/MHR15](https://github.com/MHR15)

---

*Proyecto en desarrollo continuo. Próximamente: monitorización con análisis automatizado de logs de acceso.*
