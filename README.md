# Homelab: NAS con Synology DSM y Tailscale

> Servidor NAS casero montado sobre hardware reciclado, con acceso remoto seguro mediante Tailscale VPN y gestión centralizada de archivos y copias de seguridad.

---

## Descripción

Este proyecto documenta la configuración de un servidor NAS casero ejecutando **Synology DSM** sobre un PC reciclado mediante **XPEnology / ARC Loader**.

El objetivo es disponer de un almacenamiento centralizado y privado accesible desde cualquier lugar, gestionando archivos personales y copias de seguridad de fotografías sin depender de servicios en la nube de terceros.

---

## Hardware

- PC reciclado (modelo por determinar)
- 1 disco SSD de 128 GB (ampliable)

---

## Software y Sistema

| Componente | Detalle |
|---|---|
| Sistema operativo | Synology DSM (instalado mediante XPEnology / ARC Loader) |
| Acceso remoto | Tailscale, instalado desde el Centro de Paquetes de Synology |
| Acceso en red local | IP local del servidor con puerto 5000 / 5001 |

---

## Arquitectura de Red

```
[Internet]
    |
[Router doméstico]
    |
    +-- [NAS / PC reciclado con Synology DSM]
             +-- Tailscale (acceso remoto seguro)
             +-- Red local (192.168.x.x:5000)

Acceso remoto: Portatil / Movil --(Tailscale VPN)--> NAS
Acceso local:  Portatil / PC    --(Red local)------> NAS
```

---

## Servicios Configurados

### Synology Drive
Sincronización bidireccional de archivos entre el NAS y el portátil y el PC de sobremesa. Permite tener los archivos disponibles en todos los dispositivos de forma automática, funcionando como una nube privada.

### Synology Photos
Almacenamiento centralizado y copia de seguridad automática de las fotografías de 3 dispositivos móviles. Las fotos se suben directamente al NAS sin pasar por servicios externos.

---

## Acceso Remoto con Tailscale

Tailscale está instalado directamente en el NAS desde el Centro de Paquetes de Synology DSM. Permite acceder al servidor desde cualquier red externa de forma segura, sin necesidad de abrir puertos en el router ni exponer la IP pública.

Desde fuera de la red local, el acceso se realiza a través de la IP privada asignada por Tailscale al NAS.

---

## Estado Actual

- Sistema operativo Synology DSM operativo sobre hardware reciclado
- Tailscale configurado y funcional para acceso remoto
- Synology Drive sincronizando archivos en 2 equipos
- Synology Photos realizando copias de seguridad de 3 móviles
- Almacenamiento actual: 1 SSD de 128 GB (ampliable)
- Configuración de seguridad: acceso mediante usuario y contraseña

---

## Próximos Pasos

- Ampliar el almacenamiento con un segundo disco cuando se llene el SSD de 128 GB
- Implementar medidas de bastionado: desactivar usuario admin por defecto, activar 2FA y configurar reglas de firewall

---

## Autor

**Miguel Hidalgo** — Estudiante de SMR | Futuro ASIR  
GitHub: [github.com/MHR15](https://github.com/MHR15)

---

*Proyecto en desarrollo continuo.*
