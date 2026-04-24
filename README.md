# Homelab: NAS con Synology DSM y Tailscale

> Servidor NAS casero montado sobre hardware reciclado, con acceso remoto seguro mediante Tailscale VPN y gestión centralizada de archivos y copias de seguridad.

---

## Descripción

Este proyecto documenta la configuración de un servidor NAS casero ejecutando **Synology DSM** sobre un PC reciclado mediante **XPEnology / ARC Loader**.

El objetivo es disponer de un almacenamiento centralizado y privado accesible desde cualquier lugar, gestionando archivos personales y copias de seguridad de fotografías sin depender de servicios en la nube de terceros.

---

## Hardware

- Intel(R) Celeron(R) N3050 @ conservative (2 núcleos)
- 4096MB de memoria RAM
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
- Bastionado implementado: usuario admin desactivado, 2FA activado y firewall configurado

---
## Consideraciones

Este proyecto utiliza Synology DSM mediante ARC Loader sobre hardware no oficial, lo que significa que no está soportado por Synology y no se recomienda para entornos de producción ni uso comercial. Su objetivo es exclusivamente educativo y de laboratorio doméstico.

---

## Evidencias

| Inicio de sesión Synology DSM | Escritorio y Servicios |
| :---: | :---: |
| <img src="https://github.com/user-attachments/assets/63a426c3-78bd-42f9-8d5e-e1d2bb5fd89c" width="100%" /> | <img src="https://github.com/user-attachments/assets/7f1495c1-ae27-4d98-bcf7-593696e01476" width="100%" /> |

---
## Próximos Pasos

- Ampliar el almacenamiento con un segundo disco cuando se llene el SSD de 128 GB

---

## Autor

**Miguel Hidalgo**  
GitHub: [github.com/MHR15](https://github.com/MHR15)

---
