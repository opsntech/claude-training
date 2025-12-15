# Module 1: Fundamentals

Learn the core principles of effective communication with Claude Code.

## Table of Contents
- [What is Claude Code?](#what-is-claude-code)
- [Core Principles](#core-principles)
- [What Claude Does Best](#what-claude-does-best)
- [Your First Requests](#your-first-requests)

---

## What is Claude Code?

Claude Code is an AI-powered development assistant that:
- Reads and understands your entire codebase
- Writes production-quality code across multiple files
- Debugs issues and suggests fixes
- Refactors code while maintaining functionality
- Runs tests, handles git operations, and manages your development workflow

**Key insight:** Claude Code is not a code generator - it's a skilled development partner that thinks through problems and implements complete solutions.

---

## Core Principles

### 1. Be Specific and Direct

Claude works best with clear, actionable requests.

#### Examples

**✅ Good:**
```
Add input validation to the login form:
- Email must be valid format
- Password minimum 8 characters
- Show error messages below each field
```

**❌ Bad:**
```
Make the login better
```

**Why it matters:** Specificity eliminates guesswork and reduces back-and-forth iterations.

---

### 2. Provide Context When Needed

For complex tasks, share relevant information upfront.

#### Examples

**✅ Good:**
```
We're using React 18 with TypeScript and React Query for data fetching.
Add a user profile page that:
- Fetches data from /api/users/:id
- Shows loading and error states
- Matches the styling in DashboardPage.tsx
```

**❌ Bad:**
```
Add a user profile page
```

**Why it matters:** Context helps Claude match your existing patterns and architecture.

---

### 3. Let Claude Explore First

For unfamiliar areas, let Claude investigate before implementing.

#### Examples

**✅ Good:**
```
How is authentication currently handled in this app?
```
Then after understanding:
```
Add OAuth support following the existing auth pattern
```

**❌ Bad:**
```
Add OAuth to src/auth/index.ts
```
(Without knowing if that's the right place or approach)

**Why it matters:** Understanding existing patterns prevents architectural mismatches.

---

### 4. Trust but Verify

Claude is highly capable but not infallible.

#### Best Practice Flow:
1. Make a clear request
2. Let Claude implement
3. Review the changes
4. Test the functionality
5. Provide feedback if needed

**Remember:** You're the expert on your codebase and requirements. Claude is the expert on implementation.

---

## What Claude Does Best

### ✅ Excellent For

**Writing Production Code**
- Complete features with proper error handling
- Multi-file implementations
- Following existing patterns

**Debugging**
- Analyzing stack traces
- Finding root causes across files
- Suggesting fixes with explanations

**Refactoring**
- Restructuring code while preserving behavior
- Extracting reusable components
- Modernizing legacy code

**Code Review**
- Identifying security vulnerabilities
- Spotting edge cases
- Suggesting improvements

**Testing**
- Writing unit tests
- Creating integration tests
- Generating test cases

**Development Workflow**
- Git operations (commits, branches, PRs)
- Running builds and tests
- Fixing linter errors

### ⚠️ Less Ideal For

**Vague Requests**
- "Make it better" needs specifics
- "Optimize everything" needs focus areas

**Pure Design Decisions**
- Prefers your architectural guidance
- Will ask questions rather than assume

**Guessing Requirements**
- Better to clarify than assume
- Will propose options when unclear

---

## Your First Requests

### Exercise 1: Simple Bug Fix

```
The save button on ProfilePage.tsx doesn't work when clicked.
It should call updateProfile() but nothing happens.
```

**What Claude will do:**
1. Read ProfilePage.tsx
2. Identify the issue
3. Fix it
4. Explain what was wrong

---

### Exercise 2: Small Feature

```
Add a character counter to the bio textarea on the profile page.
Show "X/500 characters" below the field.
Turn red when over limit.
```

**What Claude will do:**
1. Find the bio textarea
2. Add state management for counting
3. Implement the UI
4. Add styling for the error state

---

### Exercise 3: Code Investigation

```
Where is the user session data stored in this application?
```

**What Claude will do:**
1. Search for session-related code
2. Explain the current implementation
3. Show relevant file locations

---

## Common First-Time Questions

**Q: How much detail should I provide?**
A: Enough to be clear, not so much you're writing the code yourself. Think of it like briefing a senior developer.

**Q: What if I don't know the technical details?**
A: Describe the behavior you want. Claude can figure out implementation details.

**Q: Should I tell Claude which files to edit?**
A: Only if you know for sure. Otherwise, let Claude find the right files.

**Q: What if Claude gets it wrong?**
A: Just say what's wrong: "The button should be blue, not red" or "This should validate on blur, not on change"

**Q: How do I know if I'm doing it right?**
A: If you get working code in 1-3 messages, you're doing great. If it takes 10+ messages, try being more specific.

---

## Key Takeaways

1. **Be clear and specific** in your requests
2. **Provide context** for complex features
3. **Let Claude explore** unfamiliar code
4. **Review all changes** before accepting
5. **Iterate quickly** with direct feedback

---

**Next:** [Module 2: Prompt Patterns](./02-prompt-patterns.md) - Learn proven templates for common development tasks.
