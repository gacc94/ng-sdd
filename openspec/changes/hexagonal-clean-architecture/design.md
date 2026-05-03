## Context

El proyecto Angular necesita un documento de arquitectura que sirva como referencia para todo el equipo. Actualmente no existe documentación formal que explique la estructura, patrones y convenciones del proyecto. La arquitectura combina Hexagonal (Ports and Adapters), Clean Architecture y Vertical Slicing.

## Goals / Non-Goals

**Goals:**
- Crear `docs/architecture.md` con documentación completa
- Incluir diagramas Mermaid visuales para cada aspecto arquitectural
- Documentar reglas de dependencia entre capas
- Proporcionar ejemplos de código para cada patrón
- Incluir guía de estructura de carpetas

**Non-Goals:**
- No se implementa código de la arquitectura en este cambio
- No se migra código existente
- No se crean templates o scaffolds

## Decisions

1. **Formato Markdown con Mermaid**: Los diagramas Mermaid se renderizan nativamente en GitHub, GitLab y la mayoría de IDEs. Esto permite que la documentación sea versionable y visible sin herramientas adicionales.

2. **Diagramas incluidos**:
   - Diagrama de Arquitectura Hexagonal: muestra core domain, ports de entrada/salida, y adaptadores
   - Diagrama de Capas Clean Architecture: muestra Domain → Application → Infrastructure → Presentation con flujo de dependencias
   - Diagrama de Vertical Slicing: muestra cómo cada feature contiene todas sus capas
   - Diagrama de flujo de datos: muestra cómo viaja una request desde el componente hasta el dominio y back

3. **Estructura del documento**: Visión general → Arquitectura Hexagonal → Clean Architecture → Vertical Slicing → Reglas → Ejemplos → Convenciones

## Risks / Trade-offs

- **[Riesgo] Diagramas Mermaid complejos** → **Mitigación**: Mantener diagramas simples y legibles, evitar sobrecarga visual
- **[Riesgo] Documentación desactualizada** → **Mitigación**: Incluir revisión de docs en PR reviews
- **[Riesgo] Demasiado detalle** → **Mitigación**: Enfocar en patrones y reglas, no en implementación específica

## Migration Plan

1. Crear estructura del documento con secciones definidas
2. Crear diagramas Mermaid para cada aspecto
3. Agregar ejemplos de código
4. Revisión y aprobación del equipo

## Open Questions

- ¿Dónde ubicar el documento? `docs/architecture.md` es el estándar
- ¿Se necesitan diagramas adicionales de secuencia?