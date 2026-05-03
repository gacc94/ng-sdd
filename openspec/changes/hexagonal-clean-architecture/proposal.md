## Why

El proyecto necesita documentación arquitectural clara que guíe al equipo de desarrollo en la implementación consistente de patrones. Sin un documento de referencia, cada desarrollador interpreta la arquitectura de forma diferente, generando inconsistencias en la estructura del código, patrones de diseño y convenciones de nombrado.

## What Changes

- Crear documento `docs/architecture.md` con documentación completa de la arquitectura
- Incluir diagrama Mermaid de Arquitectura Hexagonal (Ports and Adapters)
- Incluir diagrama Mermaid de las capas de Clean Architecture con flujo de dependencias
- Incluir diagrama Mermaid de Vertical Slicing con organización de features
- Documentar reglas de dependencia entre capas
- Definir patrones de nombrado y estructura de archivos
- Incluir ejemplos de código para cada capa

## Capabilities

### New Capabilities

- `architecture-document`: Documento markdown con diagramas Mermaid que documenta la arquitectura hexagonal, clean architecture y vertical slicing del proyecto

### Modified Capabilities

- Ninguno.

## Impact

- Documentación: Nuevo archivo `docs/architecture.md` como referencia arquitectural
- Proceso: El documento será la fuente de verdad para decisiones de arquitectura
- Onboarding: Nuevo desarrolladores podrán entender la arquitectura rápidamente