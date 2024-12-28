# RFC-0002: Type System

> RFC Number: 0002  
> Status: Draft  
> Created: 2024-03-20  
> Authors: [Om Language Team]

## Summary

This RFC proposes Om's type system, featuring wave-native types, gradual typing, and AI-assisted type inference with a focus on unit safety and wave operations.

## Motivation

### Problem Statement
```typescript
interface TypeSystemNeeds {
    current: {
        issue: "Lack of wave-specific type safety",
        impact: "Runtime errors in wave operations",
        cost: "Debugging complex wave interactions"
    };
    
    goals: {
        safety: "Compile-time wave validation",
        flexibility: "Gradual typing support",
        inference: "AI-assisted type detection"
    };
}
```

### Use Cases
```typescript
// Medical device safety
const medicalTypes = {
    scenario: "Medical imaging",
    requirements: {
        typeChecking: "strict",
        unitValidation: "required",
        safetyChecks: "compile-time"
    }
};

// Research applications
const researchTypes = {
    scenario: "Wave pattern research",
    requirements: {
        flexibility: "gradual typing",
        inference: "AI-assisted",
        extensibility: "custom types"
    }
};
```

## Design

### Core Types
```om
// Basic wave type
type Wave~ = {
    frequency: Frequency~;
    phase?: Phase~;
    amplitude?: number;
    metadata?: WaveMetadata~;
};

// Unit-aware types
type Frequency~ = {
    value: number;
    unit: FrequencyUnit;
};

type Phase~ = {
    value: number;
    unit: PhaseUnit;
};

// Pattern types
type Pattern~ = {
    waves: Wave~[];
    relationship: PatternType;
    metadata?: PatternMetadata~;
};

// Field types
type Field~ = {
    dimensions: [number, number];
    waves: Wave~[];
    boundary: BoundaryCondition;
};
```

### Type Inference
```om
// AI-assisted type inference
interface TypeInference {
    // Context detection
    context: {
        domain: "medical" | "research" | "industrial";
        requirements: TypeRequirement[];
        constraints: TypeConstraint[];
    };

    // Type suggestions
    suggest(code: string): TypeSuggestion {
        return {
            inferredType: detectType(code),
            confidence: calculateConfidence(),
            alternatives: findAlternatives()
        };
    }
}

// Example inference
const wave~ = wave(41.5kHz);  // Type: Wave~
const pattern~ = [wave~, wave~];  // Type: Pattern~
const field~ = Field~.create({/*...*/});  // Type: Field~
```

### Gradual Typing
```om
// Optional type annotations
function process(wave: Wave~): Result~;  // Fully typed
function analyze(wave~);  // Inferred return type
function compute(data);  // Dynamic typing

// Type gradience
const examples = {
    strict: (wave: Wave~): Phase~ => {
        return wave.phase;
    },
    
    flexible: (wave~) => {
        return wave.phase;  // Inferred Phase~
    },
    
    dynamic: (wave) => {
        return wave.phase;  // Dynamic
    }
};
```

### Unit Safety
```om
// Unit-safe operations
interface UnitSafety {
    // Frequency operations
    frequency: {
        convert(value: number, from: FrequencyUnit, to: FrequencyUnit): number;
        validate(frequency: Frequency~): boolean;
    };

    // Phase operations
    phase: {
        convert(value: number, from: PhaseUnit, to: PhaseUnit): number;
        normalize(phase: Phase~): Phase~;
    };
}

// Example usage
const safeWave~ = wave(41.5kHz)
    | phase(45deg)      // Unit checked
    | frequency(2MHz);  // Unit conversion
```

### Type Composition
```om
// Type composition
type CompositeWave~ = Wave~ & {
    metadata: WaveMetadata~;
};

type WavePattern~ = {
    base: Wave~;
    variations: Wave~[];
    composition: CompositionType;
};

// Generic wave types
type ProcessedWave~<T extends ProcessingConfig> = {
    base: Wave~;
    processing: T;
    result: ProcessingResult~;
};
```

## Implementation

### Type Checker
```typescript
interface TypeChecker {
    // Type checking pipeline
    check(ast: AST): TypedAST {
        return pipeline([
            inferTypes,
            validateUnits,
            checkOperations,
            validatePatterns
        ]);
    }
}

// Example implementation
class WaveTypeChecker implements TypeChecker {
    inferTypes(node: ASTNode): TypeInfo {
        if (isWaveOperation(node)) {
            return this.inferWaveType(node);
        }
        return this.inferGenericType(node);
    }
}
```

### Error Handling
```typescript
interface TypeError~ {
    kind: TypeErrorKind;
    message: string;
    location: SourceLocation;
    suggestions: string[];
}

// Example errors
const errors = {
    unitMismatch: new TypeError~({
        kind: "UnitMismatch",
        message: "Cannot mix Hz with kHz",
        suggestions: ["Convert to same unit"]
    }),
    
    typeMismatch: new TypeError~({
        kind: "TypeMismatch",
        message: "Expected Wave~, got Pattern~",
        suggestions: ["Extract wave from pattern"]
    })
};
```

## Migration Strategy

### Adoption Path
```typescript
interface Migration {
    phases: [
        {
            name: "Basic Types",
            tasks: [
                "Add Wave~ annotations",
                "Enable unit checking",
                "Update existing code"
            ]
        },
        {
            name: "Advanced Features",
            tasks: [
                "Add pattern types",
                "Enable type inference",
                "Optimize type checking"
            ]
        }
    ];
}
```

### Compatibility
```typescript
const compatibility = {
    typescript: {
        interop: true,
        declarations: "Generated",
        tooling: "VSCode support"
    },
    javascript: {
        gradual: true,
        runtime: "Type checking optional",
        migration: "Progressive"
    }
};
```

## Future Possibilities

```typescript
const future = {
    features: [
        "Dependent types for wave relationships",
        "Effect system for wave operations",
        "Refinement types for constraints"
    ],
    tooling: [
        "Advanced type inference",
        "Interactive type exploration",
        "Automated migration tools"
    ],
    integration: [
        "Hardware-specific types",
        "Domain-specific extensions",
        "Framework integrations"
    ]
};
```

## See Also

- [Wave Syntax RFC](0001-wave-syntax.md)
- [Compiler Pipeline RFC](0003-compiler-pipeline.md)
- [Type System Specification](../compiler/analyzer/type-checker.md)
