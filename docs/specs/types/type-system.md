# Om Type System

> Version: 0.1.0 (Draft)  
> Status: Proposal Stage

## Introduction

Om's type system is designed to support wave-native computing with gradual typing and AI assistance. It combines the flexibility of dynamic typing with the safety of static typing, enabling progressive enhancement of code quality.

## Core Types

### Wave Types
```om
// Basic wave type
type Wave~ = {
    frequency: Frequency~,
    phase: Angle~,
    amplitude: Number~
}

// Frequency type with units
type Frequency~ = {
    value: Number~,
    unit: 'Hz' | 'kHz' | 'MHz' | 'GHz'
}

// Angle type for phases
type Angle~ = {
    value: Number~,
    unit: '°'  // Degree symbol required
}
```

### Pattern Types
```om
// Wave pattern type
type Pattern~ = {
    waves: Wave~[],
    relationship: 'sequence' | 'parallel' | 'matrix'
}

// Field type for complex wave interactions
type Field~ = {
    dimensions: [number, number],
    waves: Wave~[],
    interference: InterferencePattern~
}
```

## Gradual Typing

### Progressive Type Enhancement
```om
// 1. Start with dynamic typing
let wave = oscillate(41.5kHz)

// 2. Add basic type annotation
let wave: Wave~ = oscillate(41.5kHz)

// 3. Add full type specification
let wave: Wave~ = oscillate({
    frequency: 41.5kHz,
    phase: 0°,
    amplitude: 1.0
})
```

### Type Inference
```om
// Automatic type inference
const medical~ = {
    scan: wave(41.5kHz),        // Inferred as Wave~
    pattern: [0°, 45°, 90°],    // Inferred as Angle~[]
    power: 0.5                  // Inferred as Number~
}

// AI-assisted type suggestions
const signal = measure(frequency)
// AI suggests: Consider adding Wave~ type for medical context
```

## Unit Types

### Frequency Units
```om
// Strict unit typing
type FrequencyUnit~ = 'Hz' | 'kHz' | 'MHz' | 'GHz'

// Unit validation
const validate~ = (freq: Frequency~) => {
    if (!isValidUnit(freq.unit)) {
        throw new TypeError(`Invalid frequency unit: ${freq.unit}`)
    }
}
```

### Measurement Units
```om
// Physical measurement types
type Power~ = {
    value: Number~,
    unit: 'mW' | 'W'
}

type Duration~ = {
    value: Number~,
    unit: 'ms' | 's' | 'min'
}
```

## Generic Wave Operations

### Type-Safe Operations
```om
// Generic wave transformation
type WaveTransform~<T extends Wave~> = (wave: T) => T

// Type-safe pipe operations
const process~ = <T extends Wave~>(wave: T): T => {
    return wave
        | normalize
        | optimize
}
```

### Pattern Matching Types
```om
// Pattern matching with type preservation
type Matcher~<T extends Pattern~> = {
    pattern: T,
    threshold: Number~,
    callback: (match: T) => void
}

// Type-safe pattern matching
const match~<T extends Pattern~>(
    signal: Wave~,
    matcher: Matcher~<T>
): boolean
```

## AI Collaboration Features

### Type Suggestions
```om
// AI provides context-aware type suggestions
const scan = (input) => {
    // AI suggests:
    // 1. input: Wave~ for medical scanning
    // 2. Return type: ScanResult~
    return measure(input)
}

// AI-enhanced version
const scan~ = (input: Wave~): ScanResult~ => {
    return measure(input)
        | validate
        | optimize
}
```

### Progressive Enhancement
```om
// AI helps refine types based on usage
const process = {
    input: wave(41.5kHz),
    // AI suggests: Add type annotations based on medical context
}

// Enhanced version
const process: MedicalProcess~ = {
    input: wave(41.5kHz),
    frequency: 41.5kHz,
    duration: 5min,
    power: 0.5mW
}
```

## Error Handling

### Type Errors
```om
// Type-safe error handling
type WaveError~ = {
    type: 'frequency' | 'phase' | 'amplitude',
    message: string,
    context: Wave~
}

try~ {
    const result~ = process(wave~)
} catch~ (error: WaveError~) {
    console.error(`Wave error: ${error.message}`)
}
```

## Best Practices

1. **Progressive Typing**
   - Start simple
   - Add types gradually
   - Use AI suggestions

2. **Unit Safety**
   - Always specify units
   - Use type-safe unit conversions
   - Validate unit combinations

3. **Pattern Types**
   - Define clear pattern structures
   - Use generic constraints
   - Preserve type information

4. **AI Collaboration**
   - Accept AI type suggestions
   - Review context-aware enhancements
   - Document type decisions

## Implementation Notes

The type system is implemented with:
- Gradual typing support
- AI-assisted type inference
- Runtime type checking
- Unit validation

## See Also

- [Language Overview](../core/language-overview.md)
- [Wave Computing](../core/wave-computing.md)
- [Basic Patterns](../examples/basic-patterns.md)
