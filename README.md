# 🔥 Laboratorio de Seguridad de Red con FortiGate

## 📌 Descripción

Este proyecto demuestra la implementación y configuración de un
**firewall Fortinet FortiGate** para proteger una red segmentada.

El laboratorio simula una red empresarial pequeña con dos segmentos
principales:

![alt text](image-8.png)

-   **LAN de usuarios**
-   **LAN de servidores**

Se aplican diferentes controles de seguridad como:

-   Segmentación de red
-   DHCP
-   NAT para acceso a Internet
-   Políticas de firewall
-   Control de aplicaciones
-   Filtrado web
-   IPS
-   Web Application Firewall (WAF)

El objetivo es aplicar el principio de **mínimo privilegio** y demostrar
múltiples capas de seguridad.

------------------------------------------------------------------------

# 🖼️ Topología de Red

![alt text](image-2.png)

La red está compuesta por:

-   Firewall Fortinet
-   Red de usuarios
-   Red de servidores
-   Acceso a Internet

## Diseño de Red

  Segmento         Red             Descripción
  ---------------- --------------- ------------------------------
  LAN Usuarios     23.6.1.0/25     Red de estaciones de trabajo
  LAN Servidores   23.6.1.128/28   Red de servidores
  WAN              DHCP            Conexión a Internet

------------------------------------------------------------------------

# 🧱 Componentes de la Infraestructura

-   **Firewall Fortinet FortiGate**
-   **Equipo de usuario**
-   **Servidor Linux (Servidor Web)**
-   **Red WAN / Internet**

------------------------------------------------------------------------

# ⚙️ Configuración de Interfaces

![alt text](image-7.png)

  Interfaz   Red             Función
  ---------- --------------- ---------------------
  port1      DHCP            Conexión a Internet
  port2      23.6.1.128/28   LAN de servidores
  port3      23.6.1.0/25     LAN de usuarios

------------------------------------------------------------------------

# 📡 Configuración de DHCP

![alt text](image-6.png)

Se configuró **DHCP en la red de usuarios** para asignar direcciones IP
automáticamente.

Ejemplo de configuración:

    Red: 23.6.1.0/25
    Gateway: 23.6.1.1
    DNS: 8.8.8.8
    Rango: 23.6.1.10 - 23.6.1.100

------------------------------------------------------------------------

# 🌐 Acceso a Internet

El acceso a Internet se implementa mediante:

-   **Ruta por defecto hacia la interfaz WAN**
-   **NAT (PAT)**

Ejemplo:

    LAN Usuarios → WAN
    NAT habilitado

------------------------------------------------------------------------

# 🔐 Políticas de Seguridad

## Acceso HTTP

Los usuarios solo pueden acceder a la red de servidores utilizando
**HTTP**.

  Origen         Destino          Servicio   Acción
  -------------- ---------------- ---------- ----------
  LAN Usuarios   LAN Servidores   HTTP       Permitir
  LAN Usuarios   LAN Servidores   ANY        Bloquear

------------------------------------------------------------------------

# 🚫 Bloqueo de Redes Sociales

![alt text](image-3.png)

Se configuró **Application Control** para bloquear acceso a redes
sociales como:

-   Facebook
-   Instagram
-   TikTok
-   Twitter/X

Esto evita que los usuarios accedan a estas aplicaciones desde la red
interna.

------------------------------------------------------------------------

# 🌍 Bloqueo de Dominios

![alt text](image-4.png)

Se configuró filtrado para bloquear el dominio:

    *.itla.edu.do

Incluyendo subdominios como:

    itla.edu.do
    portal.itla.edu.do
    campus.itla.edu.do

Esto se implementó mediante **Web Filtering o DNS Filtering**.

------------------------------------------------------------------------

# 🛡️ Detección de Escáneres de Red

![alt text](image-5.png)

Se configuró el **IPS (Intrusion Prevention System)** del FortiGate para
detectar y bloquear herramientas de escaneo de red como:

-   Nmap
-   Masscan
-   Herramientas de reconocimiento de red

Las firmas del IPS detectan patrones de tráfico asociados a actividades
de escaneo.

------------------------------------------------------------------------

# 📊 Capas de Seguridad Implementadas

  Control de Seguridad    Función
  ----------------------- --------------------------------
  Políticas de Firewall   Filtrado de tráfico
  NAT                     Acceso a Internet
  DHCP                    Gestión automática de IP
  Application Control     Bloqueo de aplicaciones
  Web Filtering           Bloqueo de dominios
  IPS                     Detección de escaneo
  WAF                     Protección de aplicaciones web

------------------------------------------------------------------------

# 🎯 Objetivos de Aprendizaje

Este laboratorio permite practicar los siguientes conceptos:

-   Segmentación de redes
-   Diseño de políticas de firewall
-   Control de aplicaciones
-   Detección y prevención de intrusiones
-   Protección de aplicaciones web
-   Configuración de firewall empresarial
