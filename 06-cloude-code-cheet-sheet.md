# Claude Code Quick Start Cheat Sheet

A comprehensive guide to getting started quickly with Claude Code, featuring best practices, exercises, and examples.

## How to Use This Guide

This cheat sheet is designed as a **progressive learning path** for beginners. Follow it in order:

1. **Quick Start** - Get Claude Code installed and configured (5 minutes)
2. **Core Features** - Understand what Claude Code can do (10 minutes)
3. **Essential Commands** - Learn the commands you'll use daily (10 minutes)
4. **Best Practices** - Master effective prompting techniques (15 minutes)
5. **Workflow Patterns** - See real-world examples in action (20 minutes)
6. **Exercises** - Practice with hands-on exercises (30+ minutes)
7. **Troubleshooting** - Reference when you get stuck (as needed)
8. **Quick Reference** - Bookmark for daily use (reference)

**Total time to proficiency:** ~2 hours of focused learning + practice

**For experienced users:** Jump to [Quick Reference Card](#quick-reference-card) for command lookup.

## Table of Contents

### Main Sections
- [Quick Start](#quick-start)
  - [Installation & Setup](#installation--setup)
- [Core Features](#core-features)
  - [1. Conversational Git Operations](#1-conversational-git-operations)
  - [2. File and Directory References](#2-file-and-directory-references)
  - [3. Extended Thinking Mode](#3-extended-thinking-mode)
    - [Thinking Budget Keywords](#thinking-budget-keywords)
    - [How Thinking Budget Works](#how-thinking-budget-works)
    - [Parallel Subagents](#parallel-subagents)
    - [When to Use Each Level](#when-to-use-each-level)
    - [Complete Example](#complete-example)
  - [4. Context Management Commands](#4-context-management-commands)
  - [5. Permission Modes](#5-permission-modes)
- [Essential Commands](#essential-commands)
  - [Development Workflow](#development-workflow)
  - [Code Navigation](#code-navigation)
  - [Planning & Review](#planning--review)
- [Best Practices](#best-practices)
  - [1. Be Specific with Instructions](#1-be-specific-with-instructions)
  - [2. Reference Existing Code Patterns](#2-reference-existing-code-patterns)
  - [3. Plan Before Execution](#3-plan-before-execution)
  - [4. Use Checklists for Complex Workflows](#4-use-checklists-for-complex-workflows)
  - [5. Test-Driven Development (TDD)](#5-test-driven-development-tdd)
  - [6. Visual Development Workflow](#6-visual-development-workflow)
  - [7. Work in Small, Focused Chunks](#7-work-in-small-focused-chunks)
  - [8. Pass Data Effectively](#8-pass-data-effectively)
  - [9. Headless Mode for Automation](#9-headless-mode-for-automation)
- [Workflow Patterns with Examples](#workflow-patterns-with-examples)
  - [Pattern 1: Simple Bug Fix](#pattern-1-simple-bug-fix)
  - [Pattern 2: New Feature Development](#pattern-2-new-feature-development)
  - [Pattern 3: Refactoring](#pattern-3-refactoring)
  - [Pattern 4: Code Review](#pattern-4-code-review)
  - [Pattern 5: Debugging Complex Issues](#pattern-5-debugging-complex-issues)
  - [Pattern 6: Performance Optimization](#pattern-6-performance-optimization)
- [Exercises](#exercises)
  - [Exercise 1: Create Your CLAUDE.md](#exercise-1-create-your-claudemd)
  - [Exercise 2: Test-Driven Feature Development](#exercise-2-test-driven-feature-development)
  - [Exercise 3: Visual Iteration Workflow](#exercise-3-visual-iteration-workflow)
  - [Exercise 4: File Reference Mastery](#exercise-4-file-reference-mastery)
  - [Exercise 5: Complex Refactoring with Planning](#exercise-5-complex-refactoring-with-planning)
  - [Exercise 6: Git Operations Mastery](#exercise-6-git-operations-mastery)
  - [Exercise 7: Extended Thinking for Architecture](#exercise-7-extended-thinking-for-architecture)
  - [Exercise 8: Thinking Keywords and Parallel Subagents](#exercise-8-thinking-keywords-and-parallel-subagents)
  - [Exercise 9: Headless Mode Automation](#exercise-9-headless-mode-automation)
- [Troubleshooting](#troubleshooting)
  - [Problem: Too Many Iterations](#problem-too-many-iterations)
  - [Problem: Wrong Implementation](#problem-wrong-implementation)
  - [Problem: Code Doesn't Match Style](#problem-code-doesnt-match-style)
  - [Problem: Missing Edge Cases](#problem-missing-edge-cases)
  - [Problem: Context Overflow](#problem-context-overflow)
  - [Problem: Tests Failing](#problem-tests-failing)
- [Quick Reference Card](#quick-reference-card)
  - [Most Used Commands](#most-used-commands)
  - [Thinking Budget Keywords](#thinking-budget-keywords-1)
  - [Permission Modes](#permission-modes-1)
  - [Headless Mode](#headless-mode)
- [Key Takeaways](#key-takeaways)
- [Success Metrics](#success-metrics)
- [Additional Resources](#additional-resources)

---

## Quick Start

### Installation & Setup

1. **Install Claude Code**
   ```bash
   # Follow official installation guide for your platform
   # Visit: https://claude.ai/code
   ```
   or simply run following in terminal
   ```bash
    curl -fsSL https://claude.ai/install.sh | bash
   ```
   and next command `claude` to get started
    ```bash
     claude
    ```
   

2. **Initialize in Your Project**
   ```bash
   cd your-project
   claude
   ```

3. **Create CLAUDE.md Configuration**
   Create a `CLAUDE.md` file in your project root to guide Claude:
   ```markdown
   # Project Goals
   Build fast, safe features with comprehensive tests.
   
   # Technology Stack
   - Node.js 20
   - React 18
   - TypeScript 5
   - PostgreSQL 15
   
   # Code Style
   - ESLint: Airbnb config
   - Prettier: default settings
   - TypeScript: strict mode
   
   # Testing
   - Unit tests: Vitest
   - E2E tests: Cypress
   - Always write/adjust tests first
   - Minimum 80% coverage
   
   # Pull Request Guidelines
   - Max 200 lines per PR
   - Include rationale and test proof
   - "DONE" = merged + tests + docs + monitoring
   
   # Common Commands
   - Review current file: claude -p "Review the current file and propose fixes"
   - Plan migration: claude -p "Plan a safe migration for X; list steps and checks"
   ```

---

## Core Features

Now that you're set up, let's explore what Claude Code can do. These core features form the foundation of your workflow.

### 1. Conversational Git Operations

Use natural language for Git tasks:

```bash
> What files have I changed?
> Commit my changes with a descriptive message
> Create a new branch called feature/user-authentication
> Show me the last 5 commits
> Help me resolve merge conflicts
> Create a pull request with title: "Add user authentication"
```

**Example:**
```bash
> I've added user authentication. Create a commit with message: 
  "feat(auth): add OAuth2 authentication with JWT tokens"
```

### 2. File and Directory References

Use `@` symbol to reference files or directories:

```bash
> Explain the logic in @src/utils/auth.js
> What's the structure of @src/components?
> Review @src/services/payment.ts for security issues
> Compare @src/components/Button.tsx with @src/components/Link.tsx
```

**Benefits:**
- Precise context without reading entire codebase
- Faster responses
- Better understanding of relationships

### 3. Extended Thinking Mode

For complex tasks, prompt Claude to think deeply using thinking budget keywords. These keywords allocate progressively more computational resources for Claude's reasoning process.

#### Thinking Budget Keywords

Claude Code supports different levels of thinking intensity, each allocating more thinking budget:

**1. `Think`** - Standard extended thinking
```bash
> Think about the best approach for implementing OAuth2 authentication.
```

**2. `Think hard`** - Increased thinking budget
```bash
> Think hard about potential security vulnerabilities in this authentication system.
```

**3. `Think harder`** - Significantly increased thinking budget
```bash
> Think harder about the architectural implications of migrating from REST to GraphQL.
```

**4. `Ultra Think`** - Maximum thinking budget allocation
```bash
> Ultra Think about the complete system design for a scalable microservices architecture.
```

#### How Thinking Budget Works

- **More budget = More reasoning time**: Claude spends more computational cycles analyzing the problem
- **Deeper analysis**: Higher levels allow Claude to explore more solution paths, consider more edge cases, and perform more thorough evaluations
- **Better for complex problems**: Use higher levels for architectural decisions, complex debugging, or multi-faceted problems

#### Parallel Subagents

Claude Code can use parallel subagents to tackle complex problems from multiple angles simultaneously:

```bash
> Use parallel subagents to analyze this problem:
  - Subagent 1: Focus on security implications
  - Subagent 2: Focus on performance optimization
  - Subagent 3: Focus on maintainability and code quality
  Then synthesize the findings into a comprehensive solution.
```

**Benefits of Parallel Subagents:**
- Multiple perspectives on the same problem
- Faster analysis of complex, multi-faceted issues
- Comprehensive coverage of different concerns
- Better synthesis of solutions

**Example with Thinking Keywords:**
```bash
> Ultra Think with parallel subagents about refactoring our payment system:
  - Subagent 1: Think harder about transaction safety and rollback strategies
  - Subagent 2: Think hard about API design and backward compatibility
  - Subagent 3: Think about testing strategy and edge cases
  Provide a unified recommendation.
```

#### When to Use Each Level

**Use `Think`:**
- Standard problem-solving
- Code review questions
- Simple architectural decisions
- Routine debugging

**Use `Think hard`:**
- Security-critical decisions
- Performance optimization
- Complex refactoring
- Multi-system integration

**Use `Think harder`:**
- Major architectural changes
- System design decisions
- Complex debugging across multiple systems
- Evaluating multiple competing solutions

**Use `Ultra Think`:**
- Critical system design decisions
- High-stakes architectural planning
- Complex multi-faceted problems requiring deep analysis
- Problems where the cost of mistakes is very high

**Use Parallel Subagents:**
- Problems with multiple orthogonal concerns
- When you need comprehensive analysis quickly
- Complex systems requiring multi-perspective evaluation
- Large refactoring with multiple considerations

#### Complete Example

```bash
> Ultra Think with parallel subagents about implementing a real-time chat system:

  Subagent 1 (Think harder): Analyze WebSocket vs Server-Sent Events
    - Scalability implications
    - Connection management
    - Message delivery guarantees
    
  Subagent 2 (Think hard): Design message persistence strategy
    - Database schema
    - Caching layer
    - Message history retrieval
    
  Subagent 3 (Think): Evaluate security considerations
    - Authentication per connection
    - Message encryption
    - Rate limiting
    
  Synthesize all findings into a comprehensive implementation plan.
```

**Best Practices:**
- Start with `Think` for most problems
- Escalate to `Think hard` or `Think harder` when initial analysis is insufficient
- Use `Ultra Think` sparingly for truly critical decisions
- Combine with parallel subagents for complex, multi-faceted problems
- Remember: More thinking budget = longer response time but deeper analysis

### 4. Context Management Commands

Claude Code provides several commands to manage your session context:

```bash
/clear    # Clear session context (keeps CLAUDE.md)
/compact  # Summarize session into single message
/help     # Show available commands and help
/exit     # Exit Claude Code session
```

**Command Details:**

- **`/clear`** - Removes all conversation history except `CLAUDE.md` configuration
  - Use when: Starting a new task, context is cluttered, or switching projects
  - Example: After completing a feature, use `/clear` before starting the next one

- **`/compact`** - Summarizes the entire conversation into a single condensed message
  - Use when: Long sessions where you want to preserve key context but reduce token usage
  - Example: After a 50-message debugging session, use `/compact` to continue with a clean summary

- **`/help`** - Displays all available commands and their usage
  - Use when: You forget a command or want to discover new features

- **`/exit`** - Safely exits the Claude Code session
  - Use when: You're done working and want to close the session

**Best Practices:**
- Use `/clear` after completing major tasks to start fresh
- Use `/compact` for long sessions to preserve essential context while reducing clutter
- Use `/help` to discover new commands as Claude Code evolves

### 5. Permission Modes

Permission modes control how Claude Code handles tool usage permissions, balancing safety and productivity.

#### Available Permission Modes

- **Default Mode**: Prompts for permission when first using each tool (recommended for beginners)
- **AcceptEdits Mode**: Automatically accepts file editing permissions (daily development)
- **Plan Mode**: Read-only mode providing detailed implementation plans (code reviews)
- **BypassPermissions Mode**: Skips all permission prompts (use with extreme caution)

#### How to Configure Permission Modes

**Method 1: Using Configuration Files**

Create or edit a settings file in your project:

**Project-level settings** (`.claude/settings.json` - checked into git):
```json
{
  "defaultMode": "acceptEdits"
}
```

**User-level settings** (`~/.claude/settings.json` - applies to all projects):
```json
{
  "defaultMode": "acceptEdits",
  "permissions": {
    "allow": [
      "Bash(npm run test:*)",
      "Read(~/.zshrc)"
    ]
  }
}
```

**Method 2: Using Keyboard Shortcuts**

During an active session:
- Press `Shift+Tab` repeatedly to cycle through permission modes
- The current mode is displayed in the UI
- Changes apply immediately to the current session

**Method 3: Command Line Flag**

Start Claude Code with a specific mode:
```bash
claude --mode acceptEdits
claude --mode plan
```

#### Allowing Specific Tools

You can allow specific tools without prompting by configuring `allowedTools`:

**In settings file:**
```json
{
  "permissions": {
    "allow": [
      "Edit",
      "Bash(eslint:*)",
      "Bash(npm run test:*)",
      "Read(src/**)"
    ]
  }
}
```

**Tool Permission Syntax:**
- `Edit` - Allow all file editing
- `Bash(command)` - Allow specific bash commands
- `Bash(command:*)` - Allow commands matching pattern
- `Read(path)` - Allow reading specific files/directories

#### When to Use Each Mode

**Default Mode** (Recommended for beginners):
- Learning Claude Code
- Working on critical code
- Unfamiliar with the codebase

**AcceptEdits Mode** (Daily development):
- Comfortable with Claude Code
- Working on non-critical features
- Want faster workflow

**Plan Mode** (Code review and planning):
- Reviewing code changes
- Planning architecture
- Getting implementation suggestions without changes

**BypassPermissions Mode** (Use with extreme caution):
- Automated scripts in secure environments
- CI/CD pipelines
- Only when you fully trust the operation

**⚠️ Safety Warning:**
- Never use `BypassPermissions` in production without thorough testing
- Always review changes before committing
- Use `Plan Mode` first to review what will change

---

## Essential Commands

These are the commands you'll use most frequently. Start here to get comfortable with daily operations.

### Development Workflow

```bash
# Start new feature
> Add user profile page with avatar upload

# Fix bug
> Fix the null pointer exception in UserService.ts line 45

# Run tests
> Run the test suite and fix any failures

# Code quality
> Run the linter and fix all issues

# Start dev server
> Start the development server and verify the feature works
```

### Code Navigation

```bash
# Find code
> Where is user authentication implemented?

# Understand code
> Explain what @src/services/auth.ts does

# Find patterns
> Show me examples of error handling in this codebase
```

### Planning & Review

```bash
# Plan before execution
> Plan the change. Identify impacted files, test plan, and safe rollback. 
  Then wait for my OK.

# Code review
> Review @src/components/Checkout for:
  - Security vulnerabilities
  - Edge cases
  - Performance issues
  - Better error handling opportunities
```

---

## Best Practices

Following these practices will dramatically improve your results and reduce back-and-forth iterations. Apply these principles from day one.

### 1. Be Specific with Instructions

**❌ Vague:**
```bash
> Make the login better
```

**✅ Specific:**
```bash
> Add input validation to the login form:
  - Email must be valid format (regex check)
  - Password minimum 8 characters with one number
  - Show error messages below each field in red
  - Disable submit button until all fields are valid
```

### 2. Reference Existing Code Patterns

**✅ Good:**
```bash
> Look at how existing widgets are implemented on the homepage to understand 
  the patterns, especially how code and interfaces are separated. 
  HotDogWidget.php is a good example. Then, implement a new calendar widget 
  following this pattern, supporting month selection and year navigation 
  with forward/backward paging. Use only libraries already in the codebase.
```

### 3. Plan Before Execution

Always ask Claude to plan complex changes:

```bash
> Plan the migration from REST to GraphQL:
  - List all impacted files
  - Identify breaking changes
  - Create test plan
  - Suggest rollback strategy
  - Wait for my approval before proceeding
```

### 4. Use Checklists for Complex Workflows

Create a checklist file for large tasks:

```markdown
# migration-checklist.md
- [ ] Plan: list steps and risks
- [ ] Batch 1: update configs
- [ ] Batch 2: update imports
- [ ] Batch 3: update API calls
- [ ] Tests: all passing
- [ ] Rollback plan: documented
```

Then reference it:
```bash
> Update the checklist as you complete each step
```

### 5. Test-Driven Development (TDD)

**Write tests first:**
```bash
> Write comprehensive tests for the user authentication feature. Cover:
  - Valid login scenarios
  - Invalid credentials
  - Session management
  - Edge cases like expired tokens
  - Rate limiting on failed attempts
```

**Then implement:**
```bash
> Now write the minimum code needed to make all tests pass. 
  Don't modify the tests.
```

### 6. Visual Development Workflow

For UI work, use visual feedback:

```bash
# Setup (one time)
> Set up Puppeteer MCP server so you can take screenshots of our React app.

# Implementation
> Here's the design mock [drag/drop image]. Implement this component, 
  take a screenshot of the result, and iterate until it matches the design.
```

### 7. Work in Small, Focused Chunks

**Best Practice:**
- Keep edits under 200 lines per change
- Commit often
- One feature per commit
- Test after each change

**Example:**
```bash
> Add user avatar upload feature (keep under 200 lines, commit when done)
```

### 8. Pass Data Effectively

**Methods to provide data:**
```bash
# Direct paste
> Here's the API response: [paste JSON]

# Pipe from file
cat data.json | claude "Analyze this data structure"

# Bash commands
> Run: cat logs/error.log | grep "ERROR" | head -20
  Then analyze these errors

# Custom slash commands
> /fetch-api-data
```

### 9. Headless Mode for Automation

**What is Headless Mode?**

Headless mode allows you to run Claude Code **without an interactive interface**, making it perfect for automation, scripting, and CI/CD pipelines. Instead of having a conversation, you send a single command and get a response.

**Key Difference:**
- **Interactive mode**: `claude` - Opens a chat interface for back-and-forth conversation
- **Headless mode**: `claude -p "command"` - Runs a single command and exits

**When to Use Headless Mode:**

✅ **Use headless mode for:**
- Automated code reviews in CI/CD pipelines
- Batch processing multiple files
- Scheduled maintenance tasks
- Integration with other tools/scripts
- One-off analysis tasks
- Running predefined checks

❌ **Don't use headless mode for:**
- Complex multi-step features (use interactive mode)
- Tasks requiring clarification or iteration
- Learning and experimentation
- Tasks where you need to review changes step-by-step

**Basic Usage:**

```bash
# Review current file
claude -p "Review the current file and propose fixes"

# Analyze logs
claude -p "Analyze logs in ./logs and summarize errors by code"

# Batch processing
claude -p "Fix all TypeScript errors in src/components"

# Run with specific permission mode
claude -p --mode acceptEdits "Format all Python files in src/"
```

**Advanced Options:**

```bash
# Output in JSON format (for parsing by other tools)
claude -p --output-format json "Analyze code quality"

# Resume a previous conversation
claude -p --resume session-id-123 "Continue from where we left off"

# Combine with allowed tools
claude -p --allowedTools "Edit,Bash(eslint:*)" "Fix all lint errors"
```

**Real-World Examples:**

**CI/CD Pipeline Integration:**
```bash
#!/bin/bash
# ci-review.sh

# Run automated code review
claude -p "Review all changed files for security issues" > review-report.txt

# Check if review found issues
if grep -q "CRITICAL" review-report.txt; then
  echo "Security issues found!"
  exit 1
fi
```

**Scheduled Maintenance:**
```bash
# cron job to check for outdated dependencies
claude -p "Check package.json for outdated dependencies and suggest updates"
```

**Batch File Processing:**
```bash
# Process multiple files
for file in src/**/*.ts; do
  claude -p "Add JSDoc comments to $file"
done
```

**Best Practices:**
- Use headless mode for predictable, well-defined tasks
- Always test headless commands in interactive mode first
- Use `--mode plan` to preview changes before applying them
- Combine with `--allowedTools` for safe automation
- Ensure stable network connection for CI/CD usage

---

## Workflow Patterns with Examples

Learn common development workflows with real-world examples. Each pattern shows the step-by-step process followed by a concrete example you can use immediately.

### Pattern 1: Simple Bug Fix

**When to use:** Quick fixes for bugs you've identified

**Workflow:**
```bash
1. > The save button in ProfileForm.tsx doesn't call the API.
     Expected: Should POST to /api/users/me with form data
     Actual: Button click does nothing, no console errors

2. [Claude fixes it]

3. > Run tests to verify the fix
```

**Real-World Example:**
```bash
> The login form in @src/components/LoginForm.tsx accepts invalid emails.
  Expected: Should validate email format using the same regex as @src/utils/validators.ts
  Actual: Accepts "notanemail" as valid
  Fix the validation and add a test case for this.
```

### Pattern 2: New Feature Development

**When to use:** Adding new functionality to your application

**Workflow:**
```bash
1. > Plan the user profile feature:
     - List impacted files
     - Suggest architecture
     - Create test plan
     Wait for approval.

2. [Review plan, approve]

3. > Write tests first for the profile feature

4. > Implement the feature to pass all tests

5. > Run linter and fix issues

6. > Create commit: "feat(profile): add user profile page with avatar upload"
```

**Real-World Example:**
```bash
> Add a search bar to the products page.

Requirements:
- Filter by product name as user types
- Debounce input by 300ms
- Show "No results found" when empty
- Clear button to reset
- Use the existing Input component from @src/components/Input.tsx
- Match the styling pattern in @src/components/Dashboard.tsx
```

### Pattern 3: Refactoring

**When to use:** Improving code structure without changing functionality

**Workflow:**
```bash
1. > Analyze the current architecture of @src/services/payment.ts

2. > Propose a refactoring plan to split this 600-line file into smaller modules

3. [Review plan]

4. > Execute the refactoring incrementally:
     - First, extract PaymentValidator
     - Then extract PaymentService
     - Finally, update PaymentController
     Run tests after each step.
```

**Real-World Example:**
```bash
> Refactor @src/services/paymentService.ts which is 600 lines.

Keep:
- All existing API endpoints working
- Current error handling pattern
- Existing test coverage

Change:
- Split into PaymentService and RefundService
- Extract validation into PaymentValidator
- Extract business logic into PaymentProcessor
- Maintain backward compatibility
```

### Pattern 4: Code Review

**When to use:** Before committing or creating pull requests

**Workflow:**
```bash
1. > Review all uncommitted changes for:
     - Security vulnerabilities
     - Edge cases
     - Performance issues
     - Code style consistency
     - Missing tests
```

**Real-World Example:**
```bash
> Review @src/components/Checkout.tsx for:
  - Security vulnerabilities (XSS, CSRF)
  - Edge cases (empty cart, network failures)
  - Performance issues (unnecessary re-renders)
  - Accessibility (ARIA labels, keyboard navigation)
  - Code style consistency with @src/components/Cart.tsx
```

### Pattern 5: Debugging Complex Issues

**When to use:** Investigating errors, crashes, or unexpected behavior

**Workflow:**
```bash
1. > Analyze this stack trace: [paste stack trace]
     Identify the root cause.

2. > Read the relevant files and explain what's happening

3. > Fix the issue and add tests to prevent regression

4. > Run the test suite and verify the fix works
```

### Pattern 6: Performance Optimization

**When to use:** Improving speed, efficiency, or resource usage

**Workflow:**
```bash
1. > Identify the performance bottleneck in [component/system]

2. > Analyze current implementation and suggest optimizations

3. > Implement optimizations incrementally

4. > Measure and verify improvements
```

**Real-World Example:**
```bash
> The product list page loads slowly with 1000+ items.
  Optimize it by:
  - Implementing virtual scrolling
  - Adding pagination (50 items per page)
  - Lazy loading images
  - Memoizing expensive computations
  - Use the pattern from @src/components/UserList.tsx
```

---

## Exercises

Practice makes perfect! Work through these exercises in order. Each builds on previous concepts and prepares you for real-world scenarios.

### Exercise 1: Create Your CLAUDE.md

**Task:** Set up project configuration

```bash
1. cd your-project
2. claude
3. > Create a CLAUDE.md file with:
     - Project goals
     - Technology stack
     - Code style rules
     - Testing guidelines
     - Common commands
4. Review and customize the generated file
```

**Expected Outcome:** A comprehensive `CLAUDE.md` file that guides Claude in your project.

---

### Exercise 2: Test-Driven Feature Development

**Task:** Implement a new feature using TDD

```bash
1. > Write comprehensive tests for a "user notification preferences" feature:
     - Enable/disable email notifications
     - Enable/disable push notifications
     - Save preferences to database
     - Validate input (boolean values only)
     - Handle API errors gracefully

2. Verify tests fail (they should, no implementation yet)

3. > Implement the feature to make all tests pass

4. > Run the test suite

5. > Create commit: "feat(notifications): add user preference management"
```

**Learning Points:**
- TDD workflow
- Test coverage
- Incremental development

---

### Exercise 3: Visual Iteration Workflow

**Task:** Build a UI component from a design

```bash
1. Find a UI design (screenshot or mockup)

2. > Here's the design for a product card component [attach image].
     Implement this component matching the design exactly.

3. [Claude implements]

4. > Take a screenshot of the rendered component

5. > Compare with design and iterate until perfect

6. Repeat steps 4-5 until satisfied
```

**Learning Points:**
- Visual development workflow
- Iterative refinement
- Design-to-code translation

---

### Exercise 4: File Reference Mastery

**Task:** Understand and modify existing code

```bash
1. > Explain the authentication flow in @src/services/auth.ts

2. > Show me how @src/components/LoginForm.tsx uses the auth service

3. > Add OAuth2 support following the existing pattern in @src/services/auth.ts

4. > Update @src/components/LoginForm.tsx to include OAuth2 button
```

**Learning Points:**
- Using @ references effectively
- Understanding code relationships
- Maintaining consistency

---

### Exercise 5: Complex Refactoring with Planning

**Task:** Refactor a large file safely

```bash
1. > Analyze @src/services/userService.ts (assume it's 800 lines)

2. > Plan a refactoring to split this into:
     - UserService (core logic)
     - UserRepository (data access)
     - UserValidator (validation)
     List impacted files, test plan, and rollback strategy.

3. [Review and approve plan]

4. > Execute Phase 1: Extract UserRepository
     Run tests after extraction.

5. > Execute Phase 2: Extract UserValidator
     Run tests after extraction.

6. > Execute Phase 3: Refactor UserService
     Run full test suite.

7. > Review all changes for issues
```

**Learning Points:**
- Planning complex changes
- Incremental refactoring
- Safety through testing

---

### Exercise 6: Git Operations Mastery

**Task:** Complete a feature using Git commands

```bash
1. > Create a new branch: feature/shopping-cart

2. > What files have I changed?

3. [Make changes with Claude]

4. > Commit changes: "feat(cart): add shopping cart functionality"

5. > Show me the last 3 commits

6. > Create a pull request:
     Title: "Add shopping cart feature"
     Summary: "Implements shopping cart with add/remove items, 
              quantity management, and persistence"
```

**Learning Points:**
- Conversational Git workflow
- Branch management
- PR creation

---

### Exercise 7: Extended Thinking for Architecture

**Task:** Design a new feature architecture

```bash
1. > I need to implement a real-time chat feature. Think deeply about:
     - WebSocket vs Server-Sent Events
     - Message persistence strategy
     - Scalability considerations
     - Security implications
     - Integration with existing auth system
     Provide a detailed analysis before implementation.

2. [Review Claude's analysis]

3. > Based on your analysis, implement Phase 1: WebSocket setup
```

**Learning Points:**
- Using extended thinking effectively
- Architectural decision-making
- Planning before coding

---

### Exercise 8: Thinking Keywords and Parallel Subagents

**Task:** Use different thinking budget levels and parallel subagents for complex problem-solving

```bash
1. Start with standard thinking:
   > Think about the best database schema for a user activity logging system.
   [Review the analysis]

2. Escalate to higher thinking budget:
   > Think hard about the performance implications of the proposed schema.
   [Compare with previous analysis - notice deeper insights]

3. Use even higher budget for critical decision:
   > Think harder about scalability when we reach 10 million users.
   [Notice more thorough analysis of edge cases]

4. Apply maximum thinking budget:
   > Ultra Think about the complete system architecture including:
     - Database design
     - Caching strategy
     - Query optimization
     - Data retention policies
   [Observe comprehensive, multi-layered analysis]

5. Use parallel subagents for multi-faceted problem:
   > Ultra Think with parallel subagents about migrating our monolith to microservices:
     
     Subagent 1 (Think harder): Analyze service boundaries and domain modeling
     Subagent 2 (Think hard): Evaluate deployment and infrastructure requirements
     Subagent 3 (Think): Consider team structure and development workflow changes
     Subagent 4 (Think hard): Assess data consistency and transaction management
     
     Synthesize all findings into a unified migration strategy.

6. Compare the depth and breadth of analysis at each level
```

**Learning Points:**
- Understanding thinking budget allocation
- When to use each thinking keyword level
- Leveraging parallel subagents for comprehensive analysis
- Recognizing when to escalate thinking budget
- Synthesizing multi-perspective analysis

**Key Observations:**
- `Think` provides good baseline analysis
- `Think hard` adds more depth and edge case consideration
- `Think harder` provides thorough architectural analysis
- `Ultra Think` delivers comprehensive, multi-layered solutions
- Parallel subagents enable simultaneous multi-perspective analysis

---

### Exercise 9: Headless Mode Automation

**Task:** Automate a repetitive task

```bash
# Create a script
#!/bin/bash
# fix-lint.sh

claude -p "Run ESLint on src/ directory and fix all auto-fixable issues"
claude -p "Run Prettier on src/ directory"
claude -p "Check for any remaining lint errors"

# Make executable and run
chmod +x fix-lint.sh
./fix-lint.sh
```

**Learning Points:**
- Automation with headless mode
- Scripting workflows
- CI/CD integration

---

## Troubleshooting

Stuck? These common problems and solutions will help you get back on track quickly.

### Problem: Too Many Iterations

**Symptom:** Still not done after 10+ messages

**Solution:**
```bash
> Let's start over. Here's exactly what I need:
  [Write very specific, detailed requirements with examples]
```

**Prevention:**
- Be specific from the start
- Provide examples
- Reference existing code patterns

---

### Problem: Wrong Implementation

**Symptom:** Code works but isn't what you wanted

**Solution:**
```bash
> This should actually work like: [specific description]
  See @src/components/SimilarComponent.tsx for the pattern to follow
```

---

### Problem: Code Doesn't Match Style

**Symptom:** Looks different from your codebase

**Solution:**
```bash
> Follow the same patterns and style as @src/components/Button.tsx
  Use our existing @src/utils/helpers.ts instead of creating new utilities
```

---

### Problem: Missing Edge Cases

**Symptom:** Works for happy path only

**Solution:**
```bash
> Also handle these cases:
  - Empty input
  - Network timeout
  - Invalid API response
  - Concurrent requests
  - User cancels operation
```

---

### Problem: Context Overflow

**Symptom:** Claude seems to forget earlier parts of conversation

**Solution:**
```bash
# Use /compact to summarize
/compact

# Or start fresh with /clear
/clear

# Then provide key context again
> Working on user authentication. Key files: @src/services/auth.ts, @src/components/LoginForm.tsx
```

---

### Problem: Tests Failing

**Symptom:** Tests break after changes

**Solution:**
```bash
> Fix all test failures before proceeding.
  Don't modify the tests unless there's a legitimate reason.
```

**Never ignore failing tests!**

---

## Quick Reference Card

Keep this section bookmarked for quick lookups during your daily work.

### Most Used Commands

```bash
# File operations
@filename              # Reference a file
@directory/            # Reference a directory

# Context management
/clear                 # Clear session (keeps CLAUDE.md)
/compact               # Summarize session
/help                  # Show available commands
/exit                  # Exit Claude Code session

# Git operations
> What files changed?
> Commit: "message"
> Create branch: name
> Create PR: title

# Development
> Run tests
> Fix lint errors
> Review changes
> Plan: [feature]

# Extended Thinking (increasing budget)
> Think about [problem]
> Think hard about [complex problem]
> Think harder about [very complex problem]
> Ultra Think about [critical problem]

# Parallel Subagents
> Use parallel subagents to analyze [problem] from multiple angles
```

### Thinking Budget Keywords

- `Think` - Standard extended thinking (routine problems)
- `Think hard` - Increased budget (security, performance)
- `Think harder` - High budget (major architecture)
- `Ultra Think` - Maximum budget (critical decisions)
- `Parallel subagents` - Multiple perspectives simultaneously

### Permission Modes

**Available modes:**
- `default` - Safe, prompts for permissions (beginners)
- `acceptEdits` - Auto-accept edits (daily use)
- `plan` - Read-only planning mode (code reviews)
- `bypassPermissions` - Skip all prompts (dangerous, CI/CD only)

**How to configure:**
```bash
# Method 1: Settings file (.claude/settings.json)
{
  "defaultMode": "acceptEdits",
  "permissions": {
    "allow": ["Edit", "Bash(npm run test:*)"]
  }
}

# Method 2: Keyboard shortcut
Shift+Tab  # Cycle through modes during session

# Method 3: Command line
claude --mode acceptEdits
```

### Headless Mode

**What it is:** Run Claude Code without interactive interface for automation

**Basic usage:**
```bash
claude -p "command"              # Run single command
claude -p --mode plan "command"   # Preview changes only
claude -p --output-format json    # Get JSON output
```

**When to use:**
- CI/CD pipelines
- Batch processing
- Automated reviews
- Scheduled tasks

**When NOT to use:**
- Complex multi-step features
- Tasks needing iteration
- Learning/experimentation
```

---

## Key Takeaways

1. **Be Specific** - Clear instructions = better results
2. **Reference Existing Code** - Use `@` to point to patterns
3. **Plan First** - Ask Claude to plan complex changes
4. **Test Continuously** - Run tests after each change
5. **Work Incrementally** - Small, focused changes
6. **Use CLAUDE.md** - Document your project context
7. **Manage Context** - Use `/clear` and `/compact` wisely
8. **Review Everything** - You're the expert, Claude is the assistant

---

## Success Metrics

Track your improvement:

**Week 1 (Baseline):**
- Messages per feature: ~15
- Time to review: ~30 min
- Bugs found in review: ~5

**Week 4 (Target):**
- Messages per feature: ~5
- Time to review: ~10 min
- Bugs found in review: ~1

**Team Benefits:**
- Development velocity: +30-50%
- Code review time: -40%
- Bug count: -30%
- Test coverage: +20%

---

## Additional Resources

- **Official Documentation:** https://claude.ai/code
- **Community:** Team Slack channel `#claude-code-help`
- **Training Modules:**
  - [Module 1: Fundamentals](./01-fundamentals.md)
  - [Module 2: Prompt Patterns](./02-prompt-patterns.md)
  - [Module 3: Best Practices](./03-best-practices.md)
  - [Module 4: Common Mistakes](./04-common-mistakes.md)
  - [Module 5: Quick Reference](./05-quick-reference.md)

---

**Ready to start?** Begin with Exercise 1 and work through each exercise to build your Claude Code skills!

**Remember:** Claude Code is a powerful assistant, but you're the expert on your codebase. Always review, test, and verify before deploying to production.

