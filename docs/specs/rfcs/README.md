# Om Language RFCs (Requests for Comments)

> Version: 0.1.0 (Draft)  
> Status: Proposal Stage

## Overview

The Om RFC process is designed to provide a consistent path for new features to enter the language, ensuring proper discussion and documentation of design decisions.

## RFC Process

### 1. RFC Lifecycle
```typescript
interface RFCState {
    states: {
        draft: "Initial proposal",
        review: "Open for community feedback",
        accepted: "Approved for implementation",
        implemented: "Feature is live",
        withdrawn: "Proposal withdrawn"
    }
}
```

### 2. RFC Structure
```typescript
interface RFC {
    metadata: {
        number: number;        // RFC number
        title: string;        // RFC title
        author: string[];     // RFC authors
        status: RFCState;     // Current state
        created: Date;        // Creation date
        updated?: Date;       // Last update
    };
    
    sections: {
        summary: string;      // Brief overview
        motivation: string;   // Why is this needed
        design: string;       // Proposed design
        drawbacks: string;    // Potential issues
        alternatives: string; // Other approaches
        adoption: string;     // Migration strategy
    };
}
```

## Creating an RFC

### 1. File Naming
```bash
# Format: ####-feature-name.md
0001-wave-syntax.md
0002-type-system.md
0003-compiler-pipeline.md
```

### 2. Template Usage
```markdown
# RFC-XXXX: Title

## Summary
Brief explanation of the feature.

## Motivation
Why are we doing this?

## Design
Detailed design explanation.

## Drawbacks
Potential issues to consider.

## Alternatives
Other approaches considered.

## Adoption
How will users adopt this?
```

## Review Process

### 1. Submission
```typescript
interface RFCSubmission {
    // Submit new RFC
    submit(): Promise<RFC> {
        return {
            validateFormat(),
            assignNumber(),
            initiateReview(),
            notifyReviewers()
        };
    }
}
```

### 2. Review Phases
```typescript
interface ReviewProcess {
    phases: {
        initial: "Core team review",
        public: "Community feedback",
        final: "Decision making"
    };

    // Review timeframes
    timeframes: {
        initial: "1 week",
        public: "2 weeks",
        final: "1 week"
    };
}
```

## Implementation

### 1. After Acceptance
```typescript
interface RFCImplementation {
    // Implementation steps
    implement(): Promise<void> {
        return {
            createBranch(),
            implementFeature(),
            addTests(),
            updateDocs(),
            submitPR()
        };
    }
}
```

### 2. Documentation
```typescript
interface RFCDocs {
    // Required documentation
    documents: {
        spec: "Technical specification",
        guide: "User guide",
        examples: "Usage examples",
        tests: "Test cases"
    };
}
```

## Current RFCs

### Active RFCs
```typescript
const activeRFCs = [
    {
        number: "0001",
        title: "Wave Syntax",
        status: "review",
        url: "./0001-wave-syntax.md"
    },
    {
        number: "0002",
        title: "Type System",
        status: "draft",
        url: "./0002-type-system.md"
    },
    {
        number: "0003",
        title: "Compiler Pipeline",
        status: "draft",
        url: "./0003-compiler-pipeline.md"
    }
];
```

## Best Practices

### 1. Writing RFCs
```markdown
- Be specific and detailed
- Include code examples
- Consider edge cases
- Address backwards compatibility
- Provide migration paths
```

### 2. Review Guidelines
```markdown
- Focus on technical merit
- Consider implementation complexity
- Evaluate user impact
- Check compatibility
- Assess maintenance burden
```

## See Also

- [RFC Template](template.md)
- [Wave Syntax RFC](0001-wave-syntax.md)
- [Type System RFC](0002-type-system.md)
- [Compiler Pipeline RFC](0003-compiler-pipeline.md)
