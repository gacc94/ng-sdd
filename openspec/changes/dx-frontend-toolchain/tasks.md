## 1. Verificación de Bun y Migración de Package Manager (Local)

- [x] 1.1 Verificar que Bun está instalado ejecutando `bun --version` (ya instalado localmente)
- [x] 1.2 Eliminar package-lock.json existente (si existe)
- [x] 1.3 Ejecutar `bun install` para generar bun.lockb
- [x] 1.4 Actualizar scripts en package.json para usar bun (bun run en lugar de npm run)
- [x] 1.5 Verificar que todos los scripts funcionan correctamente con bun

## 2. Configuración de Vitest (Ya Instalado)

- [x] 2.1 Verificar que Vitest está instalado ejecutando `bunx vitest --version` (ya instalado localmente)
- [x] 2.2 Verificar que @vitest/coverage-v8 está instalado
- [x] 2.3 Crear archivo vitest.config.ts en raíz del proyecto si no existe
- [x] 2.4 Configurar mode: 'run' y 'watch' para desarrollo
- [x] 2.5 Configurar include/exclude para archivos de test
- [x] 2.6 Configurar coverage provider: v8
- [x] 2.7 Actualizar scripts en package.json: "test": "vitest", "test:run": "vitest run", "test:coverage": "vitest run --coverage" (si no existen)

## 3. Instalación de Dependencias (con Bun)

- [x] 3.1 Instalar Biome como dependencia de desarrollo (`bun add -d @biomejs/biome`)
- [x] 3.2 Instalar commitlint y conventional-changelog-conventionalcommits (`bun add -d @commitlint/cli @commitlint/config-conventional`)
- [x] 3.3 Instalar lefthook como dependencia de desarrollo (`bun add -d lefthook`)
- [x] 3.4 Verificar instalaciones ejecutando `bunx biome --version`, `bunx commitlint --version`, `bunx lefthook --version`

## 4. Configuración de Biome

- [x] 4.1 Crear archivo biome.json en raíz del proyecto con configuración básica
- [x] 4.2 Configurar reglas de linting para TypeScript y JavaScript
- [x] 4.3 Configurar reglas de formatting (lineWidth, indentStyle, trailingComma)
- [x] 4.4 Configurar include/exclude para archivos y carpetas a procesar
- [x] 4.5 Agregar scripts bun en package.json: "lint": "biome lint .", "format": "biome format --write .", "format:check": "biome format ."
- [x] 4.6 Crear configuración de VS Code en .vscode/settings.json para Biome

## 5. Configuración de Commitlint

- [x] 5.1 Crear archivo commitlint.config.js o commitlint.config.ts en raíz del proyecto
- [x] 5.2 Configurar extends con "conventionalcommits"
- [x] 5.3 Configurar tipos de commit permitidos: build, chore, ci, docs, feat, fix, perf, refactor, revert, style, test
- [x] 5.4 Configurar validación de longitud del header (max 72 caracteres)
- [x] 5.5 Probar con commit de prueba: `echo "feat: test" | bunx commitlint`

## 6. Configuración de Lefthook

- [x] 6.1 Crear archivo lefthook.yml en raíz del proyecto
- [x] 6.2 Configurar pre-commit hook: ejecutar Biome lint
- [x] 6.3 Configurar commit-msg hook: ejecutar commitlint
- [x] 6.4 Ejecutar `bunx lefthook install` para instalar Git hooks
- [x] 6.5 Probar pre-commit hook con un archivo que tenga errores de lint
- [x] 6.6 Probar commit-msg hook con mensaje inválido

## 7. Configuración de GitHub Actions (CI - Requiere Instalación de Bun)

- [x] 7.1 Crear directorio .github/workflows/
- [x] 7.2 Crear archivo ci.yml con workflow de CI usando Bun
- [x] 7.3 Configurar triggers: push a main/master y pull requests
- [x] 7.4 **CI Only** - Agregar step para instalar Bun en runners con `oven-sh/setup-bun@v1`
- [x] 7.5 **CI Only** - Configurar job "lint" que ejecute `bun run lint`
- [x] 7.6 **CI Only** - Configurar job "test" que ejecute `bun run test` (usando Vitest ya en node_modules)
- [x] 7.7 **CI Only** - Configurar job "test:coverage" que ejecute `bun run test:coverage`
- [x] 7.8 **CI Only** - Configurar job "build" que ejecute `bun run build`
- [x] 7.9 **CI Only** - Configurar dependency caching (Bun cache en ~/.bun/install/cache)
- [x] 7.10 Verificar workflow en GitHub Actions interface

## 8. Validación del Toolchain Completo

- [x] 8.1 Ejecutar `bun run lint` y verificar que funciona correctamente
- [x] 8.2 Ejecutar `bun run format` y verificar que formatea correctamente
- [x] 8.3 Ejecutar `bun run test` y verificar que los tests pasan
- [ ] 8.4 Intentar commit con formato válido y verificar que pasa
- [ ] 8.5 Intentar commit con formato inválido y verificar que rechaza
- [ ] 8.6 Push a branch y verificar que CI se ejecuta en GitHub
- [ ] 8.7 Verificar que todos los jobs de CI pasan (lint, test, build, coverage)

## 9. Desinstalación de Herramientas Antiguas (Opcional)

- [x] 9.1 Remover Prettier de package.json y dependencias (`bun remove prettier`)
- [x] 9.2 Remover ESLint de package.json y dependencias (`bun remove eslint`) - No estaba instalado
- [x] 9.3 Remover Jest de package.json y dependencias (`bun remove jest @types/jest ts-jest`) - No estaba instalado
- [x] 9.4 Remover Husky de package.json y dependencias (`bun remove husky`) - No estaba instalado
- [x] 9.5 Eliminar archivos de configuración antiguos (.prettierrc, .eslintrc, jest.config.js, etc.)
- [x] 9.6 Eliminar package-lock.json si aún existe
- [x] 9.7 Limpiar .git/hooks/ si contiene hooks de Husky - No había hooks de Husky
- [x] 9.8 Verificar que el toolchain sigue funcionando después de limpieza