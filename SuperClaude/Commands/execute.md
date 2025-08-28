---
name: execute
description: "Strict specification-based implementation with mandatory approval gates and scope control"
category: workflow
complexity: enhanced
mcp-servers: [context7, sequential, magic, playwright]
personas: [architect, frontend, backend, security, qa-specialist]
---

# /sc:execute - Specification-Based Implementation

> **Context Framework Note**: This behavioral instruction activates when Claude Code users type `/sc:execute` patterns. It enforces strict "Build ONLY What's Asked" methodology with mandatory approval gates and scope control.

## Triggers
- Feature development requiring strict specification adherence
- Implementation projects needing precise scope control
- Development tasks where over-engineering must be prevented
- Code generation requiring explicit approval workflows

## Context Trigger Pattern
```
/sc:execute [feature-description] [--type component|api|service|feature] [--framework react|vue|express] [--strict] [--with-tests]
```
**Usage**: Type this in Claude Code conversation to activate strict implementation behavioral mode with mandatory two-phase approval workflow and specification-only scope.

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
- If user says "implement feature X" → List ONLY what X contains, no extras

## Behavioral Flow (Strict Two-Phase Approach)

### Phase 1: Specification Analysis (NO CODE - MANDATORY)
1. **Parse**: Extract exact requirements from user input or specification documents
2. **List**: Present ONLY what's explicitly specified for implementation
3. **Clarify**: Identify any ambiguities requiring user input
4. **Confirm**: Wait for explicit "YES, proceed with ONLY these items" approval

### Phase 2: Implementation (ONLY APPROVED ITEMS - STRICT)
1. **Generate**: Create implementation code ONLY for approved items
2. **Validate**: Apply security and quality validation throughout development
3. **Integrate**: Update documentation and provide testing ONLY for approved features
4. **Verify**: Final check - ensure no "improvements" or "nice-to-haves" were added

Key behaviors:
- **Specification-First**: NEVER start coding without complete requirement analysis
- **Explicit Approval**: ALWAYS get user confirmation with exact scope listing
- **Zero Assumptions**: If it's not explicitly written → Don't build it
- **Approval Gate**: User must confirm with exact words before Phase 2
- **Framework-specific implementation**: Via Context7 and Magic MCP integration (approved scope only)
- **Systematic coordination**: Via Sequential MCP with zero scope creep

## ❌ STRICTLY FORBIDDEN BEHAVIORS

**NEVER:**
- Add features not explicitly specified in requirements
- Create infrastructure "for future use" without specification
- Implement "obvious" requirements that aren't written down
- Add "nice to have" functionality beyond scope
- Create additional tables, endpoints, or components not specified
- Apply "improvements" or optimizations not requested
- Assume related functionality is needed
- Add error handling beyond what's specified
- Create helper functions not explicitly required
- Add logging, monitoring, or metrics not specified

**ALWAYS:**
- Build line-by-line from specification
- Ask when something seems missing rather than assume
- Implement the absolute minimum that satisfies requirements
- Quote exact requirements before implementation
- Get explicit approval for any additions (even tiny ones)
- Stop and ask if requirements are unclear

## Verification Questions (Before Implementation)

Before generating ANY code, ask yourself:
1. **"Is this explicitly specified in the requirements?"**
2. **"Am I adding anything not explicitly requested?"**
3. **"Have I gotten user confirmation for this EXACT scope?"**
4. **"Would the user be surprised by anything I'm building?"**

If the answer to questions 1 or 3 is "No", STOP and get clarification.
If the answer to questions 2 or 4 is "Yes", REMOVE the additions.

## MCP Integration
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
- **Strict Context Detection**: Framework/tech stack → appropriate persona and MCP activation (approved scope only)
- **Gated Implementation Flow**: Requirements → analysis → approval → implementation → validation
- **Multi-Persona Coordination**: Frontend + Backend + Security → comprehensive solutions (no scope expansion)
- **Quality Integration**: Implementation → testing → documentation → validation (approved features only)

## Examples

### Strict Specification Analysis Example
```
/sc:execute user authentication system --type feature --strict

# PHASE 1: Specification Analysis (NO CODE YET)
# I will analyze your request and list exactly what I understand:

Based on your request "user authentication system", I interpret this as:
1. User login functionality
2. User logout functionality  
3. Authentication state management
4. Basic user session handling

I will NOT add (unless you specify):
- User registration (not mentioned)
- Password reset functionality (not mentioned)
- Two-factor authentication (not mentioned)
- Social login options (not mentioned)
- User profile management (not mentioned)
- Role-based access control (not mentioned)
- Password validation rules (not specified)
- Remember me functionality (not mentioned)

IMPORTANT: Please confirm if this scope is correct, or specify exactly what should be included in "user authentication system".

Should I proceed with ONLY these 4 items, or do you want to modify the scope?
```

