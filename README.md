# 📁 Infraestructura DNS Avanzada en Linux (BIND)

## 🌟 Resumen General del Repositorio

Este repositorio documenta una serie de prácticas esenciales para el despliegue y gestión de una infraestructura de **Servicio de Nombres de Dominio (DNS)** en un entorno Linux, utilizando el software **BIND (Berkeley Internet Name Domain)**. Los ejercicios cubren la implementación de alta disponibilidad, la seguridad y la funcionalidad de resolución inversa.

## 🎯 Objetivos Clave de las Actividades

Se consiguieron tres objetivos principales en las prácticas documentadas:

### 1. Alta Disponibilidad (Maestro-Esclavo)
* Se configuró un sistema **Maestro (`192.168.1.22`) y Esclavo (`192.168.1.26`)** para la zona `hamza.net`.
* Se validó que la transferencia de zona (AXFR/IXFR) solo se produce al incrementar el campo **Serial** del registro SOA.
* Se activaron las **Notificaciones DNS** para que el Maestro alerte inmediatamente al Esclavo sobre cambios de zona.

### 2. Seguridad (Control de Transferencia de Zona)
* Se implementó una política de seguridad estricta utilizando la directiva **`allow-transfer { 192.168.1.26; none; [cite_start]}`** en el Maestro.
* Se probó con éxito el **rechazo de transferencia de zona** (AXFR) desde un cliente no autorizado (`192.168.1.23`), confirmando la protección contra la recopilación de datos.

### 3. Resolución Inversa (PTR)
* Se creó y configuró una zona de resolución inversa (`1.168.192.in-addr.arpa`).
* Se verificó la funcionalidad creando registros **PTR** (Pointer) para mapear direcciones IP (ej. `192.168.1.22` y `192.168.1.23`) a sus respectivos nombres de host (`ns1.hamza.net`, `www.hamza.net`).

---

## 🛠️ Tecnologías y Herramientas Destacadas

| Componente | Uso Principal |
| :--- | :--- |
| **BIND9 (`named`)** | Servidor DNS principal en Linux. |
| **`dig`** | Herramienta esencial para diagnósticos, pruebas de resolución iterativa/recursiva y consulta de registros específicos (SOA, NS). |
| **`nslookup`** | Utilizado para consultas DNS rápidas y para probar la seguridad de la transferencia de zona desde un cliente Windows. |
| **`rndc dumpdb -zones`** | Comando clave utilizado en el Esclavo para volcar el contenido binario de la zona descargada a un fichero de texto legible (`named.dump.db`) para su documentación. |
| **Registros PTR** | Registros de recursos utilizados exclusivamente en la zona inversa para resolver de IP a nombre.

---

## 🔗 Ficheros y Documentos Clave

* `HamzaAkdi1_Servidor_Esclavo_Secuandario.pdf`: Documentación de la configuración Maestro-Esclavo, pruebas de Serial, Notificaciones y seguridad con `allow-transfer`.
* `HamzaAkdi1_DNS_en_Linux_Resolucion_Inversa.pdf`: Documentación sobre la creación de la zona inversa (`in-addr.arpa`) y la verificación de registros PTR.
* `Servicio_de_nombres_de_dominio_DNS.pdf`: Material teórico de apoyo que cubre los fundamentos del DNS.

---
