# Sistema de Copias de Seguridad Automatizadas Multicapa

## 1. Arquitectura General del Sistema

- Nivel 1: - En este primer nivel, cada equipo realizará de forma independiente una copia de seguridad de sus datos y configuraciones, utilizando su propio sistema operativo (Linux, Windows o macOS). Para ello, se podrán usar herramientas comunes como Duplicati o soluciones específicas para cada plataforma.
  La copia de seguridad se generará en formato ISO y se almacenará en una carpeta local. Esta carpeta tendrá un nombre identificativo que incluya el nombre del equipo y la fecha en la que se ha realizado el backup, con el objetivo de mantener un orden y facilitar futuras restauraciones.
  <p><p>
- Nivel 2: En este segundo nivel, la carpeta generada en el nivel anterior que contiene el archivo ISO con el respaldo completo se transferirá a un servidor central, un equipo designado o un dispositivo NAS. Este repositorio centralizado almacenará las copias de seguridad de todos los equipos, organizadas en subcarpetas individuales para cada uno de las backups de los equipos, respetando la misma convención de nombres, con el fin de asegurar una correcta trazabilidad y acceso.Para aumentar la seguridad e integridad de los datos almacenados, se recomienda que el servidor central o NAS utilice una configuración de almacenamiento RAID 5. Este tipo de RAID distribuye los datos y la paridad entre varios discos, lo que permite que, en caso de fallo de uno de ellos, la información pueda recuperarse sin pérdida de datos. Así nos garantizamos una mayor tolerancia a fallos y disponibilidad del sistema de backups.
  <p><p>
- Nivel 3: Por último, en este tercer nivel, el repositorio central que almacena todas las copias ISO será respaldado en un sistema de almacenamiento en la nube. Este nivel está diseñado para garantizar la continuidad de la empresa ante situaciones críticas, como desastres físicos (por ejemplo, un incendio en la empresa). Al tener una copia de seguridad externa en la nube, se añade una capa adicional de seguridad y tranquilidad, asegurando que los datos puedan recuperarse incluso si los niveles anteriores se ven comprometidos.

![esquema](imgs/esquema.jpg)

---

## 2. Configuración del Nivel 1: PCs Individuales

### a. Selección de software

- Windows: ______________________
- macOS: ________________________
- Linux: _________________________

### b. Programación de copias

- ¿Cómo se configuran las copias incrementales diarias?
- ¿Cómo se hacen las copias completas semanales?

### c. Destino de las copias

- ¿Dónde se almacenan?
- ¿Cómo se organizan las carpetas por PC?

---

## 3. Configuración del Nivel 2: Servidor Local Primario

### a. Tipo de hardware elegido

- Opción: NAS / Ordenador (elige uno)
- Marca/modelo (si aplica): ________________
- Sistema operativo: ________________________

### b. Tipo de RAID

- Elegido: RAID 1 / RAID 5 / RAID 10
- Justificación:

### c. Software de gestión

- Software elegido: __________________________
- Función principal: __________________________

---

## 4. Configuración del Nivel 3: Servidor Secundario Remoto

### a. Tipo de servidor remoto

- Opción elegida: NAS remoto / Nube / PC remoto
- Justificación:

### b. Seguridad de la sincronización

- ¿Cómo se programa la sincronización?
- ¿Qué cifrado se usa?
- ¿Se puede activar doble autenticación?

---

## 5. Automatización del Proceso

- Script de verificación:
- Alerta por email: ¿Cómo se configura?
- Prueba de restauración: ¿Cada cuánto tiempo? ¿Cómo?

---

## 6. Justificación del uso de RAID

- ¿Por qué no sustituye al backup?
- ¿Qué pasa si solo tenemos RAID?

---

## 7. Resumen de Software Recomendado

| Función                        | Software Recomendado     |
|-------------------------------|--------------------------|
| Gestión centralizada          | Urbackup, Veeam B&R                         |
| Sincronización entre servidores| Rclone, Duplicati                      |
| Monitorización                | Nagios, Zabbix                       |
| Clientes Windows              | Veeam Agent Free                         |
| Clientes Linux                | Timeshift + rsync                         |
| Almacenamiento NAS            | Synology Hyper Backup                         |

---

## Bibliografía / Fuentes consultadas

- Fuente 1: [link software de back ups](https://www.techradar.com/best/best-backup-software)
- Fuente 2: [mejores softwares de backup elegidos por usuarios](https://www.g2.com/categories/backup)
- Fuente 3: [Software backups](https://en.wikipedia.org/wiki/List_of_backup_software)
- 

