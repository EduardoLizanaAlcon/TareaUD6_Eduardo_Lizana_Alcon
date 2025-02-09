# 📱 App de Gestión de empleados

## 🧩 Introducción

En este proyecto, voy a desarrollar una aplicación móvil diseñada para mejorar el la gestión de los empleados y que sea mas simple la manera tanto de fichar como de solicitar vacaciones, como para gestionar para los jefes el tiempo que trabaja cada empleado.

---

## 🎯 Objetivos

- 🏗 **Crear una interfaz accesible** basada en la optimización del espacio.
- 🎤 **Simplificar la gestion de empleados**, la organización de vacaciones y la de archivos .
- 📊 **Proporcionar herramientas para los trabajadores**, permitiéndoles gestionar el tiempo de trabajo, la gestión de vacaciones y tener una manera rapida de transferir archivos.

---

## 📌 Características Principales

✅ Interfaz sencilla e intuitiva.<br>
✅ Base de datos sincronizada para almacenar la información requerida.<br>
✅ Módulo administrativo exclusivo para administradores.<br> 
✅ Informes y estadísticas del tiempo trabajado de los empleados.

---

## 📊 Tecnologías Utilizadas

| Tecnología | Uso |
|------------|-----|
| ![Android Studio](https://img.shields.io/badge/Android-3DDC84?style=flat&logo=android&logoColor=white) | Desarrollo móvil |
| ![Kotlin](https://img.shields.io/badge/Kotlin-0095D5?style=flat&logo=kotlin&logoColor=white) | Lenguaje principal |
| ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white) | Base de datos |
| ![Figma](https://img.shields.io/badge/Figma-F24E1E?style=flat&logo=figma&logoColor=white) | Desarrollo Interfaz |

---

## 🔄 Flujo de la Aplicación

```mermaid
flowchart TD
    A[Inicio] --> B[Iniciar Sesión]
    B --> C{Seleccionar tipo de usuario}
    C -->|Jefe| D[Ingresar usuario y contraseña]
    C -->|Encargado| E[Ingresar usuario y contraseña]
    C -->|Empleado| F[Ingresar usuario y contraseña]
    D --> G[Gestión de empleados]
    D --> H[Subir archivos]
    D --> I[Acceder a archivos]
    D --> J[Gestión de vacaciones]
    D --> K[Fichar]
    E --> L[Subir archivos]
    E --> M[Acceder a archivos]
    E --> N[Gestión de vacaciones]
    E --> O[Fichar]
    F --> P[Acceder a archivos]
    F --> Q[Solicitar vacaciones]
    F --> R[Fichar]
    J --> S[Aprobar o Rechazar vacaciones]
    N --> T[Aprobar o Rechazar vacaciones]

```

---

## 📆 Planificación (Diagrama Gantt)

```mermaid
gantt
    title APP de Gestión de Empleados
    dateFormat  YYYY-MM-DD
    Estudio de requisitos y necesidades :done, 02-01, 02-10
    section Diseño y Desarrollo
    Diseño de la interfaz              :active, 03-01, 03-15
    Implementación de base de datos    :active, 03-16, 03-31
    Desarrollo del sistema de autenticación :active, 04-01, 04-10
    Gestión de empleados (CRUD)        :active, 04-11, 04-25
    Gestión de archivos y permisos     :active, 04-26, 05-05
    Sistema de fichaje                 : 05-06, 05-15
    Gestión de vacaciones              : 05-16, 05-25
    section Documentación
    Documentación técnica              : 06-16, 06-25
```

---
## 🐙 Planificación (Diagrama Git)

```mermaid
gitGraph
    commit id: "Configuración inicial"
    branch dev
    commit id: "Desarrollo de Interfaz"
    checkout main
    commit id: "Commit en main"
    merge dev
    commit id: "Merge de dev a main"
    branch bugfix
    commit id: "Error RecicleView"
    checkout dev
    commit id: "Implementación BBDD" tag: "v1.0.0"
    merge bugfix
    checkout dev
    commit id: "Desarrollar Funcionalidades" tag: "v1.2.0"
    checkout main
    merge dev
    commit id: "Merge de dev a main"
    commit id: "Versión 2.0.0" tag: "v2.0.0"
                                                                            

```

---
## 📊 Diagrama de Entidad-Relación Provisional

```mermaid
erDiagram
    USUARIO {
        string id_usuario
        string nombre
        string rol
    }
    ARCHIVO {
        string id_archivo
        string nombre
        string tipo
        string id_subido_por
        datetime fecha_subida
    }
    FICHAJE {
        string id_fichaje
        string id_usuario
        datetime fecha_hora
    }
    SOLICITUD_VACACIONES {
        string id_solicitud
        string id_usuario
        datetime fecha_solicitud
        string estado
    }

    USUARIO ||--o{ ARCHIVO : "sube"
    USUARIO ||--o{ FICHAJE : "registra"
    USUARIO ||--o{ SOLICITUD_VACACIONES : "solicita"
    SOLICITUD_VACACIONES }o--|| USUARIO : "gestionada_por"

```

---

## 📜 Diagrama de Secuencia Provisional

```mermaid
sequenceDiagram
    participant Usuario
    participant Sistema
    participant Encargado
    participant Jefe

    Usuario->>Sistema: Iniciar sesión
    Sistema-->>Usuario: Solicitar credenciales
    Usuario->>Sistema: Enviar credenciales
    Sistema-->>Usuario: Confirmar acceso

    Usuario->>Sistema: Fichar entrada/salida
    Sistema-->>Usuario: Confirmación de fichaje

    Usuario->>Sistema: Acceder a archivos
    Sistema-->>Usuario: Mostrar archivos disponibles

    Usuario->>Encargado: Solicitar vacaciones
    Encargado->>Sistema: Aprobar/Rechazar solicitud
    Sistema-->>Usuario: Notificar decisión

    Usuario->>Jefe: Solicitar revisión de solicitud rechazada
    Jefe->>Sistema: Aprobar/Rechazar solicitud
    Sistema-->>Usuario: Notificar decisión final

```

---

## 📜 Diagrama de Requerimientos

```mermaid
requirementDiagram
    requirement R1 {
        id: 1
        text: "La aplicación debe permitir a los usuarios iniciar sesión."
    }
    requirement R2 {
        id: 2
        text: "Los Administrador deben poder rechazar y aceptar vacaciones."
    }
    requirement R3 {
        id: 3
        text: "Los trabajadores pueden poder solicitar vacaciones."
    }
    requirement R4 {
        id: 4
        text: "El sistema debe registrar las acciones de los administradores/trabajadores/responsables."
    }
    requirement R5 {
        id: 5
        text: "Los trabajadores pueden descargar archivos de la plataforma."
    }
    requirement R6 {
        id: 6
        text: "Los administradores y encargados pueden subir/descargar archivos de la plataforma."
    }
    
    requirement R7 {
        id: 7
        text: "Los usuarios tienen que poder fichar y desfichar a las horas trabajadas."
    }
    requirement R8 {
        id: 8
        text: "Los Administradores/encargados tienen que poder obtener un informe de cada trabajador."
    }
```

---
## 📜 Diagrama de Journey

```mermaid
journey
    title Uso de la Plataforma de Gestión de Empleados
    section Inicio
        Abrir la plataforma: 5: Usuario
        Iniciar sesión: 4: Usuario
    section Funcionalidades Principales
        Fichar entrada/salida: 5: Usuario
        Acceder a archivos compartidos: 4: Usuario
        Subir archivos: 4: Encargado, Jefe
        Descargar archivos: 4: Usuario
    section Gestión de Vacaciones
        Solicitar vacaciones: 3: Usuario
        Revisar solicitudes de empleados: 4: Encargado, Jefe
        Aprobar/Rechazar solicitud: 5: Encargado, Jefe
        Recibir notificación de estado: 4: Usuario

```

---

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas! Para colaborar:

1. **Escribe tu propuesta** con aquello que has pensado.
2. **Envíalo por correo** al <eduardo@correo.com>.
3. **Nos pondremos en contacto** contigo si nos interesa tu propuesta.

---
