---
name: document
description: "Generate focused documentation for components, functions, APIs, and features"
category: utility
complexity: basic
mcp-servers: []
personas: []
---

# /sc:document - Focused Documentation Generation

## Triggers
- Documentation requests for specific components, functions, or features
- API documentation and reference material generation needs
- Code comment and inline documentation requirements
- User guide and technical documentation creation requests
- File organization and indexing needs (--indexer flag)
- Changelog management and version documentation (--changelog flag)

## Usage
```
/sc:document [target] [--type inline|external|api|guide] [--style brief|detailed] [--indexer] [--changelog]
```

## Behavioral Flow
1. **Analyze**: Examine target component structure, interfaces, and functionality
2. **Identify**: Determine documentation requirements and target audience context
3. **Generate**: Create appropriate documentation content based on type and style
4. **Format**: Apply consistent structure and organizational patterns
5. **Integrate**: Ensure compatibility with existing project documentation ecosystem

Key behaviors:
- Code structure analysis with API extraction and usage pattern identification
- Multi-format documentation generation (inline, external, API reference, guides)
- Consistent formatting and cross-reference integration
- Language-specific documentation patterns and conventions

## Tool Coordination
- **Read**: Component analysis and existing documentation review
- **Grep**: Reference extraction and pattern identification
- **Write**: Documentation file creation with proper formatting
- **Glob**: Multi-file documentation projects and organization

## Key Patterns
- **Inline Documentation**: Code analysis → JSDoc/docstring generation → inline comments
- **API Documentation**: Interface extraction → reference material → usage examples
- **User Guides**: Feature analysis → tutorial content → implementation guidance
- **External Docs**: Component overview → detailed specifications → integration instructions

## Examples

### Inline Code Documentation
```
/sc:document src/auth/login.js --type inline
# Generates JSDoc comments with parameter and return descriptions
# Adds comprehensive inline documentation for functions and classes
```

### API Reference Generation
```
/sc:document src/api --type api --style detailed
# Creates comprehensive API documentation with endpoints and schemas
# Generates usage examples and integration guidelines
```

### User Guide Creation
```
/sc:document payment-module --type guide --style brief
# Creates user-focused documentation with practical examples
# Focuses on implementation patterns and common use cases
```

### Component Documentation
```
/sc:document components/ --type external
# Generates external documentation files for component library
# Includes props, usage examples, and integration patterns
```

## Boundaries

**Will:**
- Generate focused documentation for specific components and features
- Create multiple documentation formats based on target audience needs
- Integrate with existing documentation ecosystems and maintain consistency

**Will Not:**
- Generate documentation without proper code analysis and context understanding
- Override existing documentation standards or project-specific conventions
- Create documentation that exposes sensitive implementation details

## Enhanced Functionality

### File Indexing (--indexer flag)
When used with `--indexer`, generates context-aware file indices:

#### Index File Location Pattern
```
/sc:document shared --indexer → creates: shared/index-file.md
/sc:document lib/features/auth --indexer → creates: lib/features/auth/index-file.md  
/sc:document . --indexer → creates: index-file.md (project root)
```

#### Index File Structure
```markdown
# {Context} - File Index

Generated: {timestamp}
Context: {path}
Files: {count}

| File | Description | Type | Link |
|------|-------------|------|------|
| file.dart | One-line description | Dart | [📁](./file.dart) |
| config.json | Configuration file | JSON | [📁](./config.json) |

## Directory Structure
### folder/
Purpose and contents overview

**Files:**
- `file1.ext` - Description
- `file2.ext` - Description
```

#### Indexer Features
- **Comprehensive Scanning**: All files and subdirectories in specified context
- **Smart Descriptions**: Auto-generated based on file patterns, names, and content analysis
- **Working Links**: Relative links that work from index file location
- **Type Detection**: Automatic categorization by extension and content
- **Hierarchy Preservation**: Maintains folder structure in documentation

### Changelog Management (--changelog flag)
When used with `--changelog`, manages CHANGELOG.md in project root:

#### Changelog Format (Keep a Changelog Standard)
```markdown
# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

## [1.0.1] - 2024-01-15
### Added
- New feature descriptions

### Changed  
- Modified functionality details

### Fixed
- Bug fixes and corrections

### Removed
- Deprecated feature removals
```

#### Changelog Features
- **Version Detection**: Auto-detect from package.json, pubspec.yaml, or manual input
- **Structured Entries**: Categorized changes (Added, Changed, Fixed, Removed)
- **Date Management**: Automatic date formatting and version timestamps
- **Upsert Logic**: Updates existing entries or creates new sections as needed

## Extended Examples

### File Indexing Examples
```
/sc:document src/components --indexer
# Creates: src/components/index-file.md
# Scans all .jsx/.tsx files with component descriptions

/sc:document docs --indexer
# Creates: docs/index-file.md  
# Organizes all documentation files with descriptions
```

### Changelog Examples
```
/sc:document . --changelog
# Updates CHANGELOG.md in project root
# Prompts for version and change descriptions

/sc:document --changelog --version 1.2.0 --changes "Added Flutter support, Fixed memory leaks"
# Direct changelog entry with specified version and changes
```

### Combined Operations
```
/sc:document lib --indexer --type api
# Creates both:
# - lib/index-file.md (file index)
# - docs/projects/lib-api-documentation.md (API docs)

/sc:document . --changelog --indexer --type architecture
# Creates:
# - index-file.md (project file index)
# - CHANGELOG.md update
# - docs/projects/architecture.md
```

## File Organization Rules

### Generated File Locations
- **Index Files**: `{context}/index-file.md` (relative to specified context)
- **Documentation**: `docs/projects/{target}-{type}.md` for external docs  
- **Changelog**: `CHANGELOG.md` in project root
- **API Docs**: `docs/api/` directory for comprehensive API documentation

### Integration with Task Management
- **TodoWrite**: Automatically created for complex documentation projects
- **Memory Management**: Store documentation patterns for reuse
- **Progress Tracking**: Monitor completion of multi-file documentation tasks