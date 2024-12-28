# RFC-0001: Wave Syntax

> RFC Number: 0001  
> Status: Draft  
> Created: 2024-03-20  
> Authors: [Om Language Team]

## Summary

This RFC proposes the core wave syntax for Om, introducing a natural and intuitive way to express wave operations with explicit unit support and type safety.

## Motivation

### Problem Statement
```typescript
interface WaveProblem {
    current: {
        issue: "No standard way to express wave operations",
        impact: "Inconsistent and error-prone wave programming",
        safety: "Lack of compile-time unit validation"
    };
    
    goals: {
        syntax: "Natural wave expression",
        safety: "Type and unit safety",
        performance: "Efficient compilation"
    };
}
```

### Use Cases
```typescript
// Medical scanning
const medicalCase = {
    scenario: "Ultrasound imaging",
    requirements: {
        frequency: "41.5kHz",
        precision: "high",
        units: "required",
        validation: "strict"
    }
};

// Wave analysis
const analysisCase = {
    scenario: "Brain wave monitoring",
    requirements: {
        realtime: true,
        frequencies: "8-12Hz",  // Alpha waves
        latency: "<1ms"
    }
};
```

## Design

### Core Wave Syntax
```om
// Basic wave creation
const wave~ = wave(41.5kHz);

// Wave operations
const processed~ = wave~
    | phase(45deg)
    | amplitude(0.8)
    | normalize;

// Wave patterns
const pattern~ = [
    wave(41.0kHz),
    wave(41.5kHz),
    wave(42.0kHz)
] | sequence;

// Wave fields
const field~ = Field~.create({
    dimensions: [10, 10],
    wave: wave~
});
```

### Unit System
```om
// Frequency units
type FrequencyUnit = 
    | 'Hz'    // Hertz
    | 'kHz'   // Kilohertz
    | 'MHz'   // Megahertz
    | 'GHz';  // Gigahertz

// Phase units
type PhaseUnit =
    | 'deg'   // Degrees
    | 'rad';  // Radians

// Example usage
const examples~ = {
    frequency: {
        hz: wave(100Hz),
        khz: wave(41.5kHz),
        mhz: wave(2.4MHz)
    },
    phase: {
        degrees: phase(45deg),
        radians: phase(0.785rad)
    }
};
```

### Type System Integration
```om
// Wave type
interface Wave~ {
    frequency: Frequency~;
    phase?: Phase~;
    amplitude?: number;
}

// Pattern type
interface Pattern~ {
    waves: Wave~[];
    relationship: 'sequence' | 'parallel';
}

// Example with type annotations
const typed~: Wave~ = wave(41.5kHz)
    | phase(45deg)
    | amplitude(0.8);
```

### Operation Pipeline
```om
// Pipeline operator
interface PipeOperator {
    syntax: "expression '|' operation";
    chainable: true;
    precedence: "left-to-right";
}

// Example pipeline
const pipeline~ = wave~
    | normalize        // Normalize amplitude
    | phase(90deg)     // Set phase
    | filter(bandpass) // Apply filter
    | analyze;        // Analyze result
```

## Drawbacks

### Potential Issues
```typescript
const drawbacks = {
    learning: "New syntax to learn",
    tooling: "IDE support needed",
    migration: "Converting existing code"
};
```

### Complexity Analysis
```typescript
const complexity = {
    syntax: "Medium - New operators and units",
    implementation: "High - Unit system integration",
    validation: "Medium - Type and unit checking"
};
```

## Alternatives

### Alternative Approaches
```typescript
// Alternative 1: Method chaining
const methodChain = wave(41.5, 'kHz')
    .phase(45, 'deg')
    .amplitude(0.8);

// Alternative 2: Configuration object
const configObject = createWave({
    frequency: { value: 41.5, unit: 'kHz' },
    phase: { value: 45, unit: 'deg' },
    amplitude: 0.8
});

// Alternative 3: Functional composition
const functional = compose(
    setPhase(45, 'deg'),
    setAmplitude(0.8)
)(wave(41.5, 'kHz'));
```

## Adoption

### Migration Strategy
```typescript
interface Migration {
    phases: [
        {
            name: "Preparation",
            tasks: [
                "Update tooling",
                "Convert basic waves",
                "Test conversion"
            ]
        },
        {
            name: "Implementation",
            tasks: [
                "Convert complex patterns",
                "Update libraries",
                "Validate results"
            ]
        }
    ];
}
```

### Backwards Compatibility
```typescript
const compatibility = {
    breaking: true,
    mitigation: "Provide migration tools",
    timeline: "6 months transition"
};
```

## Implementation

### Compiler Changes
```typescript
interface CompilerUpdates {
    parser: {
        unitRecognition: true,
        pipelineSupport: true
    },
    typeChecker: {
        unitValidation: true,
        waveTypeChecking: true
    },
    codeGen: {
        optimizeWaveOps: true,
        validateUnits: true
    }
}
```

### Runtime Support
```typescript
interface RuntimeSupport {
    features: [
        "Unit conversion",
        "Wave optimization",
        "Pattern processing"
    ];
    optimizations: [
        "SIMD operations",
        "Parallel processing",
        "Hardware acceleration"
    ];
}
```

## Documentation

### Examples
```om
// Basic wave creation and processing
async function processWave~() {
    // Create a wave
    const wave~ = wave(41.5kHz);
    
    // Process the wave
    const result~ = await wave~
        | phase(45deg)
        | amplitude(0.8)
        | normalize
        | validate;
        
    return result~;
}

// Pattern creation and analysis
async function analyzePattern~() {
    const pattern~ = [
        wave(41.0kHz),
        wave(41.5kHz),
        wave(42.0kHz)
    ] | sequence | analyze;
    
    return pattern~;
}
```

## Future Possibilities

```typescript
const future = {
    extensions: [
        "Custom unit definitions",
        "Advanced pattern matching",
        "AI-assisted optimization"
    ],
    integrations: [
        "Hardware-specific optimizations",
        "Cloud processing support",
        "Real-time visualization"
    ]
};
```

## See Also

- [Type System RFC](0002-type-system.md)
- [Compiler Pipeline RFC](0003-compiler-pipeline.md)
- [Language Specification](../core/language-overview.md)
