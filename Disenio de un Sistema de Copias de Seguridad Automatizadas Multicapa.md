# Sistema de Copias de Seguridad Automatizadas Multicapa

## 1. Arquitectura General del Sistema

- Nivel 1: En este primer nivel, cada equipo realizará de forma independiente una copia de seguridad de sus datos y configuraciones, utilizando su propio sistema operativo (Linux, Windows o macOS). Para ello, se podrán usar herramientas comunes como Duplicati o soluciones específicas para cada plataforma.
  La copia de seguridad se generará en formato ISO y se almacenará en una carpeta local. Esta carpeta tendrá un nombre identificativo que incluya el nombre del equipo y la fecha en la que se ha realizado el backup, con el objetivo de mantener un orden y facilitar futuras restauraciones.
  <p><p>
- Nivel 2: En este segundo nivel, la carpeta generada en el nivel anterior que contiene el archivo ISO con el respaldo completo se transferirá a un servidor central, un equipo designado o un dispositivo NAS. Este repositorio centralizado almacenará las copias de seguridad de todos los equipos, organizadas en subcarpetas individuales para cada uno de las backups de los equipos, respetando la misma convención de nombres, con el fin de asegurar una correcta trazabilidad y acceso.Para aumentar la seguridad e integridad de los datos almacenados, se recomienda que el servidor central o NAS utilice una configuración de almacenamiento RAID 5. Este tipo de RAID distribuye los datos y la paridad entre varios discos, lo que permite que, en caso de fallo de uno de ellos, la información pueda recuperarse sin pérdida de datos. Así nos garantizamos una mayor tolerancia a fallos y disponibilidad del sistema de backups.
  <p><p>
- Nivel 3: Por último, en este tercer nivel, el repositorio central que almacena todas las copias ISO será respaldado en un sistema de almacenamiento en la nube. Este nivel está diseñado para garantizar la continuidad de la empresa ante situaciones críticas, como desastres físicos (por ejemplo, un incendio en la empresa). Al tener una copia de seguridad externa en la nube, se añade una capa adicional de seguridad y tranquilidad, asegurando que los datos puedan recuperarse incluso si los niveles anteriores se ven comprometidos.

![esquema](imgs/esquema.jpg)

---

## 2. Configuración del Nivel 1: PCs Individuales

### a. Selección de software

- Windows: Windows: Duplicati, una herramienta gratuita y de código abierto la cual ofrece copias de
  seguridad cifradas, comprimidas, automáticas e incrementales, con una interfaz web fácil de usar
  y compatibilidad con almacenamiento local, en red y en la nube.
  ● Es una herramienta gratuita y open source.
  ● Realiza copias de seguridad cifradas y comprimidas.
  ● Permite hacer backups automáticos e incrementales en la nube o en servidores remotos.
  ● Cuenta con una interfaz web fácil de usar.
  ● Es compatible con carpetas locales, discos duros externos, servidores en red y servicios
  en la nube.
  ● Se puede programar con gran flexibilidad (diaria, semanal, etc.).
  <p><p>
- macOS: macOS: Time Machine, herramienta nativa de macOS, que realiza copias de seguridad
  automáticas e incrementales cada hora en unidades de almacenamiento externas o de red,
  destacando por su sencillez y la capacidad de restaurar archivos individuales o el sistema
  completo.
  ● Es gratuito y viene preinstalado en todos los Mac.
  ● Tiene una interfaz sencilla.
  ● Realiza copias de seguridad incrementales automáticas cada hora.
  ● Permite restaurar archivos individuales o el sistema completo desde una fecha específica.
  ● Es compatible con discos duros locales o en red (Time Capsule, servidores NAS
  compatibles).
  ● Almacena múltiples versiones de archivos, ideal para la recuperación por error del
  usuario.
  <p><p>
- Linux: Linux: rsync, es una herramienta de línea de comandos para copias de seguridad y sincronización
  de archivos, eficiente por transferir solo los cambios. Ofrece compresión, cifrado mediante SSH,
  sincronización bidireccional y es fácilmente programable.
  ● Compresión: Soporta la compresión de datos durante la transferencia para reducir el uso
  de ancho de banda.
  ● Seguridad: Permite el cifrado con SSH para transferencias seguras.
  ● Sincronización bidireccional: Puede mantener dos directorios sincronizados entre sí.
  ● Programación fácil: Se puede automatizar con cron o tareas programadas.
  ● Detección de errores: Asegura que los archivos copiados sean exactos mediante un
  mecanismo de verificación.
  ● Transfiere solo los cambios realizados en los archivos, lo que la hace rápida y eficiente.
  ● Es ideal para backups locales o remotos

### b. Programación de copias

Hablemos y escogeremos Duplicati, debido a que anteriormente lo he tratado. Duplicati como la
actividad hemos comentado Duplicati es una herramienta gratuita y open source para realizar
copias de seguridad automáticas, cifradas y comprimidas. Es compatible con múltiples
plataformas y permite almacenar los datos en la nube o servidores remotos.

