# Om Type Checker

> Version: 0.1.0 (Draft)  
> Status: Proposal Stage

## Overview

The Om type checker ensures type safety with a focus on wave operations, unit compatibility, and AI-assisted type inference.

## Type Checking Process

```typescript
interface TypeChecker {
    // Main type checking pipeline
    check(ast: Program): TypedProgram {
        return {
            validateUnits(),
            inferTypes(),
            checkWaveOperations(),
            validatePatterns()
        }
    }
}
```

## Wave Type System

### Basic Wave Types
```typescript
// Core wave type
interface Wave~ {
    frequency: Frequency~;
    phase?: Phase~;
    amplitude?: number;
    metadata?: WaveMetadata~;
}

// Frequency type with units
interface Frequency~ {
    value: number;
    unit: 'Hz' | 'kHz' | 'MHz' | 'GHz';
}

// Phase type with units
interface Phase~ {
    value: number;
    unit: 'deg' | 'rad';
}
```

### Pattern Types
```typescript
// Wave pattern type
interface Pattern~ {
    waves: Wave~[];
    relationship: PatternRelationship~;
}

type PatternRelationship~ = {
    type: 'sequence' | 'parallel' | 'matrix';
    parameters?: PatternParameters~;
}
```

## Type Inference

### AI-Assisted Inference
```typescript
interface TypeInference {
    // Context-aware type inference
    inferTypes(node: Node): TypeInfo {
        return {
            analyzeContext(),
            suggestTypes(),
            validateSuggestions()
        }
    }
}

// Example usage
const wave = oscillate(41.5kHz)  
// AI infers: Wave~ type based on medical context
```

### Unit Compatibility
```typescript
interface UnitChecker {
    // Check unit compatibility
    checkUnits(operation: WaveOperation): boolean {
        switch (operation.type) {
            case 'frequency':
                return validateFrequencyUnit(operation);
            case 'phase':
                return validatePhaseUnit(operation);
            // ...
        }
    }
}

// Example validation
wave~ | phase(45)      // Error: Missing phase unit
wave~ | phase(45deg)   // Valid: Explicit phase unit
```

## Error Handling

### Type Errors
```typescript
interface TypeError~ {
    kind: TypeErrorKind;
    message: string;
    location: SourceLocation;
    suggestions: string[];
}

type TypeErrorKind = 
    | 'UnitMismatch'
    | 'InvalidWaveOperation'
    | 'PatternMismatch'
    | 'MissingUnit';

// Example error
const error: TypeError~ = {
    kind: 'MissingUnit',
    message: 'Phase angle must specify unit (deg or rad)',
    location: { line: 10, column: 15 },
    suggestions: [
        'Add "deg" for degrees: phase(45deg)',
        'Add "rad" for radians: phase(0.785rad)'
    ]
}
```

## Progressive Type Checking

### Basic to Advanced
```typescript
// Level 1: Basic type checking
const basic~ = wave(41.5kHz);

// Level 2: With type annotations
const typed~: Wave~ = wave(41.5kHz);

// Level 3: Full type specification
const detailed~: MedicalWave~ = wave({
    frequency: 41.5kHz,
    phase: 0deg,
    amplitude: 0.8,
    metadata: {
        context: 'medical',
        validation: 'strict'
    }
});
```

## Type Safety Features

### Unit Safety
```typescript
// Unit conversion safety
function convertPhase(
    value: number, 
    from: PhaseUnit, 
    to: PhaseUnit
): Phase~ {
    // Safe unit conversion
    if (from === to) return { value, unit: to };
    
    if (from === 'deg' && to === 'rad') {
        return {
            value: value * Math.PI / 180,
            unit: 'rad'
        };
    }
    // ...
}
```

### Pattern Validation
```typescript
interface PatternValidator {
    // Validate wave patterns
    validatePattern(pattern: Pattern~): ValidationResult {
        return {
            checkWaveCompatibility(),
            validateRelationships(),
            ensureUnitConsistency()
        }
    }
}
```

## Implementation Notes

1. **Type Checking Strategy**
```typescript
class TypeCheckingPipeline {
    stages = [
        this.parseTypes,
        this.inferMissingTypes,
        this.validateUnits,
        this.checkOperations,
        this.validatePatterns
    ];

    async check(ast: Program) {
        for (const stage of this.stages) {
            await stage(ast);
        }
    }
}
```

2. **AI Integration**
```typescript
interface AITypeAssistant {
    suggestTypes(context: TypeContext): TypeSuggestion[];
    validateOperations(ops: WaveOperation[]): ValidationResult;
    inferMissingUnits(expr: Expression): UnitSuggestion[];
}
```

## See Also

- [Semantic Analysis](semantic.md)
- [Code Generation](../generator/code-gen.md)
- [Wave Engine](../runtime/wave-engine.md)
