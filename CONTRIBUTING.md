# Contributing to Om

> Version: 0.1.0 (Draft)  
> Status: Proposal Stage

## Introduction

Thank you for considering contributing to Om! This document provides guidelines and best practices for contributing to the Om programming language and its ecosystem.

## Code of Conduct

### Our Standards
```typescript
interface CommunityStandards {
    behavior: [
        "Be respectful and inclusive",
        "Focus on constructive feedback",
        "Help others learn and grow",
        "Maintain professional discourse"
    ];
}
```

## Getting Started

### Development Setup
```bash
# Clone the repository
git clone https://github.com/univault-org/om-lang.git
cd om-lang

# Using pnpm (preferred)
pnpm install
pnpm test
pnpm run build

# Or using npm
npm install
npm test
npm run build

# Package manager consistency
# We include both package-lock.json and pnpm-lock.yaml
# Please use the same package manager you started with
```

### Package Manager Notes
```typescript
interface PackageManagers {
    preferred: "pnpm",  // Faster and more efficient
    supported: [
        "pnpm",
        "npm"
    ],
    lockFiles: [
        "pnpm-lock.yaml",
        "package-lock.json"
    ]
}
```

### Project Structure
```typescript
interface ProjectStructure {
    src: {
        compiler: "Compiler source code",
        runtime: "Runtime engine",
        tools: "Development tools"
    },
    docs: {
        specs: "Language specifications",
        examples: "Code examples",
        rfcs: "RFCs"
    },
    tests: {
        unit: "Unit tests",
        integration: "Integration tests",
        benchmarks: "Performance tests"
    }
}
```

## Making Contributions

### Types of Contributions
```typescript
type Contribution =
    | "Bug fixes"
    | "Feature implementations"
    | "Documentation improvements"
    | "Performance optimizations"
    | "Test coverage"
    | "RFCs";
```

### Contribution Process
```typescript
interface ContributionProcess {
    steps: [
        "Fork repository",
        "Create feature branch",
        "Make changes",
        "Write tests",
        "Update docs",
        "Submit PR"
    ];
}
```

## Development Guidelines

### Code Style
```typescript
// Wave operation style
const goodStyle~ = wave(41.5kHz)
    | phase(45deg)     // Clear operation
    | amplitude(0.8)   // With units
    | normalize;       // Single responsibility

// Avoid
const badStyle~ = wave(41.5)  // Missing units
    |phase(45)               // Inconsistent spacing
    |amplitude(0.8)|norm;   // Cluttered
```

### Testing Requirements
```typescript
interface TestRequirements {
    unit: {
        coverage: "90% minimum",
        style: "BDD with clear descriptions",
        performance: "Include benchmarks"
    };
    
    integration: {
        scenarios: "Real-world use cases",
        compatibility: "Cross-platform",
        performance: "Benchmark critical paths"
    };
}
```

### Documentation
```typescript
// Good documentation
/**
 * Processes a wave pattern with specified parameters.
 * 
 * @param wave~ - Input wave (41.5kHz medical standard)
 * @param options - Processing options
 * @returns Processed wave pattern
 * @throws WaveError~ if frequency is invalid
 */
async function processWave~(
    wave~: Wave~,
    options: ProcessOptions~
): Promise<Pattern~> {
    // Implementation
}
```

## Submitting Changes

### Pull Request Process
```typescript
interface PRProcess {
    preparation: [
        "Update documentation",
        "Add/update tests",
        "Run full test suite",
        "Update changelog"
    ];
    
    review: [
        "Address feedback",
        "Keep discussions focused",
        "Update as needed",
        "Maintain clean history"
    ];
}
```

### Commit Messages
```bash
# Good commit messages
feat(compiler): Add wave pattern optimization
fix(runtime): Correct phase calculation in medical context
docs(examples): Add advanced wave processing patterns
test(integration): Add medical scanning scenarios

# Avoid
fix stuff
update code
WIP
```

## Review Process

### Code Review Guidelines
```typescript
interface ReviewGuidelines {
    focus: [
        "Correctness",
        "Performance",
        "Safety",
        "Clarity",
        "Documentation"
    ];
    
    feedback: [
        "Be constructive",
        "Explain rationale",
        "Suggest improvements",
        "Share knowledge"
    ];
}
```

## Release Process

### Version Control
```typescript
interface VersionControl {
    major: "Breaking changes";
    minor: "New features";
    patch: "Bug fixes";
    
    branches: {
        main: "Stable releases",
        develop: "Integration branch",
        feature: "New features",
        release: "Release preparation"
    };
}
```

## Community

### Getting Help
```typescript
interface Help {
    channels: {
        discord: "Real-time chat",
        github: "Issues and discussions",
        forum: "Long-form discussions",
        stackoverflow: "Q&A"
    };
}
```

### Recognition
```typescript
interface Recognition {
    contributors: "All contributors listed",
    acknowledgments: "In release notes",
    awards: "Community recognition"
}
```

## Additional Resources

- [Development Setup Guide](docs/development-setup.md)
- [Coding Standards](docs/coding-standards.md)
- [Testing Guide](docs/testing-guide.md)
- [RFC Process](docs/specs/rfcs/README.md)

## Questions?

If you have questions about contributing, please:
1. Check existing issues
2. Read the documentation
3. Ask in community channels
4. Create a new issue if needed
