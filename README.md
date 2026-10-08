# Sistema de Gestión Académica

Aplicación de consola en Java para gestionar **estudiantes** y **cursos** (registrar, listar, actualizar y eliminar), organizada en capas con inyección de dependencias. Los datos se guardan en archivos JSON con Gson.

## Arquitectura

```
com.academico
├── application          → Servicios (lógica de la aplicación)
│   ├── CursoService
│   └── EstudianteService
├── domain
│   ├── model            → Entidades
│   │   ├── Curso
│   │   └── Estudiante
│   └── repository       → Interfaces (contratos de persistencia)
│       ├── CursoRepository
│       └── EstudianteRepository
├── infrastructure       → Implementaciones de persistencia en JSON
│   ├── CursoRepositoryJson
│   └── EstudianteRepositoryJson
├── presentation         → Menús de consola
│   ├── CursoUI
│   └── EstudianteUI
└── Main                 → Crea y conecta las capas
```

Flujo de dependencias:

```
Main → UI → Service → Repository (interfaz) ← RepositoryJson
```

Los servicios dependen de la **interfaz** del repositorio, no de la implementación JSON. `Main` crea las implementaciones y las inyecta por constructor.

## Datos

- `data/estudiantes.json`
- `data/cursos.json`

## Ejecución

Requisitos: JDK 25 y Maven.

- **IntelliJ:** abrir el proyecto, cargar Maven y ejecutar `Main`.
- **Terminal** (desde la raíz del proyecto):

```bash
mvn compile
mvn exec:java -Dexec.mainClass=com.academico.Main
```
