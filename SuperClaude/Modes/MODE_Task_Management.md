# Task Management Mode

**Purpose**: Hierarchical task organization with persistent memory for complex multi-step operations

## Activation Triggers
- Operations with >3 steps requiring coordination
- Multiple file/directory scope (>2 directories OR >3 files)
- Complex dependencies requiring phases
- Manual flags: `--task-manage`, `--delegate`
- Quality improvement requests: polish, refine, enhance
- Prompt generation requests for reusable templates

## Task Hierarchy with Memory

📋 **Plan** → write_memory("plan", goal_statement)
→ 🎯 **Phase** → write_memory("phase_X", milestone)
  → 📦 **Task** → write_memory("task_X.Y", deliverable)
    → ✓ **Todo** → TodoWrite + write_memory("todo_X.Y.Z", status)

## Memory Operations

### Session Start
```
1. list_memories() → Show existing task state
2. read_memory("current_plan") → Resume context
3. think_about_collected_information() → Understand where we left off
```

### During Execution
```
1. write_memory("task_2.1", "completed: auth middleware")
2. think_about_task_adherence() → Verify on track
3. Update TodoWrite status in parallel
4. write_memory("checkpoint", current_state) every 30min
```

### Session End
```
1. think_about_whether_you_are_done() → Assess completion
2. write_memory("session_summary", outcomes)
3. delete_memory() for completed temporary items
4. Generate prompt template if --task-manage flag active
```

## Prompt Template Generation (--task-manage Enhancement)

When `--task-manage` flag is used, automatically generate reusable prompt templates:

### Template Location
- **File Path**: `docs/todos/{task-name}-prompt-template.md`
- **Max Length**: 300 lines
- **Format**: Structured markdown following best practice prompt engineering

### Template Structure
```markdown
# {Task Name} - Implementation Template

## Technical Requirements
- [Extracted from discussion and analysis]
- [Architecture constraints and dependencies]
- [Performance and quality requirements]

## Implementation Steps
1. [Phase 1: Analysis and Planning]
   - Specific deliverables and validation criteria
2. [Phase 2: Core Implementation]
   - Code generation patterns and validation
3. [Phase 3: Testing and Documentation]
   - Test coverage requirements and docs

## Validation Criteria
- [ ] Technical requirements met and verified
- [ ] Code quality standards maintained
- [ ] Testing coverage > 80%
- [ ] Documentation updated
- [ ] Performance benchmarks satisfied

## Context Variables
- Project Type: {detected from analysis}
- Tech Stack: {framework/libraries identified}
- Architecture Pattern: {architectural decisions}
- Key Dependencies: {critical imports/packages}

## Reuse Instructions
This template can be reused for similar {task-type} implementations by:
1. Updating context variables for new project
2. Modifying technical requirements as needed
3. Adapting validation criteria to project standards
```

### Auto-Generation Triggers
- Task completion with `--task-manage` flag
- Discussion sessions that result in structured implementation plans
- Multi-phase development workflows
- Feature development with reusable patterns

## Execution Pattern

1. **Load**: list_memories() → read_memory() → Resume state
2. **Plan**: Create hierarchy → write_memory() for each level  
3. **Track**: TodoWrite + memory updates in parallel
4. **Execute**: Update memories as tasks complete
5. **Checkpoint**: Periodic write_memory() for state preservation
6. **Complete**: Final memory update with outcomes

## Tool Selection

| Task Type | Primary Tool | Memory Key |
|-----------|-------------|------------|
| Analysis | Sequential MCP | "analysis_results" |
| Implementation | MultiEdit/Morphllm | "code_changes" |
| UI Components | Magic MCP | "ui_components" |
| Testing | Playwright MCP | "test_results" |
| Documentation | Context7 MCP | "doc_patterns" |

## Memory Schema

```
plan_[timestamp]: Overall goal statement
phase_[1-5]: Major milestone descriptions
task_[phase].[number]: Specific deliverable status
todo_[task].[number]: Atomic action completion
checkpoint_[timestamp]: Current state snapshot
blockers: Active impediments requiring attention
decisions: Key architectural/design choices made
```

## Examples

### Session 1: Start Authentication Task
```
list_memories() → Empty
write_memory("plan_auth", "Implement JWT authentication system")
write_memory("phase_1", "Analysis - security requirements review")
write_memory("task_1.1", "pending: Review existing auth patterns")
TodoWrite: Create 5 specific todos
Execute task 1.1 → write_memory("task_1.1", "completed: Found 3 patterns")
```

### Session 2: Resume After Interruption
```
list_memories() → Shows plan_auth, phase_1, task_1.1
read_memory("plan_auth") → "Implement JWT authentication system"
think_about_collected_information() → "Analysis complete, start implementation"
think_about_task_adherence() → "On track, moving to phase 2"
write_memory("phase_2", "Implementation - middleware and endpoints")
Continue with implementation tasks...
```

### Session 3: Completion Check
```
think_about_whether_you_are_done() → "Testing phase remains incomplete"
Complete remaining testing tasks
write_memory("outcome_auth", "Successfully implemented with 95% test coverage")
delete_memory("checkpoint_*") → Clean temporary states
write_memory("session_summary", "Auth system complete and validated")
```