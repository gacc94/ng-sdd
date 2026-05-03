## 1. Crear Estructura del Documento

- [x] 1.1 Crear directorio `docs/` en raíz del proyecto
- [x] 1.2 Crear archivo `docs/architecture.md`
- [x] 1.3 Definir secciones del documento con encabezados

## 2. Diagrama Mermaid - Arquitectura Hexagonal

- [x] 2.1 Crear diagrama Mermaid con forma hexagonal
- [x] 2.2 Mostrar Core Domain en el centro (Entities, Value Objects)
- [x] 2.3 Mostrar Input Ports (Use Cases) como interfaz de entrada
- [x] 2.4 Mostrar Output Ports (Repository Interfaces) como interfaz de salida
- [x] 2.5 Mostrar Primary Adapters (UI Components, CLI, API)
- [x] 2.6 Mostrar Secondary Adapters (Database, External APIs, File System)

## 3. Diagrama Mermaid - Clean Architecture Layers

- [x] 3.1 Crear diagrama de capas concéntricas o en capas
- [x] 3.2 Mostrar Domain layer (Entities, Value Objects, Domain Events)
- [x] 3.3 Mostrar Application layer (Use Cases, Port Interfaces)
- [x] 3.4 Mostrar Infrastructure layer (Repositories, HTTP Clients)
- [x] 3.5 Mostrar Presentation layer (Angular Components, Guards)
- [x] 3.6 Mostrar dirección de dependencias (flechas hacia Domain)

## 4. Diagrama Mermaid - Vertical Slicing

- [x] 4.1 Crear diagrama mostrando organización vertical
- [x] 4.2 Mostrar features como slices verticales
- [x] 4.3 Mostrar capas dentro de cada feature
- [x] 4.4 Mostrar shared kernel para código común

## 5. Diagrama Mermaid - Data Flow

- [x] 5.1 Crear diagrama de secuencia o flujo
- [x] 5.2 Mostrar flujo: Component → Use Case → Entity → Repository → External
- [x] 5.3 Mostrar flujo de retorno con datos

## 6. Documentar Reglas de Arquitectura

- [x] 6.1 Documentar regla: Domain no depende de nada
- [x] 6.2 Documentar regla: Application depende solo de Domain
- [x] 6.3 Documentar regla: Infrastructure implementa Application ports
- [x] 6.4 Documentar regla: Presentation depende de Application

## 7. Agregar Ejemplos de Código

- [x] 7.1 Ejemplo de Entity en Domain layer
- [x] 7.2 Ejemplo de Value Object en Domain layer
- [x] 7.3 Ejemplo de Use Case en Application layer
- [x] 7.4 Ejemplo de Repository Interface en Application layer
- [x] 7.5 Ejemplo de Repository Implementation en Infrastructure layer
- [x] 7.6 Ejemplo de Component en Presentation layer con Signals

## 8. Convenciones y Guías

- [x] 8.1 Documentar patrones de nombrado para cada capa
- [x] 8.2 Documentar estructura de carpetas por feature
- [x] 8.3 Agregar tabla resumen de dependencias permitidas
- [x] 8.4 Agregar sección de preguntas frecuentes (FAQ)