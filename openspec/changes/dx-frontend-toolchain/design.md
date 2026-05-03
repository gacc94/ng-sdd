## Context

El proyecto frontend actual utiliza un toolchain fragmentado con múltiples herramientas para linting, formatting y Git hooks. Prettier y ESLint requieren configuraciones separadas y procesos de ejecución independientes. Husky gestiona los Git hooks pero presenta limitaciones en flexibilidad y rendimiento. No existe un pipeline de CI/CD estructurado en GitHub Actions. El objetivo es consolidar estas herramientas en un toolchain unificado y moderno que mejore la experiencia del desarrollador.

## Goals / Non-Goals

**Goals:**
- Adoptar Bun como package manager y runtime principal del proyecto (ya instalado localmente)
- Adoptar Vitest como test runner principal (ya instalado localmente, compatible con Jest API)
- Implementar Biome como herramienta única de linting y formatting
- Configurar commitlint con Conventional Commits para estandarizar mensajes de commit
- Migrar a lefthook para gestión de Git hooks
- Crear pipelines de CI/CD en GitHub Actions para validación automática (requiere instalación de Bun en runners)
- Reducir complejidad de configuración y mantenimiento del toolchain

**Non-Goals:**
- No se contempla migración de código existente
- No se incluye integración con otras herramientas de terceros (SonarQube, Snyk)
- No se implementa análisis de código en tiempo de ejecución en producción
- No se mantiene compatibilidad con npm/yarn/pnpm (solo Bun)
- No se mantiene Jest como test runner (solo Vitest)

## Decisions

1. **Bun como package manager y runtime**: Bun ofrece rendimiento superior (hasta 10x más rápido que npm para instalación de dependencias), runtime de JavaScript integrado, y gestión unificada de scripts. Ya instalado localmente. En CI/CD se instala con `oven-sh/setup-bun@v1`. Usa `bun.lockb` para lockfile.

2. **Vitest como test runner**: Vitest es un test runner moderno basado en Vite que ofrece compatibilidad con la API de Jest, ejecución en paralelo ultra-rápida, y nativamente compatible con TypeScript. Ya instalado localmente. Se integra perfectamente con Bun para velocidad extrema. Los tests ya existen en node_modules.

3. **Biome en lugar de Prettier + ESLint**: Biome ofrece rendimiento superior (escrito en Rust), configuración unificada en un solo archivo `biome.json`, y combina capacidades de linting y formatting. La migración reduce complejidad y mejora velocidad.

4. **lefthook en lugar de Husky**: lefthook es más rápido, permite configuración en YAML/JSON, y no requiere instalación de dependencias en el sistema. Además, es más fácil de integrar con herramientas como Biome y commitlint.

5. **GitHub Actions para CI/CD**: GitHub Actions es la plataforma nativa del repositorio. Se implementarán workflows para lint, test, y deployment con caching de dependencias para optimizar tiempos de ejecución. Los runners de CI requieren instalación de Bun con `oven-sh/setup-bun@v1`, pero no necesitan instalar Vitest (ya está en node_modules tras `bun install`).

6. **Conventional Commits con commitlint**: Estandarización de mensajes de commit para facilitar generación automática de changelogs, versionado semántico automatizado, y mejor trazabilidad en el historial del proyecto.

## Risks / Trade-offs

- **[Riesgo] Curva de aprendizaje del equipo** → **Mitigación**: Documentación clara y ejemplos de configuración. Los mensajes de error de Biome son más claros que los de ESLint.

- **[Riesgo] Compatibilidad con configuración existente de Prettier** → **Mitigación**: Biome puede importar configuraciones de Prettier. Se realizará migración gradual.

- **[Riesgo] breaking changes en Biome** → **Mitigación**: Usar versión estable y actualizar con pruebas de regresión.

- **[Riesgo] Workflows de CI/CD complejos** → **Mitigación**: Comenzar con pipeline básico (lint + test) y expandir gradualmente.

## Migration Plan

1. **Fase 1**: Verificación de Bun y migración de package manager (ya instalado localmente, generar bun.lockb)
2. **Fase 2**: Verificación de Vitest y configuración de vitest.config.ts (ya instalado localmente)
3. **Fase 3**: Instalación de dependencias (biome, commitlint, lefthook) usando Bun
4. **Fase 4**: Configuración de Biome con reglas equivalentes a Prettier/ESLint actuales
5. **Fase 5**: Configuración de commitlint con Conventional Commits
6. **Fase 6**: Configuración de lefthook para pre-commit y commit-msg
7. **Fase 7**: Creación de workflows de GitHub Actions con Bun (instalación requerida en CI) y Vitest (ya en node_modules)
8. **Fase 8**: Desinstalación de herramientas antiguas (Prettier, ESLint, Husky, Jest) y eliminación de package-lock.json

**Rollback**: Mantener configuración anterior en branch separada por 2 semanas antes de eliminar.

## Open Questions

- ¿Se requiere integración con Angular CLI para comandos de lint específicos?
- ¿Qué estrategia de branching se usará para deployments (gitflow, trunk-based)?
- ¿Se necesita configuración específica para TypeScript estricto?