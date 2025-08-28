---
name: save
description: "Session lifecycle management with Serena MCP integration for session context persistence"
category: session
complexity: standard
mcp-servers: [serena]
personas: []
---

# /sc:save - Session Context Persistence

## Triggers
- Session completion and project context persistence needs
- Cross-session memory management and checkpoint creation requests
- Project understanding preservation and discovery archival scenarios
- Session lifecycle management and progress tracking requirements

## Usage
```
/sc:save [context_name] [--type session|learnings|context|all] [--summarize] [--checkpoint] [--merge]
```

## Behavioral Flow
1. **Analyze**: Examine session progress and identify discoveries worth preserving
2. **Persist**: Save session context and learnings using Serena MCP memory management
3. **Checkpoint**: Create recovery points for complex sessions and progress tracking
4. **Validate**: Ensure session data integrity and cross-session compatibility
5. **Prepare**: Ready session context for seamless continuation in future sessions

Key behaviors:
- Serena MCP integration for memory management and cross-session persistence
- Automatic checkpoint creation based on session progress and critical tasks
- Session context preservation with comprehensive discovery and pattern archival
- Cross-session learning with accumulated project insights and technical decisions

## MCP Integration
- **Serena MCP**: Mandatory integration for session management, memory operations, and cross-session persistence
- **Memory Operations**: Session context storage, checkpoint creation, and discovery archival
- **Performance Critical**: <200ms for memory operations, <1s for checkpoint creation

## Tool Coordination
- **write_memory/read_memory**: Core session context persistence and retrieval
- **think_about_collected_information**: Session analysis and discovery identification
- **summarize_changes**: Session summary generation and progress documentation
- **TodoRead**: Task completion tracking for automatic checkpoint triggers

## Key Patterns
- **Session Preservation**: Discovery analysis → memory persistence → checkpoint creation
- **Cross-Session Learning**: Context accumulation → pattern archival → enhanced project understanding
- **Progress Tracking**: Task completion → automatic checkpoints → session continuity
- **Recovery Planning**: State preservation → checkpoint validation → restoration readiness

## Examples

### Basic Session Save
```
/sc:save
# Saves current session discoveries and context to Serena MCP
# Automatically creates checkpoint if session exceeds 30 minutes
```

### Comprehensive Session Checkpoint
```
/sc:save --type all --checkpoint
# Complete session preservation with recovery checkpoint
# Includes all learnings, context, and progress for session restoration
```

### Session Summary Generation
```
/sc:save --summarize
# Creates session summary with discovery documentation
# Updates cross-session learning patterns and project insights
```

### Discovery-Only Persistence
```
/sc:save --type learnings
# Saves only new patterns and insights discovered during session
# Updates project understanding without full session preservation
```

## Boundaries

**Will:**
- Save session context using Serena MCP integration for cross-session persistence
- Create automatic checkpoints based on session progress and task completion
- Preserve discoveries and patterns for enhanced project understanding

**Will Not:**
- Operate without proper Serena MCP integration and memory access
- Save session data without validation and integrity verification
- Override existing session context without proper checkpoint preservation

## Memory Collision Prevention

### Issue Resolution
Previous behavior created new memory files for duplicate context names instead of updating existing ones. This caused memory fragmentation and loss of session continuity.

### Enhanced Behavior (--merge flag)
When `--merge` flag is used or same context name is detected:

#### Memory Collision Detection
```
1. Check existing memories with list_memories()
2. If context_name already exists, prompt for merge strategy:
   - "merge": Combine new content with existing memory
   - "overwrite": Replace existing memory completely  
   - "version": Create versioned memory (context_name_v2, context_name_v3)
   - "cancel": Abort save operation
```

#### Merge Strategy Implementation
```markdown
## Merge Process
1. **Content Analysis**: Compare new content with existing memory
2. **Conflict Detection**: Identify overlapping or contradictory information
3. **Intelligent Merge**: 
   - Append new discoveries to existing context
   - Update outdated information
   - Preserve historical context when relevant
4. **Validation**: Ensure merged content maintains coherence
```

#### Default Behavior (without --merge)
- **First Save**: `/sc:save "project context"` → Creates new memory
- **Subsequent Saves**: `/sc:save "project context"` → Automatically prompts for merge strategy
- **Auto-merge**: If content is purely additive (no conflicts), merge automatically
- **Conflict Prompt**: If conflicts detected, require user choice

### Enhanced Examples

#### Memory Update with Merge
```
/sc:save "enhance redesign" --merge
# Checks for existing "enhance redesign" memory
# Merges new discoveries with existing context
# Maintains session continuity across work phases
```

#### Versioned Memory Management
```
/sc:save "project analysis" --type learnings
# First save: creates "project analysis" memory
# Second save: automatically merges new learnings
# Conflict resolution: prompts for strategy choice
```

#### Structured Session Management
```
/sc:save "flutter app development" --checkpoint --merge
# Creates/updates comprehensive session context
# Includes progress tracking and discovery accumulation
# Enables seamless session restoration
```

### Implementation Rules

#### Memory Naming Convention
- **Context Names**: Use descriptive, consistent naming across sessions
- **Avoid Duplicates**: System warns when similar context names exist
- **Merge Validation**: Ensure merged content maintains logical flow
- **Version Control**: Track content changes for rollback capability

#### Conflict Resolution Priority
1. **User Explicit Choice**: Always honor user-specified merge strategy
2. **Additive Content**: Auto-merge when new content complements existing
3. **Contradictory Content**: Always prompt for resolution strategy
4. **Session Continuity**: Prioritize maintaining coherent project context

#### Quality Assurance
- **Content Validation**: Verify merged memories maintain coherence
- **Cross-Reference Check**: Ensure consistency with other project memories
- **Size Management**: Prevent memory bloat through intelligent summarization
- **Recovery Points**: Maintain backup of previous memory states for rollback