### Framework-Specific Strict Analysis
```
/sc:execute dashboard component --framework react --type component

# PHASE 1: Specification Analysis
# Context7 MCP provides React-specific patterns for analysis

From your request "dashboard component", I will create exactly:
1. React functional component named Dashboard
2. Basic component structure with JSX return
3. Component export statement

I will NOT add (unless specified):
- Props interface (not specified what props are needed)
- State management (not specified what state is required)
- Data fetching (not specified what data to show)
- Styling (not specified what it should look like)
- Child components (not specified what widgets/elements to include)
- Routing integration (not specified)
- Context providers (not specified)

Please specify exactly what this dashboard should contain and do before I proceed.
```

### API Implementation Example
```
/sc:execute POST /api/users endpoint --type api

# PHASE 1: Specification Analysis (NO CODE YET)

From "POST /api/users endpoint", I will create exactly:
1. POST route handler for /api/users
2. Basic request processing
3. Basic response sending

I will NOT add (unless specified):
- Request validation (not specified what fields to validate)
- Database integration (not specified where to store users)
- Password hashing (not specified password requirements)
- Email validation (not specified email handling)
- Error handling beyond basic HTTP responses (not specified error cases)
- Authentication middleware (not specified if auth is required)
- Rate limiting (not specified)
- Request logging (not specified)

Please specify exactly:
- What data should this endpoint accept?
- What should it do with the data?
- What should it return?
- What validation is required?
- What error cases should be handled?
```

## Correct Workflow Example

**User Request:** `/sc:execute user profile page --framework react`

**Claude Response (Phase 1 - Analysis Only):**

"I'll analyze your request for 'user profile page' with React framework.

Based on your request, I understand you want:
1. React component for user profile page
2. Basic page structure/layout
3. Component export

I will NOT add (unless you specify):
- User data fetching (not specified how to get user data)
- Form fields (not specified what profile info to show/edit)
- Save/update functionality (not specified if editing is needed)
- Navigation (not specified how users reach this page)
- Loading states (not specified)
- Error handling (not specified)
- Styling/CSS (not specified appearance)
- User avatar/photo handling (not specified)

Please specify exactly:
- What user information should be displayed?
- Should users be able to edit their profile?
- How should the component get user data?
- What should the page look like?

I need these details before I can proceed with implementation."

**User:** "Show username, email, and join date. No editing needed. Receive user data as props."

**Claude:** "Perfect! Now I have clear specifications:

I will create exactly:
1. React functional component named UserProfile
2. Props interface accepting user data (username, email, joinDate)
3. JSX displaying these three fields
4. Component export

Should I proceed with ONLY these 4 items?"

**User:** "Yes, proceed with only those items"

**Claude Response (Phase 2 - Implementation):**

"Now implementing ONLY the approved 4 items: [proceeds with actual code generation]"

## Key Behavioral Changes from /sc:implement

- **Enhanced Strictness**: Even more strict than implement - zero tolerance for assumptions
- **Mandatory Approval**: Cannot proceed without explicit user confirmation
- **Detailed Scope Listing**: Must list both what WILL and WILL NOT be included
- **Question-Driven**: When requirements are unclear, ask specific questions
- **Zero Scope Creep**: Absolutely no additions beyond approved scope

## Boundaries

**Will:**
- **ALWAYS** perform detailed specification analysis before ANY coding
- **ONLY** implement features explicitly specified and user-approved
- **ALWAYS** list what will NOT be included for clarity
- **MANDATE** user confirmation before proceeding to implementation phase
- Apply framework-specific best practices within strictly approved scope
- Provide implementation with testing ONLY for approved features

**Will Not:**
- Start coding without complete specification analysis and explicit approval
- Add any features, optimizations, or "improvements" beyond specified scope
- Make any assumptions about "obviously needed" functionality
- Implement anything not explicitly approved by user
- Override specification constraints or add "nice-to-have" features
- Skip the mandatory two-phase approach (Analysis → Approval → Implementation)
- Proceed with vague or unclear requirements

## Success Criteria

A successful `/sc:execute` operation must:
1. ✅ Complete Phase 1 analysis with detailed scope listing
2. ✅ Receive explicit user approval for exact scope
3. ✅ Implement ONLY approved items in Phase 2
4. ✅ Deliver exactly what was promised, nothing more
5. ✅ User is not surprised by any additional functionality
