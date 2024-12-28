# RFC Template: [Feature Name]

> RFC Number: XXXX  
> Status: Draft  
> Created: [YYYY-MM-DD]  
> Authors: [Author Names]

## Summary

[One paragraph explanation of the feature.]

## Motivation

### Problem Statement
```typescript
interface Problem {
    current: "What's wrong with the current situation?";
    impact: "Who is affected and how?";
    urgency: "Why is this important now?";
}
```

### Use Cases
```typescript
// Example use cases
const useCases = [
    {
        scenario: "Medical scanning",
        requirements: {
            frequency: "41.5kHz",
            precision: "high",
            safety: "critical"
        }
    },
    {
        scenario: "Wave pattern analysis",
        requirements: {
            realtime: true,
            accuracy: "99.9%",
            latency: "<1ms"
        }
    }
];
```

## Design

### Overview
```typescript
interface Design {
    principles: string[];
    constraints: Constraints;
    components: Component[];
    interfaces: Interface[];
}
```

### Syntax Examples
```om
// Before (if applicable)
const before = wave(41.5kHz);

// After (proposed)
const after~ = wave(41.5kHz)
    | optimize
    | validate;
```

### Technical Details
```typescript
// Implementation details
interface Implementation {
    compiler: {
        changes: string[];
        impact: Impact;
    };
    runtime: {
        changes: string[];
        performance: Performance;
    };
}
```

## Drawbacks

### Potential Issues
```typescript
interface Drawbacks {
    compatibility: string[];
    complexity: string[];
    performance: string[];
    maintenance: string[];
}
```

### Risk Analysis
```typescript
const risks = {
    high: [
        "Breaking changes",
        "Performance impact"
    ],
    medium: [
        "Learning curve",
        "Migration effort"
    ],
    low: [
        "Documentation updates",
        "Tool changes"
    ]
};
```

## Alternatives

### Option Analysis
```typescript
interface Alternative {
    approach: string;
    pros: string[];
    cons: string[];
    tradeoffs: Tradeoff[];
}

const alternatives: Alternative[] = [
    {
        approach: "Alternative 1",
        pros: ["Simpler", "Faster"],
        cons: ["Less flexible", "Limited scope"]
    },
    // More alternatives...
];
```

## Adoption

### Migration Strategy
```typescript
interface Migration {
    steps: {
        preparation: string[];
        execution: string[];
        verification: string[];
    };
    timeline: Timeline;
    support: Support;
}
```

### Backwards Compatibility
```typescript
interface Compatibility {
    breaking: boolean;
    mitigations: string[];
    timeline: string;
}
```

## Implementation

### Development Phases
```typescript
const phases = {
    phase1: {
        description: "Core implementation",
        tasks: string[],
        timeline: string
    },
    phase2: {
        description: "Testing and validation",
        tasks: string[],
        timeline: string
    },
    phase3: {
        description: "Documentation and release",
        tasks: string[],
        timeline: string
    }
};
```

### Testing Strategy
```typescript
interface Testing {
    unit: TestSuite[];
    integration: TestSuite[];
    performance: Benchmark[];
    acceptance: Criteria[];
}
```

## Documentation

### Required Updates
```typescript
interface Documentation {
    specs: string[];
    guides: string[];
    examples: string[];
    tutorials: string[];
}
```

### Example Documentation
```om
/**
 * Example usage documentation
 */
async function example~() {
    // Show how to use the new feature
    const result~ = await someNewFeature({
        // Configuration
    });
    
    // Explain the results
    return result~;
}
```

## Unresolved Questions

```typescript
interface OpenQuestions {
    design: string[];
    implementation: string[];
    adoption: string[];
}
```

## Future Possibilities

```typescript
interface FuturePossibilities {
    enhancements: string[];
    extensions: string[];
    integrations: string[];
}
```

## Appendix

### References
```typescript
interface References {
    specs: string[];
    research: string[];
    related: string[];
}
```

### Feedback
```typescript
interface Feedback {
    channel: string;
    process: string;
    timeline: string;
}
```
