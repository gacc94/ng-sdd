## ADDED Requirements

### Requirement: Vitest verification (already installed locally)
The system MUST verify that Vitest is available as a development dependency (already installed in node_modules).

#### Scenario: Vitest CLI available locally
- **WHEN** developer runs `bunx vitest --version`
- **THEN** system displays the installed Vitest version

#### Scenario: Vitest available in node_modules
- **WHEN** developer checks node_modules/
- **THEN** vitest package MUST be present (already installed)

#### Scenario: Configuration file exists
- **WHEN** developer checks for vitest.config.ts in project root
- **THEN** the configuration file MUST exist with valid TypeScript configuration (create if missing)

### Requirement: Vitest configuration
The system MUST provide a vitest.config.ts that configures the test runner appropriately for the project.

#### Scenario: Test mode configured
- **WHEN** Vitest runs in run mode
- **THEN** configuration MUST define mode: 'run' for CI execution

#### Scenario: Watch mode configured
- **WHEN** Vitest runs in development
- **THEN** configuration MUST define mode: 'watch' for auto-reload

#### Scenario: Include patterns configured
- **WHEN** Vitest discovers tests
- **THEN** configuration MUST specify include patterns for test files (*.spec.ts, *.test.ts)

#### Scenario: Exclude patterns configured
- **WHEN** Vitest discovers tests
- **THEN** configuration MUST specify exclude patterns to skip non-test files

### Requirement: Coverage configuration
The system MUST provide coverage configuration using v8 provider.

#### Scenario: Coverage provider configured
- **WHEN** coverage runs
- **THEN** Vitest MUST use v8 as coverage provider

#### Scenario: Coverage reports generated
- **WHEN** coverage command executes
- **THEN** coverage report MUST be generated in HTML format under coverage/ directory

### Requirement: npm scripts for testing
The system MUST provide npm scripts for running tests with Bun.

#### Scenario: Test script defined
- **WHEN** developer runs `bun run test`
- **THEN** Vitest MUST start in watch mode for development

#### Scenario: Test run script defined
- **WHEN** developer runs `bun run test:run`
- **THEN** Vitest MUST execute tests once and exit

#### Scenario: Coverage script defined
- **WHEN** developer runs `bun run test:coverage`
- **THEN** Vitest MUST run tests with coverage and generate report

### Requirement: IDE integration
The system MUST provide configuration that integrates with popular IDEs for running tests.

#### Scenario: VS Code Vitest extension works
- **WHEN** developer opens project in VS Code with Vitest extension
- **THEN** test files MUST show run/debug buttons