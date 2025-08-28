# 🛑 MANDATORY BEFORE ANY IMPLEMENTATION

## Pre-Implementation Checklist
Before creating ANY code:
1. READ the specification document completely
2. LIST exactly what's specified (no additions)
3. CONFIRM understanding by listing what you'll build
4. WAIT for user approval before coding

## Implementation Guard Rails
- If specification says "create table X with fields A,B,C" → Create ONLY that
- If architecture.md doesn't mention it → DON'T create it
- If you think something is "obviously needed" → ASK first, don't assume

# Required Workflow for Features

## Mandatory Two-Phase Implementation

### Phase 1: Requirements Analysis (NO CODE)
- Read specification
- List exact deliverables
- Present findings
- Get approval

### Phase 2: Implementation (ONLY APPROVED ITEMS)
- Build approved list
- No additions
- No optimizations
- No extras

# ❌ FORBIDDEN BEHAVIORS

**NEVER:**
- Add tables not in architecture.md
- Create features "for completeness"
- Implement "obvious" requirements not written
- Add "nice to have" functionality
- Create infrastructure "for future use"

**ALWAYS:**
- Build line-by-line from specification
- Ask when something seems missing
- Implement the minimum that satisfies requirements

# Strict Implementation Rules

## 1. Specification Analysis First
- ALWAYS analyze requirements before coding
- ALWAYS list what you'll build and get confirmation
- NEVER start coding without approval

## 2. No Assumptions
- If it's not written → Don't build it
- If it seems missing → Ask about it
- If it could be useful → Still don't build it

## 3. Verification Questions
Before implementing, ask:
- "Is this explicitly specified?"
- "Am I adding anything not requested?"
- "Should I proceed with ONLY these items?"

# Example Correct Workflow

User: "Implement Story 1.2 authentication"

Claude: "I'll analyze Story 1.2 requirements from architecture.md first.

Based on architecture.md, Story 1.2 requires exactly:
1. User authentication with email/password
2. JWT token generation
3. Session management
4. Role-based access control

I will NOT add:
- Password reset (not specified)
- Two-factor auth (not specified)
- Social login (not specified)

Should I proceed with ONLY these 4 items?"

User: "Yes"

Claude: [Now implements ONLY those 4 items]

# The Key Principle

**Current behavior**: Read requirements → Assume related features → Build everything
**Desired behavior**: Read requirements → List exact scope → Confirm → Build ONLY that

The solution is to force a confirmation checkpoint before any implementation. This breaks the pattern of assumption-based development.
