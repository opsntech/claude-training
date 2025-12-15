# Module 4: Common Mistakes

Learn what to avoid, recognize problems early, and fix them fast.

## Table of Contents
- [Communication Mistakes](#communication-mistakes)
- [Workflow Mistakes](#workflow-mistakes)
- [Technical Mistakes](#technical-mistakes)
- [How to Recover](#how-to-recover)
- [Red Flags](#red-flags)

---

## Communication Mistakes

### Mistake 1: Being Too Vague

**❌ What Not to Do:**
```
"Make the app better"
"Fix the bugs"
"Improve performance"
"Update the design"
```

**✅ What to Do Instead:**
```
"Add loading states to all API calls - show spinners during fetch"
"Fix the null pointer exception in UserService.ts line 45"
"Optimize the product list - it's slow with 500+ items"
"Update button styles to match the new design system colors"
```

**Why it matters:** Vague requests lead to guesswork, multiple iterations, and wasted time.

---

### Mistake 2: Assuming Claude Knows Your Codebase

**❌ What Not to Do:**
```
"Update the user function"
(Which file? Which function? What update?)
```

**✅ What to Do Instead:**
```
"Update the updateUser function in src/services/UserService.ts
to also update the lastModified timestamp"
```

**Even Better:**
```
"The updateUser function in src/services/UserService.ts
doesn't update the lastModified field. Add that."
```

**Why it matters:** Claude needs to search your codebase. Specificity saves time.

---

### Mistake 3: Asking for Plans Instead of Action

**❌ What Not to Do:**
```
"How would you add authentication?"
"What's the best way to implement caching?"
"Can you create a plan for refactoring?"
```

**✅ What to Do Instead:**
```
"Add JWT-based authentication to the API"
"Implement Redis caching for the product catalog"
"Refactor the UserController to separate auth and profile logic"
```

**Why it matters:** Claude will explore and plan automatically when needed. Just ask for what you want done.

**Exception:** Investigation questions ARE good:
```
"How is authentication currently implemented?"
"Where should I add caching based on the existing architecture?"
```

---

### Mistake 4: Over-Explaining the How

**❌ What Not to Do:**
```
"First read UserService.ts, then search for the updateUser function,
then check if it has a lastModified parameter, then add it if missing,
then update the tests..."
```

**✅ What to Do Instead:**
```
"The updateUser function should update the lastModified timestamp
but currently doesn't. Fix this and update tests."
```

**Why it matters:** Let Claude figure out the steps. You focus on the what and why.

---

### Mistake 5: Not Providing Examples

**❌ What Not to Do:**
```
"Add error handling"
```

**✅ What to Do Instead:**
```
"Add error handling like we have in PaymentService.ts:
- Try/catch blocks
- User-friendly error messages
- Logging to our error service
- Fallback UI"
```

**Why it matters:** Examples ensure consistency with your existing patterns.

---

## Workflow Mistakes

### Mistake 6: Batching Unrelated Tasks

**❌ What Not to Do:**
```
"Fix the login bug, add dark mode, update README,
refactor the database layer, and optimize images"
```

**✅ What to Do Instead:**
Complete one task at a time:
```
First: "Fix the login bug in AuthService.ts"
Then: "Add dark mode toggle to settings"
Then: "Refactor the database connection logic"
```

**Why it matters:**
- Easier to review
- Easier to test
- Easier to debug if something goes wrong
- Better commit history

---

### Mistake 7: Not Testing Along the Way

**❌ What Not to Do:**
```
Build entire feature → Never test → PR → Everything breaks
```

**✅ What to Do Instead:**
```
Add feature → "Run tests and fix failures"
Add more → "Test in dev server"
Complete → "Run full test suite"
→ "Create commit"
```

**Why it matters:** Catching issues early is exponentially faster than debugging later.

---

### Mistake 8: Ignoring Test Failures

**❌ What Not to Do:**
```
You: "Add the new feature"
Claude: [adds feature, 5 tests fail]
You: "Great! Now add another feature"
```

**✅ What to Do Instead:**
```
You: "Add the new feature"
Claude: [adds feature, 5 tests fail]
You: "Fix all test failures before moving on"
Claude: [fixes tests]
You: "Now add the next feature"
```

**Why it matters:** Broken tests indicate broken functionality. Fix immediately.

---

### Mistake 9: Not Reviewing Before Committing

**❌ What Not to Do:**
```
"Just commit everything with message 'updates'"
```

**✅ What to Do Instead:**
```
"Review all changes for issues, then create commit
following our convention: feat(auth): add password reset flow"
```

**Why it matters:** Catch issues before they hit your git history.

---

## Technical Mistakes

### Mistake 10: Not Specifying Quality Requirements

**❌ What Not to Do:**
```
"Add file upload"
```
(What about size limits? File types? Security? Error handling?)

**✅ What to Do Instead:**
```
"Add file upload with:
- Max size 5MB
- Only allow images (jpg, png, webp)
- Validate file type on client and server
- Show progress bar
- Handle errors gracefully
- Scan for malware before saving"
```

**Why it matters:** Missing requirements lead to incomplete implementations.

---

### Mistake 11: Forgetting Edge Cases

**❌ What Not to Do:**
```
"Add a shopping cart"
```

**✅ What to Do Instead:**
```
"Add a shopping cart that handles:
- Empty cart state
- Items going out of stock
- Price changes during checkout
- Quantity limits
- Promotional codes
- Network failures during save"
```

**Why it matters:** Edge cases are where bugs hide.

---

### Mistake 12: Not Considering Security

**❌ What Not to Do:**
```
"Add an admin panel"
```
(Who can access it? How is it protected?)

**✅ What to Do Instead:**
```
"Add an admin panel:
- Only accessible to users with admin role
- Check permissions on every endpoint
- Log all admin actions
- Rate limit sensitive operations
- Add CSRF protection
- Validate all inputs server-side"
```

**Why it matters:** Security can't be an afterthought.

---

### Mistake 13: Premature Optimization

**❌ What Not to Do:**
```
"Optimize everything for maximum performance before we even have users"
```

**✅ What to Do Instead:**
```
"Implement the feature with reasonable performance,
then we'll optimize bottlenecks if needed"
```

**Exception: Avoid obvious problems:**
```
"Implement pagination for the user list (we have 10,000+ users)"
```

**Why it matters:** Optimize when you have data showing bottlenecks.

---

## How to Recover

### When Results Aren't What You Expected

**1. Be Direct About What's Wrong**
```
"The button should be blue (#2563eb), not red"
"This should trigger on blur, not on change"
"The validation should happen before the API call, not after"
```

**2. Show, Don't Just Tell**
```
"The error message should look like the one in LoginForm.tsx:45"
"Use the same layout as ProductCard.tsx"
```

**3. Provide Examples**
```
"When I type 'test@example.com', it should be valid
When I type 'invalid', it should show error: 'Invalid email format'"
```

---

### When You're Getting Too Many Iterations

**Red flag:** If you're on message 10+ and still not done.

**Stop and reset:**
```
"Let's start over. Here's exactly what I need:
[Write a very specific, detailed description]"
```

**Or provide more context:**
```
"I should have mentioned: we're using React 18 with TypeScript,
and we already have a validation library in src/utils/validation.ts.
Let's use that instead."
```

---

### When Claude Makes Assumptions

**Clarify immediately:**
```
❌ "I guess that works..."
✅ "Actually, we need it to work differently: [explain how]"
```

**Set constraints:**
```
"Don't add any new dependencies - use what we already have"
"Keep the existing API contract - don't change function signatures"
"Match the exact styling of the other forms"
```

---

## Red Flags

Watch for these warning signs:

### 🚩 Red Flag 1: Taking Too Long
If conversation exceeds 10 messages for a simple feature:
- You're being too vague
- You're not providing enough context
- You need to be more specific about requirements

**Fix:** Write a comprehensive, specific request and start over.

---

### 🚩 Red Flag 2: Code Doesn't Match Your Style
If the code doesn't look like your codebase:
- You didn't reference existing patterns
- You didn't specify your conventions
- Claude hasn't seen similar code

**Fix:** Point to example code:
```
"Follow the same patterns as UserService.ts"
"Use our existing Button component, not a plain <button>"
```

---

### 🚩 Red Flag 3: Missing Error Handling
If code lacks error handling:
- You didn't specify it in requirements
- You didn't reference examples with error handling

**Fix:**
```
"Add comprehensive error handling like in PaymentService.ts"
```

---

### 🚩 Red Flag 4: No Tests Written
If feature is done but no tests exist:
- You didn't ask for tests
- You didn't specify test requirements

**Fix:**
```
"Write comprehensive tests covering happy path and error cases"
```

---

### 🚩 Red Flag 5: Breaking Changes
If existing functionality breaks:
- Requirements weren't clear about preserving behavior
- Edge cases weren't considered

**Fix:**
```
"The checkout still needs to work exactly as before.
Only add the new coupon code feature without changing existing behavior."
```

---

## Quick Fixes Cheat Sheet

| Problem | Quick Fix |
|---------|-----------|
| Too vague | Add specific requirements and examples |
| Wrong file | Specify exact file path |
| Wrong approach | "Actually, use [specific approach]" |
| Missing edge cases | "Also handle [case1], [case2], [case3]" |
| Wrong style | "Follow the pattern in [file.ts]" |
| No tests | "Write tests covering [scenarios]" |
| No error handling | "Add error handling like [example.ts]" |
| Too complex | "Keep it simple - just [specific need]" |
| Too many iterations | Start over with specific requirements |

---

## Prevention Checklist

Before asking Claude to implement:

- [ ] Can I describe this in one clear sentence?
- [ ] Have I specified all requirements?
- [ ] Have I mentioned edge cases?
- [ ] Have I referenced similar existing code?
- [ ] Have I specified quality requirements (testing, security, performance)?
- [ ] Do I know what "done" looks like?

If you answer "no" to any, add that information first.

---

## Key Takeaways

1. **Be specific** - vague requests waste time
2. **Reference existing code** - for consistency
3. **One task at a time** - for quality
4. **Test continuously** - catch issues early
5. **Specify all requirements** - including edge cases
6. **Course correct immediately** - don't wait
7. **Start over if needed** - with better details
8. **Watch for red flags** - and fix fast

---

**Next:** [Module 5: Quick Reference](./05-quick-reference.md) - Cheat sheet for daily use.
