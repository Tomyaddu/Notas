Un poquito mas en profundidad los conceptos de COM, OneView y COM-OneView Edition. Estos son los temas que se van a abordar ![[Pasted image 20260713164337.png]]
Muchos conceptos se explicaron en [[Effortless Compute Management at Scale]], así que esta presentación tendrá mucho de los conceptos ya cubiertos, lo mas destacable de la presentación es que hacen de nuevo un deep dive a iLO, luego muestran los roadmaps para las 3 aplicaciones.

### iLO – Actualizaciones clave (iLO7)

Nuevo ASIC de iLO con foco en **seguridad multicapa**: cumple **FIPS 140-3 Level 3**, soporte de resistencia cuántica, nueva WebUI, soporte de arquitectura DC-MHS, y retiro de interfaces legacy (RIBCL, SMASH-CLP, CHIF, iLO Federation, .NET IRC). Se destaca el contexto de servidores optimizados para IA (ej. DL380a Gen12 con NVIDIA H200 NVL).

**Secure Enclave (deep dive):** ofrece un entorno resistente a manipulaciones, elimina vulnerabilidades de EEPROM externa, realiza de forma autónoma el Silicon Root of Trust (SRoT) y su recuperación, gestión avanzada de llaves/certificados, y transferencia de propiedad sin hardware externo. El SRoT en Gen12 arranca desde un chip de enclave inaccesible que valida a iLO antes de que ejecute código (protección ante firmware de iLO comprometido), con múltiples respaldos de firmware en distintos medios para recuperación ante fallas.

HPE se posiciona como el **primer fabricante en cumplir FIPS 140-3 Level 3** y en soportar los requisitos de resistencia cuántica NIST/CNSA 2.0 (firma segura de firmware), a través de iLO 7 (requiere Gen12).

**Nueva GUI de iLO7:** rediseño orientado a flujos de trabajo, con barra de menú simplificada en 6 áreas clave (overview, firmware, host, seguridad, apps HPE, configuración de iLO), tarjetas modernas con info a simple vista, nueva barra de búsqueda para acceso instantáneo, y un menú "Quick Glance" con estado de salud del servidor (verde/amarillo/rojo).![[Pasted image 20260717092106.png]]
![[Pasted image 20260717092116.png]]
![[Pasted image 20260717092128.png]]
![[Pasted image 20260717092142.png]]
![[Pasted image 20260717092204.png]]
![[Pasted image 20260717092219.png]]