- ¿Cómo se configuran las copias incrementales diarias?
  
  <p><p>
  
  Para configurar las copias incrementales diarias en Duplicati, primero debemos abrir el programa y
  crear una nueva tarea de copia de seguridad. En la configuración de esta tarea, accederemos al
  apartado de "Horario", donde activaremos la opción "Ejecutar automáticamente". A continuación,
  seleccionaremos el horario en el que deseamos que se ejecute la copia, asegurándonos de elegir un
  momento que no interfiera con el rendimiento de la red o los recursos del sistema, ya que durante la
  ejecución de Duplicati, el uso de la CPU y el tráfico de red aumentarán. Después, en el apartado de
  Tipo de copia de seguridad, seleccionaremos la opción Incremental para que sólo se respalden los
  archivos modificados desde la última copia. Finalmente, configuraremos la tarea para que se ejecute
  de manera diaria, lo que garantizará que las copias incrementales se realicen automáticamente cada
  día sin necesidad de intervención manual.
  
  <p><p><p>
- ¿Cómo se hacen las copias completas semanales?
  
  <p><p>
  
  Para programar copias completas semanales en Duplicati, primero abrimos el programa y nos
  dirigimos a la ventana de “Horario”. Ahí, configuramos una nueva tarea de copia de seguridad,
  seleccionando la opción Semanal. Elegimos el día de la semana en que queremos realizar la copia
  completa, como por ejemplo, todos los domingos. Luego, definimos una hora para que se ejecute la
  copia, preferentemente en un horario de baja actividad, como a las 2:00 AM, para minimizar el
  impacto en el rendimiento del sistema. Nos aseguramos de seleccionar el tipo de backup como
  Completa, para que se respalden todos los archivos, no solo los modificados. Con esta configuración,
  las copias de seguridad completas se realizan de forma automática cada semana, asegurando que se
  conserve una copia íntegra de todos los archivos.

### c. Destino de las copias

- ¿Dónde se almacenan?
  <p><p>
  Las copias ISO se almacenan en un servidor central o NAS, al que se accede mediante la red local.
  <p><p>
- ¿Cómo se organizan las carpetas por PC?
  <p><p>
  Las copias se organizan en subcarpetas dentro del servidor, usando un nombre que incluye el nombre del equipo y la fecha (por ejemplo: PC-Miguel_angel-05-08), lo que permite una trazabilidad clara y ordenada.

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

- Opción elegida: Nube (Google Cloud, Azure o AWS)
  
  <p><p>
  
  ![nube](imgs/nube.png)
  
- Justificación: La nube garantiza que los datos se almacenen en una ubicación física separada del
  servidor local, lo que es crucial en caso de incidentes catastróficos (incendios,
  inundaciones, etc.).
  Ofrece escalabilidad, alta disponibilidad y, en muchos casos, integraciones automatizadas
  para la sincronización de datos

### b. Seguridad de la sincronización

- ¿Cómo se programa la sincronización?
  
  Se programa atreaves de servicios nativos de la nube como es Google Cloud, herramientas del sistema operativo como rsync o software de terceros especializado que nos permiten configurar tareas recurrentes con diferentes frecuencias y filtros.
  
  <p>
- ¿Qué cifrado se usa?
  
  Las nubes principales cifran los datos en reposo osease cuando ya estan almacenados por defecto, normalmente con AES-256. También cifran los datos en tránsito osease durante la transferencia de los datos usando protocolos seguros como SSL/TLS pero tambien hay opciones adicionales para gestionar nuestras propias claves de cifrado si lo necesitasemos.
  
  <p>
- ¿Se puede activar doble autenticación?
  
  Sí ademas de que es altamente recomendable y encima es posible activar la autenticación multifactor para las cuentas de usuario que gestionan y acceden a los recursos de almacenamiento en la nube. Esto nos añade una capa de seguridad pidiendo una segunda verificación además de la contraseña para iniciar sesión, protege el acceso a la configuración y administración, aunque la sincronización automática use métodos de autenticación de servicio diferentes.

---

## 5. Automatización del Proceso

- Script de verificación:
- Alerta por email: ¿Cómo se configura?
- Prueba de restauración: ¿Cada cuánto tiempo? ¿Cómo?

---

## 6. Justificación del uso de RAID

- ¿Por qué no sustituye al backup?
  
  El RAID nos protege contra la pérdida de datos causada por el fallo físico de uno o varios discos duros, manteniendo la disponibilidad del sistema al distribuir o duplicar la información entre ellos pero el RAID no es una solución de copia de seguridad porque no nos protege contra la corrupción lógica de datos, el borrado accidental de archivos, los ataques de malware o ransomware que cifran o eliminan información, ni desastres que afecten al servidor completo o su ubicación física. En resumen el RAID mantiene la redundancia de los datos actuales, mientras que un backup crea una copia histórica e independiente de los datos para permitir la recuperación ante cualquier evento que no sea simplemente un fallo de disco.
  
  <p>
- ¿Qué pasa si solo tenemos RAID?
  
  Si ocurre cualquiera de los escenarios anteriores como borrado accidental, ransomware, fallo total del servidor, etc... , perderiamos nuestros datos irremediablemente aunque el array RAID esté técnicamente "sano" o los discos individuales funcionen, los datos dentro del array se habrian borrado, corrompido o vuelto inaccesibles. El RAID no tiene "memoria" de versiones anteriores de tus archivos ni puede revertir cambios lógicos o externos; solo mantiene la estructura de datos actual redundada entre los discos.

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
- Fuente 4: [Raid de discos duros, todo lo que necesitas saber](https://computerhoy.20minutos.es/pc/raid-beneficios-pc-1370709)
- Fuente 5: []()

