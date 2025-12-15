# Module 5: Quick Reference

Your daily cheat sheet for working with Claude Code.

## Table of Contents
- [Request Templates](#request-templates)
- [Common Commands](#common-commands)
- [Quality Checklist](#quality-checklist)
- [Troubleshooting](#troubleshooting)
- [Keyboard Shortcuts](#keyboard-shortcuts)

---

## Request Templates

Copy, paste, and customize these for common tasks.

### Bug Fix
```
[Where] has a bug where [what happens].
Expected: [correct behavior]
Actual: [wrong behavior]
[Error message if any]
```

### New Feature
```
Add [feature] that [description].

Requirements:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

[Optional: Technical constraints]
```

### Refactoring
```
Refactor [what] to [goal].

Keep:
- [What stays the same]

Change:
- [What improves]
```

### Add Tests
```
Write tests for [what] covering:
- [Test case 1]
- [Test case 2]
- [Test case 3]
```

### Code Review
```
Review [what] for:
- [Concern 1]
- [Concern 2]
- [Concern 3]
```

### Investigation
```
How does [feature/system] work in this codebase?
```

### Performance
```
[What] is slow [when/where].
Find and fix the performance bottleneck.
```

---

## Common Commands

### Development Workflow

**Start new feature:**
```
Add [feature description with requirements]
```

**Fix a bug:**
```
Fix [bug description with location and symptoms]
```

**Run tests:**
```
Run the test suite and fix any failures
```

**Check code quality:**
```
Run the linter and fix all issues
```

**Start dev server:**
```
Start the development server and verify [feature] works
```

---

### Git Operations

**Create commit:**
```
Create a commit with message: [type](scope): [description]
```

**Create branch:**
```
Create a new branch called feature/[name] and switch to it
```

**Create PR:**
```
Create a pull request with title: [title]
Summary: [description]
```

**Review changes:**
```
Show me all uncommitted changes
```

---

### Code Navigation

**Find code:**
```
Where is [functionality] implemented?
```

**Understand code:**
```
Explain what [file/function] does
```

**Find patterns:**
```
Show me examples of [pattern] in this codebase
```

---

## Quality Checklist

Use this before considering work "done":

### Functionality
- [ ] Feature works as specified
- [ ] All edge cases handled
- [ ] Error handling in place
- [ ] Input validation complete

### Code Quality
- [ ] Follows existing patterns
- [ ] No code duplication
- [ ] Clear variable names
- [ ] No unnecessary complexity

### Testing
- [ ] Unit tests written
- [ ] Integration tests if needed
- [ ] All tests passing
- [ ] Edge cases tested

### Security
- [ ] Input validated
- [ ] No SQL injection risk
- [ ] No XSS vulnerabilities
- [ ] Authentication/authorization checked

### Performance
- [ ] No obvious bottlenecks
- [ ] Efficient algorithms used
- [ ] Proper indexing if database
- [ ] Lazy loading where appropriate

### Documentation
- [ ] Code is self-documenting
- [ ] Complex logic has comments
- [ ] API docs updated if needed
- [ ] README updated if needed

---

## Troubleshooting

### Problem: Too Many Iterations

**Symptom:** Still not done after 10+ messages

**Fix:**
```
Let's start over. Here's exactly what I need:
[Write very specific, detailed requirements]
```

---

### Problem: Wrong Implementation

**Symptom:** Code works but isn't what you wanted

**Fix:**
```
This should actually work like: [specific description]
See [existing-file.ts] for the pattern to follow
```

---

### Problem: Code Doesn't Match Your Style

**Symptom:** Looks different from your codebase

**Fix:**
```
Follow the same patterns and style as [existing-file.ts]
Use our existing [component/service/utility] instead of creating new
```

---

### Problem: Missing Edge Cases

**Symptom:** Works for happy path only

**Fix:**
```
Also handle these cases:
- [Edge case 1]
- [Edge case 2]
- [Edge case 3]
```

---

### Problem: No Error Handling

**Symptom:** Crashes on errors

**Fix:**
```
Add error handling like in [example-file.ts]:
- Try/catch blocks
- User-friendly messages
- Proper logging
- Graceful degradation
```

---

### Problem: Tests Failing

**Symptom:** Tests break after changes

**Fix:**
```
Fix all test failures before proceeding
```

**Don't ignore failing tests!**

---

## Keyboard Shortcuts

Quick actions during development:

### When to Break the Flow

**Stop and clarify if:**
- You're not sure what Claude is doing
- Results aren't what you expected
- You realize you need something different

**Just say:**
```
"Wait, I need to clarify..."
"Actually, let's do this differently..."
"Stop - this isn't what I wanted..."
```

---

## One-Liners for Speed

### Quick Fixes
```
Fix the typo in [file]:[line]
Remove unused imports from [file]
Add type annotations to [function]
Extract [code] into a separate function
```

### Quick Tests
```
Test this in the dev environment
Verify the API works with Postman/curl
Check if this causes any console errors
```

### Quick Checks
```
Are there any TypeScript errors?
Is this code secure?
Does this follow our conventions?
What's the performance impact?
```

---

## Daily Workflow Template

Start each coding session:

```
1. "Show me what I was working on last"
   → Review context

2. "[Implement specific feature/fix]"
   → Do the work

3. "Run tests and fix failures"
   → Verify quality

4. "Review changes for issues"
   → Final check

5. "Create commit: [message]"
   → Save work
```

---

## When to Use Each Pattern

| Task | Template | Example |
|------|----------|---------|
| Known bug | Bug Fix | "Login fails with wrong error" |
| New functionality | New Feature | "Add password reset" |
| Improve structure | Refactoring | "Split large UserService" |
| Need context | Investigation | "How does auth work?" |
| Before merging | Code Review | "Review for security issues" |
| Low test coverage | Add Tests | "Test the checkout flow" |
| Slow performance | Performance | "Dashboard loads slowly" |

---

## Response Time Expectations

| Task Type | Typical Messages | If Longer, Fix By |
|-----------|-----------------|-------------------|
| Simple bug fix | 1-2 | Being more specific about location |
| Small feature | 2-4 | Adding requirements and examples |
| Medium feature | 3-6 | Referencing existing patterns |
| Complex feature | 5-10 | Breaking into phases |
| Investigation | 1-2 | Asking specific questions |
| Refactoring | 3-7 | Clarifying scope and goals |

**If any task exceeds these ranges, you need to provide more context or be more specific.**

---

## Quality Gates

Don't move forward until:

**After Implementation:**
- [ ] Code compiles/runs
- [ ] No obvious errors in code

**Before Testing:**
- [ ] All linter issues fixed
- [ ] No console errors

**Before Committing:**
- [ ] All tests pass
- [ ] Code reviewed
- [ ] Changes verified in dev

**Before PR:**
- [ ] Full test suite passes
- [ ] No breaking changes
- [ ] Documentation updated

---

## Emergency Fixes

When production is broken:

**1. Quick diagnosis:**
```
[Error message/symptoms]
What's causing this and how do we fix it?
```

**2. Immediate fix:**
```
Fix [critical issue] - prioritize working over perfect
```

**3. Verify:**
```
Test the fix in production-like environment
```

**4. Proper solution later:**
```
Create a proper long-term fix with tests
```

---

## Metrics to Track

Measure your improvement:

### Individual Metrics
- Messages per task (target: <5 for most tasks)
- Time from request to working code
- Code review feedback items
- Bugs found in testing

### Team Metrics
- Development velocity
- Code review time
- Bug count in production
- Test coverage
- Time to resolve issues

---

## Getting Help

**If stuck:**
1. Check [Common Mistakes](./04-common-mistakes.md)
2. Try being more specific
3. Reference similar existing code
4. Ask teammate who's mastered Claude
5. Post in team Slack channel

**If Claude isn't working right:**
1. Check your prompt clarity
2. Verify you provided enough context
3. Reference existing patterns
4. Start over with better requirements

---

## Remember

**The 3 Keys to Success:**

1. **Be Specific**
   - Exact requirements
   - Specific locations
   - Clear examples

2. **Reference Existing Code**
   - Point to patterns
   - Show examples
   - Maintain consistency

3. **Test Continuously**
   - After each change
   - Fix issues immediately
   - Don't accumulate problems

---

## Quick Start Examples

Copy these to practice:

### Example 1: Bug Fix
```
The save button in ProfileForm.tsx doesn't call the API.
Expected: Should POST to /api/users/me with form data
Actual: Button click does nothing, no console errors
```

### Example 2: Feature
```
Add a search bar to the products page.

Requirements:
- Filter by product name as user types
- Debounce input by 300ms
- Show "No results found" when empty
- Clear button to reset

Use the existing Input component from our design system.
```

### Example 3: Refactor
```
Refactor PaymentController.ts which is 600 lines.

Keep:
- All existing API endpoints working
- Current error handling

Change:
- Split into PaymentController and RefundController
- Extract validation into PaymentValidator
- Extract business logic into PaymentService
```

---

**This concludes the training modules. You're ready to become a Claude Code power user!**

**Review:**
- [Module 1: Fundamentals](./01-fundamentals.md)
- [Module 2: Prompt Patterns](./02-prompt-patterns.md)
- [Module 3: Best Practices](./03-best-practices.md)
- [Module 4: Common Mistakes](./04-common-mistakes.md)

**Back to:** [Main README](../../README.md)
