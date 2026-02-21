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


## Componentes principales

| Componente      | Función principal                             | Tecnología       | IP principal       |
|-----------------|-----------------------------------------------|------------------|--------------------|
| Firewall        | Segmentación, NAT, reglas perimetrales        | OPNsense         | WAN: 10.0.2.15     |
| Proxy           | Control de acceso a Internet + filtrado       | Squid 6          | 192.168.200.10:3128|
| VPN             | Acceso remoto seguro a LAN y DMZ              | WireGuard        | 10.8.0.1 / 10.8.0.2|
| Cliente LAN     | Pruebas de navegación y accesos               | Fedora           | 192.168.100.10     |
| Servidor DMZ    | Aloja proxy y página de prueba                | Ubuntu Server    | 192.168.200.10     |

## Funcionalidades implementadas

### 1. Firewall y segmentación (OPNsense)

- Interfaces: WAN, LAN, DMZ
- Reglas WAN → abierto UDP 51820 (WireGuard)
- Reglas LAN → solo permite salida al proxy (3128/TCP)
- Bloqueo de acceso directo LAN → Internet
- Permiso ICMP y tráfico proxy desde DMZ

### 2. Proxy Squid con control avanzado

- Instalación y configuración básica
- ACLs para red local (`localnet`)
- Listas de webs permitidas / prohibidas
- Reglas por IP y franjas horarias
  - Director: acceso total
  - Administrativos: restricciones horarias + webs prohibidas (youtube, etc.)
  - Fuera de horario laboral → bloqueo total
- Logs activos + informes visuales con **SARG**

### 3. VPN WireGuard

- Servidor en OPNsense (puerto 51820)
- Interfaz WireGuard con reglas firewall específicas
- Cliente configurado en Fedora
- Acceso completo a LAN y DMZ desde fuera
- Pruebas: ping, SSH, HTTP, traceroute vía VPN
