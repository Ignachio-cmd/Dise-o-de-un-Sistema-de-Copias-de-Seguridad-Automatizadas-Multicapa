# Sistema de Copias de Seguridad Automatizadas Multicapa

## 1. Arquitectura General del Sistema

- Nivel 1: ______________________________________
- Nivel 2: ______________________________________
- Nivel 3: ______________________________________

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

