## Why

El desarrollo frontend actual requiere un toolchain robusto y eficiente para mantener calidad de código, consistencia y productividad. Las herramientas tradicionales como Prettier, ESLint y Husky representan soluciones fragmentadas que，增加了 complejidad en la configuración y mantenimiento. Biome ofrece una alternativa moderna unificada que combina linting y formatting en una única herramienta, mientras que lefthook proporciona una solución más flexible para Git hooks. Este cambio busca modernizar el DX (Developer Experience) del proyecto implementando un toolchain optimizado.

## What Changes

- Usar Bun como package manager y runtime en todo el proyecto (reemplazando npm/yarn/pnpm) - ya instalado localmente
- Usar Vitest como test runner (reemplazando Jest o Karma/Jasmine) - ya instalado localmente
- Reemplazar Prettier y ESLint por Biome como herramienta unificada de linting y formatting
- Implementar commitlint con Conventional Commits para validación de mensajes de commit
- Migrar de Husky a lefthook para la gestión de Git hooks
- Configurar GitHub Actions para pipelines de CI/CD con linting, testing y deployment (requiere instalación de Bun en runners)
- Establecer workflow de commits convencionales en todo el equipo

## Capabilities

### New Capabilities

- `biome-integration`: Integración de Biome como herramienta de linting y formatting unificada para el proyecto frontend
- `conventional-commits`: Sistema de conventional commits con commitlint para mensajes de commit estandarizados
- `git-hooks-management`: Gestión de Git hooks mediante lefthook para pre-commit, commit-msg y otros hooks
- `ci-cd-pipeline`: Pipeline de CI/CD en GitHub Actions para validación automática y deployment

### Modified Capabilities

- Ninguno existente. Esta es una capacidad nueva para el proyecto.

## Impact

- Dependencias: Se agregarán biome, commitlint, lefthook, vitest y configuración de GitHub Actions. El package manager cambia de npm a Bun, y el test runner de Jest a Vitest.
- Código: Archivos de configuración en la raíz del proyecto y en `.github/workflows/`. Uso de `bun.lockb` en lugar de `package-lock.json`. Archivo `vitest.config.ts` para configuración del test runner.
- Proceso: Cambios en el flujo de trabajo del desarrollador para commits, validaciones y testing con Vitest + Bun
- Integración: Nueva pipeline de CI/CD en el repositorio con Bun y Vitest