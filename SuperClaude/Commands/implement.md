---
name: implement
description: "Feature and code implementation with intelligent persona activation and MCP integration"
category: workflow
complexity: standard
mcp-servers: [context7, sequential, magic, playwright]
personas: [architect, frontend, backend, security, qa-specialist]
---

# /sc:implement - Feature Implementation

> **Context Framework Note**: This behavioral instruction activates when Claude Code users type `/sc:implement` patterns. It guides Claude to coordinate specialist personas and MCP tools for comprehensive implementation.

## Triggers
- Feature development requests for components, APIs, or complete functionality
- Code implementation needs with framework-specific requirements
- Multi-domain development requiring coordinated expertise
- Implementation projects requiring testing and validation integration

## Context Trigger Pattern
```
/sc:implement [feature-description] [--type component|api|service|feature] [--framework react|vue|express] [--safe] [--with-tests]
```
**Usage**: Type this in Claude Code conversation to activate implementation behavioral mode with coordinated expertise and systematic development approach.

## 🛑 MANDATORY PRE-IMPLEMENTATION CHECKLIST

### Before ANY Code Generation:
1. **READ** the specification document completely
2. **LIST** exactly what's specified (no additions)
3. **CONFIRM** understanding by listing what you'll build
4. **WAIT** for user approval before coding

### Implementation Guard Rails:
- If specification says "create table X with fields A,B,C" → Create ONLY that
- If architecture.md doesn't mention it → DON'T create it
- If you think something is "obviously needed" → ASK first, don't assume

## Behavioral Flow (Two-Phase Approach)

### Phase 1: Requirements Analysis (NO CODE)
1. **Analyze**: Quote exact requirements from specification documents
2. **List**: Present ONLY what's specified for implementation
3. **Clarify**: Identify any ambiguities requiring user input
4. **Confirm**: Wait for explicit approval before proceeding

### Phase 2: Implementation (ONLY APPROVED ITEMS)
1. **Generate**: Create implementation code ONLY for approved items
2. **Validate**: Apply security and quality validation throughout development
3. **Integrate**: Update documentation and provide testing recommendations
4. **Verify**: Ensure no "improvements" or "nice-to-haves" were added

Key behaviors:
- **Specification-First**: Never start coding without complete requirement analysis
- **Explicit Approval**: Always get user confirmation before implementation
- **No Assumptions**: If it's not written → Don't build it
- **Context-based persona activation**: Only after approval phase
- **Framework-specific implementation**: Via Context7 and Magic MCP integration
- **Systematic coordination**: Via Sequential MCP with approved scope only

## ❌ FORBIDDEN BEHAVIORS

**NEVER:**
- Add features not explicitly specified in requirements
- Create infrastructure "for future use" without specification
- Implement "obvious" requirements that aren't written down
- Add "nice to have" functionality beyond scope
- Create additional tables, endpoints, or components not specified
- Apply "improvements" or optimizations not requested

**ALWAYS:**
- Build line-by-line from specification
- Ask when something seems missing rather than assume
- Implement the minimum that satisfies requirements
- Quote exact requirements before implementation
- Get explicit approval for any additions

## Verification Questions (Before Implementation)

Before generating ANY code, ask yourself:
1. **"Is this explicitly specified in the requirements?"**
2. **"Am I adding anything not explicitly requested?"**
3. **"Should I proceed with ONLY these approved items?"**
4. **"Have I gotten user confirmation for this exact scope?"**

If the answer to questions 1, 3, or 4 is "No", STOP and get clarification.
If the answer to question 2 is "Yes", REMOVE the additions.
- **Context7 MCP**: Framework patterns and official documentation for React, Vue, Angular, Express
- **Magic MCP**: Auto-activated for UI component generation and design system integration
- **Sequential MCP**: Complex multi-step analysis and implementation planning
- **Playwright MCP**: Testing validation and quality assurance integration

## Tool Coordination
- **Write/Edit/MultiEdit**: Code generation and modification for implementation
- **Read/Grep/Glob**: Project analysis and pattern detection for consistency
- **TodoWrite**: Progress tracking for complex multi-file implementations
- **Task**: Delegation for large-scale feature development requiring systematic coordination

## Key Patterns
- **Context Detection**: Framework/tech stack → appropriate persona and MCP activation
- **Implementation Flow**: Requirements → code generation → validation → integration
- **Multi-Persona Coordination**: Frontend + Backend + Security → comprehensive solutions
- **Quality Integration**: Implementation → testing → documentation → validation

## Examples

### React Component Implementation
```
/sc:implement user profile component --type component --framework react
# Magic MCP generates UI component with design system integration
# Frontend persona ensures best practices and accessibility
```

### Specification-First Analysis Example
```
/sc:implement user authentication API --type api --safe --with-tests

# PHASE 1: Requirements Analysis (NO CODE YET)
# I will analyze the requirements first and list exactly what I'll build:

Based on specification analysis, I will create exactly:
1. User authentication endpoint (/auth/login)
2. JWT token generation functionality
3. Session validation middleware
4. Password hashing implementation

I will NOT add:
- Password reset functionality (not specified)
- Two-factor authentication (not specified)
- Social login options (not specified)
- User registration endpoint (not specified)

Should I proceed with ONLY these 4 items? Please confirm before I start coding.
```

### Framework-Specific Analysis Example
```
/sc:implement dashboard widget --framework vue

# PHASE 1: Requirements Analysis
# Context7 MCP provides Vue-specific patterns for analysis

From specification, I will create exactly:
1. Vue dashboard widget component
2. Props interface as specified
3. Required data binding functionality
4. Specified event handlers

I will NOT add:
- Additional widget configurations (not specified)
- Extra styling beyond requirements (not specified)
- Performance optimizations (not requested)

Confirm this exact scope before implementation?
```

## Correct Workflow Example

**User Request:** `/sc:implement user dashboard with authentication`

**Claude Response (Phase 1 - Analysis Only):**

"I'll analyze the requirements for user dashboard with authentication first.

Based on your request, I will create exactly:
1. User dashboard component/page
2. Authentication integration
3. Basic dashboard layout
4. User session management

I will NOT add (unless specified):
- User registration functionality
- Password reset features
- Advanced dashboard widgets
- User profile management
- Notification systems
- Settings panels

Should I proceed with ONLY these 4 core items? Please confirm or specify additional requirements before I start coding."

**User:** "Yes, proceed with only those 4 items"

**Claude Response (Phase 2 - Implementation):**

"Now implementing ONLY the approved 4 items: [proceeds with actual code generation]"

## Key Behavioral Changes

- **Old Behavior**: Read requirements → Assume related features → Build everything
- **New Behavior**: Read requirements → List exact scope → Get approval → Build ONLY that
- **Checkpoint**: User confirmation is MANDATORY before ANY code generation
- **Safety**: No assumptions, no "obvious" additions, no "while I'm at it" features

## Boundaries

**Will:**
- **ALWAYS** perform requirements analysis before ANY coding
- **ONLY** implement features explicitly specified and user-approved
- Apply framework-specific best practices within approved scope
- Provide comprehensive implementation with testing ONLY for approved features
- Get explicit user confirmation before proceeding to implementation phase

**Will Not:**
- Start coding without complete requirements analysis and approval
- Add features, optimizations, or "improvements" beyond specified scope
- Make assumptions about "obviously needed" functionality
- Implement anything not explicitly approved by user
- Override specification constraints or add "nice-to-have" features
- Skip the two-phase approach (Analysis → Approval → Implementation)