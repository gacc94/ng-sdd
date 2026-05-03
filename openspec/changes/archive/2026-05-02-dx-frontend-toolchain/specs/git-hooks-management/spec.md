## ADDED Requirements

### Requirement: Lefthook installation and configuration
The system MUST provide lefthook installed as a development dependency with proper configuration.

#### Scenario: Lefthook CLI available
- **WHEN** developer runs `bunx lefthook --version`
- **THEN** system displays the installed lefthook version

#### Scenario: Configuration file exists
- **WHEN** developer checks for lefthook.yml in project root
- **THEN** the configuration file MUST exist with valid YAML structure

### Requirement: Git hooks setup with parallel execution
The system MUST configure Git hooks using lefthook with parallel execution for pre-commit checks.

#### Scenario: Pre-commit configured with parallel commands
- **WHEN** developer runs `git commit`
- **THEN** lefthook MUST execute pre-commit commands in parallel

#### Scenario: Biome check with stage_fixed
- **WHEN** pre-commit hook executes
- **THEN** Biome check MUST run on staged files with `--write` flag and auto-re-stage fixed files

#### Scenario: Commit-msg hook configured
- **WHEN** developer attempts to commit with message
- **THEN** lefthook MUST execute commit-msg hook to validate commit message

### Requirement: Hook configuration with glob and stage_fixed
The system MUST use lefthook's advanced features for efficient hook execution.

#### Scenario: Glob pattern filters files
- **WHEN** pre-commit executes
- **THEN** only files matching `*.{js,ts,jsx,tsx,json}` MUST be processed by Biome

#### Scenario: stage_fixed automatically re-stages
- **WHEN** Biome fixes files during pre-commit
- **THEN** fixed files MUST be automatically re-staged without manual intervention

#### Scenario: Invalid commit message blocked
- **WHEN** commit-msg hook detects invalid format
- **THEN** commit MUST be blocked with clear error message

### Requirement: Installation instructions
The system MUST provide clear instructions for installing Git hooks in the development environment.

#### Scenario: Hooks install command available
- **WHEN** developer runs `bunx lefthook install`
- **THEN** Git hooks MUST be installed in .git/hooks directory