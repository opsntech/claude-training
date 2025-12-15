# Module 2: Prompt Patterns

Master proven templates for common development tasks.

## Table of Contents
- [Pattern 1: Bug Fixes](#pattern-1-bug-fixes)
- [Pattern 2: New Features](#pattern-2-new-features)
- [Pattern 3: Refactoring](#pattern-3-refactoring)
- [Pattern 4: Performance](#pattern-4-performance)
- [Pattern 5: Code Review](#pattern-5-code-review)
- [Pattern 6: Testing](#pattern-6-testing)
- [Pattern 7: Investigation](#pattern-7-investigation)

---

## Pattern 1: Bug Fixes

### Template
```
[Where] has a bug where [what happens].
Expected: [correct behavior]
Actual: [wrong behavior]
[Error messages or reproduction steps]
```

### Examples

**Simple Bug**
```
The logout button in Header.tsx doesn't clear the user session.
Expected: User should be logged out and redirected to /login
Actual: Button clicks but nothing happens
```

**Bug with Error**
```
Getting "Cannot read property 'map' of undefined" in ProductList.tsx line 45.
This happens when the products array is empty.
Expected: Should show "No products found" message
```

**Intermittent Bug**
```
The search feature sometimes doesn't return results.
Expected: Should always return matching products
Actual: Works 80% of the time, occasionally returns empty array
Happens more often when typing quickly
```

### When to Use
- Known issue with specific symptoms
- Have error messages or stack traces
- Can describe expected vs actual behavior

---

## Pattern 2: New Features

### Template
```
Add [feature name] that [does what].

Requirements:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

[Optional: Technical constraints or preferences]
```

### Examples

**Simple Feature**
```
Add a search bar to the products page.

Requirements:
- Filter products by name as user types
- Debounce input by 300ms
- Show "No results" when nothing matches
- Clear button to reset search
```

**Feature with Integration**
```
Add email notifications when orders are placed.

Requirements:
- Send email to customer with order details
- Send email to admin for orders over $500
- Use the existing EmailService at src/services/email
- Queue emails rather than sending synchronously
- Include retry logic for failed sends
```

**Feature with Design Specs**
```
Add a loading skeleton for the product cards.

Requirements:
- Show while data is loading
- Match the card dimensions exactly
- Use our design system gray colors
- Animate with pulse effect like in UserCard.tsx
```

### When to Use
- Adding new functionality
- Building new components or pages
- Integrating new services

---

## Pattern 3: Refactoring

### Template
```
Refactor [what] to [goal].

Keep:
- [What must stay the same]

Change:
- [What should improve]

[Optional: Specific pattern or approach]
```

### Examples

**Extract Logic**
```
Refactor the checkout flow in CheckoutPage.tsx.

Keep:
- All existing functionality
- Current API contracts

Change:
- Extract validation logic into separate functions
- Move payment processing to a PaymentService
- Reduce file from 800 to under 300 lines
```

**Modernize Code**
```
Refactor UserProfile.tsx from class component to function component.

Keep:
- Exact same behavior and props
- All existing tests passing

Change:
- Use hooks instead of lifecycle methods
- Use functional setState patterns
```

**Improve Architecture**
```
Refactor the data fetching in the dashboard to use React Query.

Keep:
- Same data being displayed
- Same loading and error states

Change:
- Replace useEffect + fetch with useQuery
- Add proper caching and refetching
- Follow patterns from ProductList.tsx which already uses React Query
```

### When to Use
- Code is hard to maintain
- Want to improve structure without changing behavior
- Technical debt cleanup

---

## Pattern 4: Performance

### Template
```
[What] is slow/has performance issues.
[When it happens or how to reproduce]
Find the bottleneck and optimize.
```

### Examples

**Investigation + Fix**
```
The dashboard takes 5+ seconds to render with 1000+ items.
Happens on the /dashboard route when user has many items.
Find the performance bottleneck and fix it.
```

**Specific Optimization**
```
The product images are loading slowly on the gallery page.
Implement lazy loading and optimize image sizes.
Should load only images in viewport + next 5 rows.
```

**Bundle Size**
```
Our production bundle is 2.5MB which is too large.
Analyze what's making it big and reduce to under 1MB.
Consider code splitting and tree shaking.
```

### When to Use
- Performance issues
- Slow loading or rendering
- Large bundle sizes
- Memory leaks

---

## Pattern 5: Code Review

### Template
```
Review [what] for:
- [Concern 1]
- [Concern 2]
- [Concern 3]
```

### Examples

**Security Review**
```
Review src/api/auth for:
- SQL injection vulnerabilities
- Missing input validation
- Insecure password handling
- Session management issues
```

**General Review**
```
Review the changes in src/components/payment for:
- Edge cases not handled
- Error handling gaps
- Code quality issues
- Potential bugs
```

**Architecture Review**
```
Review the new messaging system design for:
- Scalability concerns
- Security implications
- Integration with existing auth
- Database schema design
```

### When to Use
- Before merging PRs
- After major changes
- Security-sensitive code
- Architecture decisions

---

## Pattern 6: Testing

### Template
```
Write tests for [what] that cover:
- [Test case 1]
- [Test case 2]
- [Test case 3]
```

### Examples

**Unit Tests**
```
Write unit tests for src/utils/validation.ts that cover:
- Valid email formats
- Invalid email formats
- Edge cases (empty string, very long emails, special characters)
- Password strength validation
```

**Integration Tests**
```
Write integration tests for the user registration flow that cover:
- Successful registration
- Duplicate email handling
- Invalid input validation
- Email sending verification
```

**End-to-End Test**
```
Write an e2e test for the checkout process that:
- Adds items to cart
- Proceeds through checkout steps
- Fills in payment information
- Completes the order
- Verifies order confirmation page
```

### When to Use
- New features need test coverage
- Found a bug (write test first)
- Improving test coverage
- Before refactoring

---

## Pattern 7: Investigation

### Template
```
[Question about codebase]
```
or
```
Explain how [feature/system] works
```

### Examples

**Understanding Code**
```
How does authentication work in this app?
```

**Finding Things**
```
Where are API endpoints defined?
```

**Architecture Questions**
```
Explain the data flow from user clicking "submit" to data being saved
```

**Debugging Prep**
```
What could cause the shopping cart to lose items on page refresh?
```

### When to Use
- Learning new codebase
- Understanding existing features
- Planning new work
- Debugging preparation

---

## Combining Patterns

You can chain patterns together:

### Example 1: Investigate → Implement
```
First: "How is pagination currently implemented in the products list?"
Then: "Add the same pagination pattern to the users list"
```

### Example 2: Implement → Test → Review
```
First: "Add user avatar upload feature"
Then: "Write tests covering success, file size limits, and invalid formats"
Finally: "Review the implementation for security issues"
```

### Example 3: Fix → Test → Commit
```
First: "Fix the email validation bug in LoginForm.tsx"
Then: "Add tests to prevent this regression"
Finally: "Run all tests and create a commit with appropriate message"
```

---

## Customizing Patterns

### Add Your Team's Context

**Before:**
```
Add a button that saves the form
```

**After (with your context):**
```
Add a save button to the form following our design system.
- Use the <Button variant="primary"> component
- Add loading state during save
- Show toast notification on success (using our ToastService)
- Follow the pattern in ProfileForm.tsx
```

### Reference Your Standards

```
Write tests using our testing conventions:
- Jest for unit tests
- React Testing Library for component tests
- Use our custom render() helper from test-utils
- Follow AAA pattern (Arrange, Act, Assert)
```

---

## Practice Exercises

Try these with your actual codebase:

1. **Bug Fix**: Pick a known bug and write a prompt using Pattern 1
2. **Feature**: Plan a small feature using Pattern 2
3. **Refactor**: Identify messy code and write a refactoring prompt using Pattern 3
4. **Investigation**: Ask about a part of the codebase you don't understand using Pattern 7

---

## Key Takeaways

1. **Use structured templates** for consistent results
2. **Be specific** about requirements and constraints
3. **Reference existing code** as examples when possible
4. **Chain patterns together** for complex workflows
5. **Customize with your context** for better alignment

---

**Next:** [Module 3: Best Practices](./03-best-practices.md) - Learn workflows and power user techniques.
