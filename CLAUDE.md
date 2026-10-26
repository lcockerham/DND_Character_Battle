# CLAUDE.md - AI Assistant Guide for DND Character Battle

**Last Updated:** 2026-01-19
**Repository:** DND_Character_Battle
**Current Branch:** claude/add-claude-documentation-X2QHh

## Table of Contents

1. [Project Overview](#project-overview)
2. [Repository Status](#repository-status)
3. [Development Workflow](#development-workflow)
4. [Git Branch Conventions](#git-branch-conventions)
5. [Code Structure Guidelines](#code-structure-guidelines)
6. [Development Best Practices](#development-best-practices)
7. [Testing Conventions](#testing-conventions)
8. [Documentation Standards](#documentation-standards)
9. [Key Conventions for AI Assistants](#key-conventions-for-ai-assistants)

---

## Project Overview

**DND_Character_Battle** is a project focused on simulating and managing Dungeons & Dragons character battles.

### Project Goals
- Simulate D&D 5e combat mechanics accurately
- Provide character creation and management functionality
- Enable battle simulations between characters
- Track combat statistics and outcomes

### Target Use Cases
- D&D combat simulation and planning
- Character build testing and optimization
- Game master tools for encounter balancing
- Educational tool for learning D&D combat mechanics

---

## Repository Status

**Current State:** 🚧 **New Project - No Codebase Yet**

This is a freshly initialized repository. The codebase is ready to be developed from scratch.

### What's Present
- Git repository initialized
- Branch: `claude/add-claude-documentation-X2QHh`
- This CLAUDE.md documentation file

### What Needs to Be Added
- Project setup (package.json, requirements.txt, or equivalent)
- Source code structure
- Testing framework
- Build/deployment configuration
- README.md for end users
- License file
- .gitignore file

---

## Development Workflow

### For AI Assistants

When working on this repository:

1. **Always work on feature branches** starting with `claude/`
2. **Never push directly to main/master**
3. **Read before modifying** - always read existing files before making changes
4. **Commit frequently** with clear, descriptive messages
5. **Push changes** when work is complete using `git push -u origin <branch-name>`

### Branch Lifecycle

```
1. Create/checkout feature branch (claude/feature-name-XXXXX)
2. Develop and test changes
3. Commit with clear messages
4. Push to remote
5. Create pull request (when requested)
```

---

## Git Branch Conventions

### Branch Naming Pattern

**Feature Branches:** `claude/<descriptive-name>-<session-id>`

Examples:
- `claude/add-claude-documentation-X2QHh`
- `claude/implement-combat-system-A1B2C`
- `claude/add-character-creation-D3E4F`

### Commit Message Format

Use conventional commit format:

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks
- `perf`: Performance improvements

**Examples:**
```
feat(combat): implement initiative rolling system

Add initiative calculation based on dexterity modifiers
and d20 rolls. Includes support for advantage/disadvantage.

Closes #123
```

```
fix(character): correct spell slot calculation for multiclass

Spell slots were not being calculated correctly for
multiclass characters. Updated to follow PHB rules.
```

---

## Code Structure Guidelines

### Recommended Project Structure

Since this is a new project, here's a recommended structure to follow:

```
DND_Character_Battle/
├── src/                    # Source code
│   ├── characters/         # Character creation and management
│   ├── combat/            # Combat system and mechanics
│   ├── rules/             # D&D 5e rules engine
│   ├── dice/              # Dice rolling utilities
│   ├── utils/             # General utilities
│   └── index.js/py/etc    # Main entry point
├── tests/                 # Test files (mirror src structure)
│   ├── characters/
│   ├── combat/
│   └── ...
├── docs/                  # Additional documentation
├── data/                  # Game data (spells, items, etc.)
├── config/                # Configuration files
├── .github/               # GitHub workflows (CI/CD)
├── .gitignore            # Git ignore patterns
├── README.md             # User-facing documentation
├── CLAUDE.md             # This file (AI assistant guide)
├── LICENSE               # License information
└── package.json/setup.py # Project dependencies
```

### Language Considerations

The project language hasn't been decided yet. Consider:

- **Python:** Excellent for game logic, data handling, rich ecosystem
- **JavaScript/TypeScript:** Good for web-based tools, interactive UIs
- **Java/C#:** Strong typing, good for complex rule engines
- **Rust:** Performance-critical applications, safety guarantees

When choosing, consider:
- Community preference
- Performance requirements
- Deployment target (CLI, web, desktop)
- Available libraries for D&D mechanics

---

## Development Best Practices

### Code Quality

1. **Keep it Simple:** Avoid over-engineering
2. **YAGNI:** Don't add features you don't need yet
3. **DRY:** Don't repeat yourself, but don't abstract prematurely
4. **Security:** Validate inputs, avoid injection vulnerabilities
5. **Error Handling:** Handle errors gracefully, provide clear messages

### D&D 5e Accuracy

When implementing D&D mechanics:

1. **Follow Official Rules:** Use PHB, DMG, and official errata as source
2. **Document Sources:** Comment which rulebook/page rules come from
3. **Handle Edge Cases:** D&D has many special cases and exceptions
4. **Support Variants:** Consider optional rules (flanking, feats, etc.)

Example:
```python
def calculate_ac(character):
    """
    Calculate Armor Class for a character.

    PHB p.14: AC = 10 + Dex modifier + armor bonus + shield bonus

    Special cases:
    - Barbarian Unarmored Defense: 10 + Dex + Con (PHB p.48)
    - Monk Unarmored Defense: 10 + Dex + Wis (PHB p.78)
    """
    # Implementation
```

### Performance Considerations

- Optimize critical paths (combat simulation loops)
- Cache calculated values when appropriate
- Use efficient data structures
- Profile before optimizing

### Extensibility

Design for extensibility:
- New character classes and subclasses
- Additional races and subraces
- Homebrew content support
- Custom rule variants

---

## Testing Conventions

### Testing Philosophy

1. **Test Coverage:** Aim for >80% coverage on core mechanics
2. **Unit Tests:** Test individual functions and classes
3. **Integration Tests:** Test system interactions
4. **Combat Simulations:** Run full battle simulations as tests

### Test Organization

Mirror source structure in tests:

```
src/combat/initiative.py  →  tests/combat/test_initiative.py
```

### Test Naming

Be descriptive:

```python
def test_initiative_roll_adds_dexterity_modifier():
    # Test implementation

def test_advantage_on_initiative_takes_higher_roll():
    # Test implementation

def test_surprised_creature_cannot_act_in_first_round():
    # Test implementation
```

### Critical Test Areas

Must have comprehensive tests for:
- Dice rolling (probability distributions)
- Attack rolls (advantage, disadvantage, crits)
- Damage calculation
- Spell effects
- Condition tracking
- Action economy

---

## Documentation Standards

### Code Comments

**DO comment:**
- Complex algorithms or non-obvious logic
- D&D rule references (with book and page)
- Edge cases and special handling
- Why decisions were made (not what the code does)

**DON'T comment:**
- Self-explanatory code
- Obvious variable assignments
- Simple getters/setters

### Inline Documentation

Use docstrings/JSDoc for all public functions:

```python
def calculate_damage(attack_roll, damage_dice, damage_modifier, is_crit=False):
    """
    Calculate damage from an attack.

    Args:
        attack_roll (int): The d20 attack roll result
        damage_dice (str): Dice notation (e.g., "2d6", "1d8+3")
        damage_modifier (int): Damage modifier to add
        is_crit (bool): Whether this is a critical hit

    Returns:
        int: Total damage dealt

    References:
        - PHB p.196: Attack Rolls and Damage
        - PHB p.196: Critical Hits (roll damage dice twice)
    """
```

### README.md vs CLAUDE.md

- **README.md:** For human users (setup, usage, features)
- **CLAUDE.md:** For AI assistants (architecture, conventions, context)

Both should be kept up to date, but serve different audiences.

---

## Key Conventions for AI Assistants

### 🤖 When Starting Work

1. **Read First:** Always read existing files before modifying
2. **Check Status:** Understand current project state
3. **Plan:** Use TodoWrite tool for multi-step tasks
4. **Ask Questions:** Use AskUserQuestion when unclear

### 🔍 Understanding Requirements

- Clarify D&D edition (assume 5e unless specified)
- Confirm scope (don't over-implement)
- Validate assumptions about rules
- Check for existing similar functionality

### ✏️ Making Changes

1. **Minimal Changes:** Only modify what's necessary
2. **No Premature Abstraction:** Three uses before abstracting
3. **Security First:** Validate inputs, avoid vulnerabilities
4. **Test As You Go:** Write tests for new functionality
5. **Document Rules:** Reference PHB/DMG page numbers

### 🚫 What NOT to Do

- Don't add features not requested
- Don't refactor code unnecessarily
- Don't add excessive error handling for impossible cases
- Don't create abstractions for single-use code
- Don't add TODOs or placeholder comments
- Don't use emojis in code or commits (unless requested)

### 📝 Commit Practices

**DO:**
- Commit working code
- Write clear commit messages
- Reference issue numbers
- Keep commits focused

**DON'T:**
- Commit broken code
- Make giant commits with unrelated changes
- Commit commented-out code
- Commit sensitive data (.env files, keys)

### 🎯 Task Completion

Mark tasks complete only when:
- ✅ Code is written and tested
- ✅ Tests are passing
- ✅ No compilation/runtime errors
- ✅ Changes are committed
- ✅ Documentation is updated

Don't mark complete if:
- ❌ Tests are failing
- ❌ Implementation is partial
- ❌ Errors remain unresolved
- ❌ Dependencies are missing

### 🧪 Testing Checklist

Before marking work complete:

- [ ] Unit tests written and passing
- [ ] Integration tests pass
- [ ] No regression in existing tests
- [ ] Code coverage maintained/improved
- [ ] Edge cases considered and tested

### 📚 D&D 5e Reference Quick Guide

**Core Rulebooks:**
- PHB: Player's Handbook
- DMG: Dungeon Master's Guide
- MM: Monster Manual
- XGTE: Xanathar's Guide to Everything
- TCOE: Tasha's Cauldron of Everything

**Key Mechanics:**
- Ability Scores: STR, DEX, CON, INT, WIS, CHA (3-20, typically)
- Ability Modifiers: (score - 10) / 2 (rounded down)
- Proficiency Bonus: Based on level (+2 to +6)
- Advantage/Disadvantage: Roll 2d20, take higher/lower
- Attack Roll: d20 + ability modifier + proficiency (if proficient)
- Damage: Roll damage dice, add ability modifier (usually)
- Critical Hit: Natural 20 on attack roll, double damage dice
- Saving Throws: d20 + ability modifier + proficiency (if proficient)
- Spell Attack: d20 + spellcasting ability modifier + proficiency
- Spell DC: 8 + spellcasting ability modifier + proficiency

### 🎲 Dice Notation

Standard dice notation format:
- `1d20`: One twenty-sided die
- `2d6`: Two six-sided dice
- `1d8+3`: One eight-sided die plus 3
- `4d6kh3`: Roll 4d6, keep highest 3 (ability score generation)

### 🔐 Security Considerations

When implementing:
- Validate all user inputs
- Sanitize data before storage/display
- Don't trust client-side validation alone
- Avoid eval() or exec() with user data
- Use parameterized queries (if using database)
- Don't expose internal error details to users

### 🎨 Code Style

Follow established patterns:
- Use consistent naming conventions
- Follow language-specific style guides (PEP 8, Airbnb, etc.)
- Use linting tools (eslint, pylint, etc.)
- Format code consistently (prettier, black, etc.)

Configure these tools in the project root once language is chosen.

---

## Project-Specific Context

### D&D 5e Combat Flow

Understanding combat is essential for this project:

1. **Determine Surprise:** Check if any creatures are surprised
2. **Establish Positions:** Where everyone is at combat start
3. **Roll Initiative:** Each participant rolls d20 + Dex modifier
4. **Take Turns:** In initiative order, each creature takes a turn
   - Movement (up to speed)
   - Action (Attack, Cast Spell, Dash, Dodge, etc.)
   - Bonus Action (if available)
   - Reaction (triggered by specific events)
   - Free Actions (talking, object interaction)
5. **Next Round:** Repeat step 4 until combat ends

### Character Statistics

Key stats to track:
- **Ability Scores:** STR, DEX, CON, INT, WIS, CHA
- **Hit Points:** Current/Max HP
- **Armor Class:** Defensive rating
- **Speed:** Movement per turn
- **Attacks:** Attack bonus, damage dice, damage type
- **Spells:** Known/prepared spells, spell slots
- **Features:** Class/race abilities
- **Equipment:** Weapons, armor, magic items
- **Conditions:** Blinded, charmed, frightened, etc.

### Action Economy

Each turn:
- **1 Action:** Attack, Cast a Spell, Dash, Disengage, Dodge, Help, Hide, Ready, Search, Use an Object
- **1 Bonus Action:** Varies by class/abilities
- **1 Reaction:** Opportunity attack, counterspell, etc.
- **Movement:** Up to speed (can be split)
- **Free Actions:** Drop item, speak briefly

### Common Issues to Anticipate

1. **Multiclassing:** Complex spell slot and feature interactions
2. **Concentration:** Tracking concentration spells and breaking
3. **Conditions:** Multiple conditions with various effects
4. **Saving Throws:** Half damage on success, immunity considerations
5. **Resistance/Vulnerability:** Damage type interactions
6. **Cover:** AC and Dex save bonuses
7. **Flanking:** Optional rule for advantage
8. **Critical Hits:** When to double dice vs when to maximize

---

## Getting Help

### For AI Assistants

If you're unsure about:
- **D&D Rules:** Ask user for clarification or check SRD
- **Implementation Approach:** Use AskUserQuestion tool
- **Project Direction:** Confirm with user before major decisions
- **Existing Code:** Read thoroughly before assuming

### Resources

- **D&D 5e SRD:** Official System Reference Document (free, legal)
- **D&D Basic Rules:** Free PDF from Wizards of the Coast
- **D&D Beyond:** Digital toolset and reference
- **Stack Overflow:** For programming questions
- **GitHub Issues:** For reporting bugs or requesting features

---

## Changelog

### 2026-01-19 - Initial Creation
- Created CLAUDE.md for new repository
- Established development conventions
- Documented git workflow
- Provided D&D 5e context and guidelines
- Set up structure recommendations

---

## Notes for Future Updates

When updating this document:

1. **Keep it current:** Update as the project evolves
2. **Add discoveries:** Document learned conventions and patterns
3. **Include examples:** Real code examples are more helpful than abstract descriptions
4. **Remove obsolete info:** Don't let outdated information linger
5. **Organize clearly:** Use headers and TOC for easy navigation

---

**Remember:** This document exists to help AI assistants work effectively on this project. Keep it practical, accurate, and up-to-date.
