# /sc:execute Command Documentation

## 🎯 Purpose

The `/sc:execute` command is a strict implementation of the "Build ONLY What's Asked" methodology. It provides enhanced specification-based implementation with mandatory approval gates and zero tolerance for scope creep.

## 🔄 Difference from /sc:implement

| Feature | /sc:implement | /sc:execute |
|---------|---------------|-------------|
| **Scope Control** | Standard | **Ultra-Strict** |
| **Approval Gate** | Optional | **Mandatory** |
| **Assumption Tolerance** | Low | **Zero** |
| **Specification Analysis** | Basic | **Detailed** |
| **User Confirmation** | Implied | **Explicit Required** |
| **Scope Listing** | Simple | **Detailed (Will/Won't)** |

## 🚦 How /sc:execute Works

### **Phase 1: Specification Analysis (NO CODE)**
```
User: /sc:execute user login form --framework react

Claude: I'll analyze your request for 'user login form' with React framework.

Based on your request, I understand you want:
1. React functional component for login form
2. Basic form structure
3. Component export

I will NOT add (unless you specify):
- Form validation (not specified)
- Submit functionality (not specified how to handle login)
- Password field styling (not specified)
- Error handling (not specified)
- Loading states (not specified)
- Redirect logic (not specified)
- Remember me checkbox (not specified)

Please specify exactly:
- What fields should the form have?
- How should form submission be handled?
- What validation is required?
- What should happen after successful/failed login?
```

### **Phase 2: Implementation (ONLY APPROVED)**
```
User: Email and password fields only. No validation. No submit handling. Just the form UI.

Claude: Perfect! I will create exactly:
1. React functional component named LoginForm
2. Form with email input field
3. Form with password input field
4. Basic form structure (no submission handling)
5. Component export

Should I proceed with ONLY these 5 items?

User: Yes

Claude: [Now proceeds with implementation of ONLY those 5 items]
```

## 🛡️ Key Features

### **1. Mandatory Approval Gate**
- Cannot proceed without explicit user confirmation
- User must respond with clear approval
- Detailed scope must be confirmed

### **2. Enhanced Specification Analysis**
- Lists both what WILL and WILL NOT be included
- Asks specific clarifying questions
- Zero assumptions about "obvious" functionality

### **3. Ultra-Strict Scope Control**
- Absolutely no additions beyond approved items
- No "improvements" or "optimizations"
- No "while I'm at it" additions

### **4. Question-Driven Clarification**
- When requirements are unclear, asks specific questions
- Requests exact specifications before proceeding
- Prevents proceeding with vague requirements

## 📋 Usage Examples

### **API Development**
```
/sc:execute GET /api/users endpoint --type api

# Claude will ask:
- What data should this endpoint return?
- What query parameters should it accept?
- What authentication is required?
- What error cases should be handled?
- What status codes should be returned?
```

### **Component Development**
```
/sc:execute navbar component --framework vue

# Claude will ask:
- What navigation items should be included?
- Should it be responsive?
- What styling framework to use?
- Should it handle authentication state?
- What click behaviors are needed?
```

### **Database Implementation**
```
/sc:execute users table --type database

# Claude will ask:
- What columns should the table have?
- What data types for each column?
- What constraints are needed?
- What indexes should be created?
- What relationships to other tables?
```

## ⚡ Benefits for Teams

### **For Developers**
- ✅ No scope creep
- ✅ Clear requirements
- ✅ Predictable deliverables
- ✅ Faster implementation cycles

### **For Project Managers**
- ✅ Accurate estimates
- ✅ Controlled scope
- ✅ Clear deliverable boundaries
- ✅ Reduced over-engineering

### **For QA Teams**
- ✅ Clear testing scope
- ✅ Defined acceptance criteria
- ✅ No surprise features
- ✅ Focused test coverage

### **For Product Owners**
- ✅ Exactly what was requested
- ✅ No unwanted features
- ✅ Clear feature boundaries
- ✅ Controlled development costs

## 🔧 Configuration Options

### **Strict Mode (Default)**
```
/sc:execute feature --strict
```
- Maximum strictness
- Mandatory approval for everything
- Zero tolerance for assumptions

### **Framework Specific**
```
/sc:execute component --framework react
/sc:execute api --framework express
/sc:execute service --framework django
```

### **Type Specific**
```
/sc:execute --type component    # UI components
/sc:execute --type api         # API endpoints
/sc:execute --type service     # Business logic
/sc:execute --type feature     # Complete features
```

## 🚨 Common Scenarios

### **Vague Requirements**
```
User: /sc:execute dashboard

Claude: I need more specific requirements for 'dashboard':

Please specify:
- What data should be displayed?
- What widgets/components are needed?
- What user interactions are required?
- What layout/design is expected?
- What framework should be used?

I cannot proceed without clear specifications.
```

### **Over-Specified Requirements**
```
User: /sc:execute user registration with validation, email confirmation, password strength checking, captcha, terms acceptance, and social login

Claude: I'll break this down into exact components:

Based on your request, I will create:
1. User registration form component
2. Email validation functionality
3. Password strength checking
4. Email confirmation system
5. Captcha integration
6. Terms acceptance checkbox
7. Social login buttons/integration

This is a large scope. Should I proceed with ALL these items, or would you like to prioritize and implement them in phases?
```

## 📈 Success Metrics

A successful `/sc:execute` operation:
- ✅ Delivers exactly what was requested
- ✅ No surprise additions
- ✅ User confirms scope before implementation
- ✅ Zero scope creep
- ✅ Clear requirements documentation

## 🔄 Migration from /sc:implement

If your team is currently using `/sc:implement`, you can gradually migrate:

1. **Start with new features** using `/sc:execute`
2. **Use for critical implementations** where scope control is essential
3. **Train team members** on the stricter methodology
4. **Eventually standardize** on `/sc:execute` for all implementations

## 🎉 Conclusion

`/sc:execute` provides the ultimate control over implementation scope, ensuring that AI assistance delivers exactly what you ask for, nothing more, nothing less. Perfect for teams that need predictable, controlled development cycles.

## 🆘 Troubleshooting

### **If Claude proceeds without approval:**
- Check that you're using `/sc:execute` not `/sc:implement`
- Ensure the command is properly formatted
- Report the issue for command behavior correction

### **If requirements are too vague:**
- Claude will ask for clarification
- Provide specific, detailed requirements
- Break large features into smaller, specific components

### **If you need to add scope:**
- Complete current implementation first
- Start new `/sc:execute` command for additional features
- Don't try to expand scope mid-implementation
