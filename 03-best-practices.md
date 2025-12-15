# Module 3: Best Practices

Level up with workflows, power user tips, and team collaboration strategies.

## Table of Contents
- [Workflow Best Practices](#workflow-best-practices)
- [Power User Tips](#power-user-tips)
- [Team Collaboration](#team-collaboration)
- [Quality Assurance](#quality-assurance)
- [Advanced Techniques](#advanced-techniques)

---

## Workflow Best Practices

### Starting a Session

**1. Navigate to Project Root**
```bash
cd /path/to/your/project
```

**2. State Your Goal Clearly**
```
Good: "Add password reset functionality to the auth system"
Not: "I need to work on auth stuff"
```

**3. Let Claude Explore If Needed**
For new areas or complex features, let Claude investigate first:
```
"How is email sending currently handled?"
"What's the structure of the authentication system?"
```

---

### During Development

**1. Track Progress Automatically**
Claude will create todo lists for complex tasks. You'll see:
- What's being worked on
- What's completed
- What's remaining

**2. Answer Questions Promptly**
When Claude asks for clarification:
- Provide specific answers
- Share examples if helpful
- Reference existing code patterns

**3. Review Changes in Real-Time**
- Check code as it's written
- Provide immediate feedback
- Course-correct early

**4. Test As You Go**
```
After feature: "Run the tests and fix any failures"
After changes: "Start the dev server and verify the feature works"
```

---

### Before Committing

Always complete this checklist:

```
1. "Run the test suite and fix any failures"
2. "Run the linter and fix all issues"
3. "Review all changes for potential issues"
4. "Create a commit with message following our convention"
```

**Example session:**
```
You: "Add user avatar upload feature"
Claude: [implements feature]
You: "Run tests"
Claude: [runs tests, fixes 2 failures]
You: "Run linter"
Claude: [fixes lint issues]
You: "Create a commit: feat: add user avatar upload with S3 integration"
Claude: [creates commit]
```

---

## Power User Tips

### Tip 1: Chain Related Tasks

Instead of multiple separate requests, chain tasks together:

**Less Efficient:**
```
You: "Add the feature"
Claude: [adds feature]
You: "Now test it"
Claude: [tests]
You: "Now commit it"
Claude: [commits]
```

**More Efficient:**
```
You: "Add user avatar upload, test it, and commit with message following our convention"
Claude: [does all three]
```

---

### Tip 2: Reference Specific Locations

Help Claude work faster by pointing to exact locations:

**Vague:**
```
"Fix the validation bug"
```

**Specific:**
```
"Fix the email validation in src/utils/validators.ts:45 - it doesn't handle plus signs"
```

**With Context:**
```
"The null check in UserService.ts:120 is causing the crash when profile data is missing"
```

---

### Tip 3: Use Existing Code as Examples

Point to code that should be replicated:

```
"Add sorting to the orders table like we have in ProductsTable.tsx -
same visual style and behavior"
```

```
"Implement error handling following the pattern in PaymentService.ts"
```

```
"Use the same loading skeleton approach as DashboardPage.tsx"
```

---

### Tip 4: Specify Quality Requirements

Be explicit about non-functional requirements:

**Error Handling:**
```
Add error handling that:
- Catches network failures gracefully
- Shows user-friendly error messages
- Logs errors to our monitoring service
- Includes retry logic for transient failures
- Has fallback UI for critical errors
```

**Performance:**
```
Implement pagination that:
- Loads 50 items per page
- Prefetches next page
- Uses virtual scrolling for smooth performance
- Maintains scroll position on navigation
```

**Security:**
```
Implement file upload with:
- File type validation (only images)
- Size limit of 5MB
- Virus scanning before storage
- Secure file naming to prevent path traversal
- Content-type verification
```

---

### Tip 5: Iterate Efficiently

Start simple, then add complexity:

**Iteration 1:**
```
"Add a users table that displays name, email, and role"
```

**Iteration 2:**
```
"Add sorting to the table columns"
```

**Iteration 3:**
```
"Add filtering by role"
```

**Iteration 4:**
```
"Add pagination with 20 items per page"
```

This approach:
- Gets working code faster
- Makes review easier
- Allows testing at each step
- Reduces complex rewrites

---

### Tip 6: Leverage Code Review

Use Claude to review your own code:

```
"Review my changes in src/components/Checkout for:
- Security vulnerabilities
- Edge cases I might have missed
- Performance issues
- Better error handling opportunities"
```

Before PRs:
```
"Review all uncommitted changes and suggest improvements"
```

---

## Team Collaboration

### Establish Team Standards

Document your conventions for Claude:

**Create a `.claude/context.md` file:**
```markdown
# Team Conventions

## Code Style
- TypeScript strict mode
- Functional components only
- Named exports preferred

## Testing
- Jest for unit tests
- React Testing Library for components
- 80% coverage minimum

## Commit Messages
Format: `type(scope): description`
Types: feat, fix, refactor, test, docs

## Architecture
- Feature-based folder structure
- Services in src/services
- Components in src/components
- Hooks in src/hooks
```

Then reference it:
```
"Add the feature following our team conventions"
```

---

### Code Review Standards

**For PR Author:**
```
"Review my changes before I create a PR. Check for:
- Breaking changes
- Missing tests
- Security issues
- Documentation needs"
```

**For PR Reviewer:**
```
"Review the changes in PR #123 focusing on:
- Architecture alignment
- Edge case handling
- Performance implications"
```

---

### Knowledge Sharing

**Document Decisions:**
```
"Explain why you chose this approach over alternatives"
```

**Create Examples:**
```
"Create an example showing how to use the new PaymentService"
```

**Update Documentation:**
```
"Update the API documentation to reflect the new endpoints"
```

---

## Quality Assurance

### Testing Strategy

**Comprehensive Testing:**
```
"Implement the shopping cart feature with full test coverage:
- Unit tests for cart logic
- Integration tests for checkout flow
- E2E test for complete purchase
- Edge cases: empty cart, out of stock, payment failures"
```

**Test-Driven Development:**
```
"Write tests first for the user registration validation, then implement"
```

**Regression Prevention:**
```
"Add tests for the bug in UserService.ts:45 before fixing it"
```

---

### Security Checklist

Always consider security for sensitive features:

```
"Implement user authentication with:
- Password hashing with bcrypt
- JWT tokens with expiration
- Refresh token rotation
- Rate limiting on login attempts
- CSRF protection
- SQL injection prevention
- XSS prevention on all user inputs"
```

---

### Performance Checklist

For user-facing features:

```
"Optimize the product gallery:
- Lazy load images
- Use appropriate image sizes
- Implement virtual scrolling for 1000+ items
- Add loading skeletons
- Cache API responses
- Debounce search input"
```

---

## Advanced Techniques

### Multi-Phase Projects

Break large features into phases:

**Phase 1: Foundation**
```
"Set up the database schema for the messaging system:
- Users table relationship
- Messages table with indexes
- Read receipts tracking
- Soft delete support"
```

**Phase 2: Backend**
```
"Implement the messaging API endpoints:
- POST /messages - send message
- GET /messages - fetch conversation
- PATCH /messages/:id/read - mark as read
- Include pagination and filtering"
```

**Phase 3: Frontend**
```
"Create the messaging UI:
- Conversation list
- Message thread view
- Compose message form
- Real-time indicators"
```

**Phase 4: Real-time**
```
"Add WebSocket support for live message updates"
```

**Phase 5: Testing**
```
"Write comprehensive tests for the entire messaging system"
```

---

### Debugging Complex Issues

**Step 1: Gather Information**
```
"Analyze the stack trace and identify the root cause:
[paste full stack trace]"
```

**Step 2: Investigate**
```
"Read the relevant files and explain what's happening"
```

**Step 3: Fix**
```
"Fix the issue and add tests to prevent regression"
```

**Step 4: Verify**
```
"Run the test suite and verify the fix works"
```

---

### Refactoring Large Codebases

**Step 1: Understand**
```
"Analyze the current architecture of the auth system"
```

**Step 2: Plan**
```
"Propose a refactoring plan to modernize the auth system"
```

**Step 3: Execute Incrementally**
```
"Refactor the login flow first, keeping everything else working"
```

**Step 4: Test Each Step**
```
"Run all tests after each change"
```

**Step 5: Continue**
```
"Now refactor the registration flow"
```

---

## Measuring Success

Track your improvement:

### Week 1 Baseline
- Messages per feature: ~15
- Time to review: ~30 min
- Bugs found in review: ~5

### Week 4 Target
- Messages per feature: ~5
- Time to review: ~10 min
- Bugs found in review: ~1

### Team Metrics
- Velocity increase: 30-50%
- Code review time: -40%
- Bug count: -30%
- Test coverage: +20%

---

## Key Takeaways

1. **Establish clear workflows** for consistency
2. **Chain related tasks** for efficiency
3. **Reference existing code** as examples
4. **Specify quality requirements** upfront
5. **Iterate incrementally** for complex features
6. **Review before committing** always
7. **Document team standards** for Claude
8. **Test comprehensively** at each step

---

**Next:** [Module 4: Common Mistakes](./04-common-mistakes.md) - Learn what to avoid and how to recover.
