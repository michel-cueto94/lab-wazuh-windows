Laboratorio de Seguridad SIEM & XDR con Wazuh y Windows Server 2022

Descripción General
Este proyecto documenta el despliegue y la configuración de un laboratorio defensivo de Monitoreo de Seguridad (SIEM) y Respuesta Extendida (XDR). Se utilizó **Wazuh** desplegado sobre contenedores Docker en **Kali Linux** para monitorear, auditar y analizar eventos en tiempo real sobre un servidor objetivo **Windows Server 2022**.

Arquitectura y Tecnologías
- **Servidor SIEM / XDR:** Wazuh v4.9 (Desplegado en Docker sobre Kali Linux)
- **Host Monitoreado:** Windows Server 2022 (Agente Wazuh v4.9)
- **Entorno de Red:** Red nativa aislada en VirtualBo

Capacidades Implementadas en el Laboratorio

  1. Ingestión y Monitoreo de Eventos de Seguridad
- Configuración de políticas de auditoría en Windows Server.
- Captura en tiempo real de eventos de autenticación fallida (**Event ID 4625** / Regla `18108`) generados por intentos de inicio de sesión no autorizados vía NTLM/SMB.

  2. Detección Automatizada de Vulnerabilidades
- Escaneo continuo de parches de seguridad cruzando la versión del sistema operativo con bases de datos de **CVE (NVD/MITRE)**.
- Identificación de fallos críticos sin parchear en el endpoint (ej. fallos de ejecución remota de código en RDP y escalada de privilegios).

  3. Monitoreo de Integridad de Archivos (FIM)
- Configuración de monitoreo en tiempo real sobre el directorio `C:\Monitoreo`.
- Detección instantánea de creación, modificación y eliminación de archivos críticos (**Regla 550** - *Integrity checksum changed*).

  Evidencias de Captura (Alertas)
- **Fuerza Bruta / Fallos de inicio de sesión:** Eventos 4625 registrados en la interfaz de Wazuh Discover.
- **Modificación de Archivos (FIM):** Alertas en vivo ante cambios en sumas de verificación SHA256 sobre archivos `.txt`.
