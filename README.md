# 🏠 Homelab: NAS Seguro con Synology y Tailscale

> Infraestructura de red doméstica con acceso remoto seguro sin abrir puertos en el router, implementada sobre hardware reciclado.

---

## 📋 Descripción

Este proyecto documenta la configuración de un servidor NAS casero montado sobre un PC antiguo reutilizado, ejecutando **Synology DSM** y conectado de forma segura a internet mediante **Tailscale** (basado en el protocolo WireGuard VPN).

El objetivo principal es poder acceder a los archivos, servicios y panel de administración desde cualquier lugar del mundo de forma **privada y segura**, sin necesidad de abrir puertos en el router ni exponer la IP pública.

---

## 🎯 Objetivos del Proyecto

- ♻️ Reutilizar hardware antiguo como servidor NAS doméstico
- 🔒 Configurar acceso remoto seguro mediante Tailscale VPN (sin port forwarding)
- 🛡️ Aplicar bastionado de seguridad (hardening) en Synology DSM
- 📁 Gestionar almacenamiento, usuarios y permisos en red local
- 🌐 Aprender administración real de sistemas y redes (SMR/ASIR)

---

## 🛠️ Tecnologías y Herramientas

| Herramienta | Uso |
|---|---|
| **Synology DSM 7.x** | Sistema operativo del NAS |
| **Tailscale (WireGuard)** | VPN para acceso remoto seguro |
| **Linux / XPEnology** | Base del servidor en el PC reciclado |
| **Firewall DSM** | Reglas de acceso por IP y subred |
| **2FA (Autenticación Doble Factor)** | Seguridad de acceso al panel |
| **Synology Active Backup** | Copias de seguridad automáticas |

---

## 🖧 Arquitectura de Red

```
[Internet]
    |
[Router doméstico]
    |
    ├── [NAS Synology / PC Reciclado]  ← Servidor principal
    |        └── Tailscale (IP: 100.x.x.x)
    |
    ├── [Portátil]  ← Cliente Tailscale
    └── [Móvil]     ← Cliente Tailscale

Acceso remoto: Portátil/Móvil ──(Tailscale VPN)──► NAS
```

---

## 🔐 Seguridad Implementada (Hardening)

- ✅ Cuenta `admin` por defecto **deshabilitada**
- ✅ Puerto de administración cambiado (no se usa 5000/5001)
- ✅ Autenticación de **doble factor (2FA)** activada
- ✅ Reglas de Firewall: acceso al panel solo desde la subred de Tailscale (`100.64.0.0/10`) y red local
- ✅ **Auto Block** activado: bloqueo automático tras intentos de login fallidos
- ✅ Actualizaciones automáticas de seguridad de DSM activadas

---

## 📦 Servicios Configurados

- 📁 **File Station** — Gestión de archivos desde cualquier dispositivo
- 💾 **Active Backup for Business** — Copias de seguridad automáticas del portátil
- 🎬 **Plex / Jellyfin** — Servidor multimedia privado accesible vía Tailscale
- 🔄 **Hyper Backup** — Backup cifrado a la nube (copia de seguridad 3-2-1)

---

## 📝 Proceso de Configuración

### 1. Preparación del Hardware
- PC antiguo con al menos 4GB RAM y disco duro de 1TB+
- Instalación de XPEnology/ARC Loader para correr Synology DSM en hardware no oficial

### 2. Instalación de Tailscale en Synology
- Instalación desde el Centro de Paquetes de DSM
- Autenticación con cuenta de Tailscale
- Configuración como nodo de la red privada virtual

### 3. Bastionado del Sistema
- Creación de usuario administrador personalizado
- Desactivación del usuario `admin` por defecto
- Configuración del Firewall con reglas restrictivas por IP
- Activación de 2FA para todos los usuarios

### 4. Configuración de Servicios
- Montaje de carpetas compartidas con permisos por usuario
- Configuración de tareas programadas para backups nocturnos

---

## ✅ Resultados

- 🌍 Acceso remoto seguro al NAS desde cualquier red sin abrir puertos
- ⚡ Latencia de acceso por Tailscale: < 2 segundos
- 🔒 Cero intentos de acceso no autorizados exitosos desde la puesta en marcha
- 💾 Sistema de backup automático 3-2-1 operativo

---

## 📚 Lo que he Aprendido

- Administración de sistemas Linux y Synology DSM
- Configuración de redes locales y VPNs (WireGuard/Tailscale)
- Políticas de seguridad y bastionado de servidores
- Gestión de almacenamiento, usuarios y permisos
- Diseño de arquitecturas de red doméstica

---

## 👤 Autor

**Miguel Hidalgo** — Estudiante de SMR | Futuro ASIR  
🔗 [GitHub](https://github.com/MHR15)

---

> 📌 *Proyecto en desarrollo continuo. Próximamente: monitorización con IA y detección de anomalías en los logs de acceso.*
