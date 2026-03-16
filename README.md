# 🔥 Laboratorio de Seguridad de Red con FortiGate

## 📌 Descripción

Este proyecto demuestra la implementación y configuración de un
**firewall Fortinet FortiGate** para proteger una red segmentada.

El laboratorio simula una red empresarial pequeña con dos segmentos
principales:



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

<img width="948" height="560" alt="image" src="https://github.com/user-attachments/assets/d97c47df-795f-4542-ab6d-c3c1575b6187" />

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

<img width="779" height="332" alt="image" src="https://github.com/user-attachments/assets/ccdbb872-1e3f-4137-bbf5-8d40f10440bd" />

  Interfaz   Red             Función
  ---------- --------------- ---------------------
  port1      DHCP            Conexión a Internet
  port2      23.6.1.128/28   LAN de servidores
  port3      23.6.1.0/25     LAN de usuarios

------------------------------------------------------------------------

# 📡 Configuración de DHCP

<img width="1124" height="383" alt="image" src="https://github.com/user-attachments/assets/4c0d71a5-9bea-43e4-bef1-e3c17f4ffad8" />

Se configuró **DHCP en la red de usuarios** para asignar direcciones IP
automáticamente.

configuración:

    Red: 23.6.1.0/25
    Gateway: 23.6.1.1
    DNS: 8.8.8.8
    Rango: 23.6.1.10 - 23.6.1.100

------------------------------------------------------------------------

# 🌐 Acceso a Internet

<img width="779" height="362" alt="image" src="https://github.com/user-attachments/assets/3a73c3e2-3394-47e9-91df-66466e9979a8" />

El acceso a Internet se implementa mediante:

-   **Ruta por defecto hacia la interfaz WAN**
-   **NAT (PAT)**

------------------------------------------------------------------------

# 🔐 Políticas de Seguridad

<img width="1414" height="954" alt="image" src="https://github.com/user-attachments/assets/ff5bc9bc-82c1-4fb7-a34d-aa99ada2ce87" />


## Acceso HTTP

Los usuarios solo pueden acceder a la red de servidores utilizando
**HTTP**.

  Origen         Destino          Servicio   Acción
  -------------- ---------------- ---------- ----------
  LAN Usuarios   LAN Servidores   HTTP       Permitir
  LAN Usuarios   LAN Servidores   ANY        Bloquear

------------------------------------------------------------------------

# 🚫 Bloqueo de Redes Sociales

<img width="770" height="503" alt="image" src="https://github.com/user-attachments/assets/775cd0d0-5b08-49df-b7d9-578c7f0fa23d" />


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

<img width="782" height="499" alt="image" src="https://github.com/user-attachments/assets/ca96b7d6-219e-462f-aac1-0fd644e5bf8b" />


Se configuró filtrado para bloquear el dominio:

    *.itla.edu.do

Incluyendo subdominios como:

    itla.edu.do
    portal.itla.edu.do
    campus.itla.edu.do

Esto se implementó mediante **Web Filtering o DNS Filtering**.

------------------------------------------------------------------------

# 🛡️ Detección de Escáneres de Red

<img width="378" height="159" alt="image" src="https://github.com/user-attachments/assets/25fd892f-79b6-4ae1-8e53-6208835c80b6" />


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
