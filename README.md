# Proyecto: Red Segura con Perímetro Definido

**Configuración de red con seguridad perimétrica**  
[![OPNsense](https://img.shields.io/badge/OPNsense-24.x-orange?style=flat&logo=opnsense)](https://opnsense.org/)
[![Squid](https://img.shields.io/badge/Squid-6.x-blue?style=flat&logo=linux)](http://www.squid-cache.org/)
[![WireGuard](https://img.shields.io/badge/WireGuard-VPN%20Moderno-green?style=flat&logo=wireguard)](https://www.wireguard.com/)

## Objetivo del proyecto

Implementar una arquitectura de red segura con:

- Firewall perimétrico (OPNsense)
- Segmentación con DMZ
- Proxy transparente + filtrado avanzado (Squid + ACLs por IP y horario)
- Acceso remoto seguro vía VPN (WireGuard)
- Control total de salida a Internet desde la LAN

Todo realizado en un homelab con máquinas virtuales (VirtualBox).

## Topología de la red


