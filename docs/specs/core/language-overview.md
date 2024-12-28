# Om Language Overview

> Version: 0.1.0 (Draft)  
> Status: Proposal Stage

## Introduction

Om is a wave-native programming language designed for bio-field computing and AI collaboration. This document outlines the core language features and syntax.

## Basic Syntax

### Wave Expressions
```om
// Basic wave creation
const wave~ = oscillate(41.5kHz)

// Wave operations using pipe syntax
const modified~ = wave~
    | phase(45°)
    | amplitude(0.8)
    | optimize
```

### Units and Scientific Notation
```om
// Frequency units
const frequencies~ = {
    brain: 13Hz,
    medical: 41.5kHz,
    imaging: 1MHz
}

// Phase angles
const phases~ = {
    quarter: 45°,    // Degree symbol required
    half: 180°,
    full: 360°
}
```

### Wave-Native Types
```om
// Wave type declaration
const signal~: Wave~ = oscillate(41.5kHz)

// Pattern type for multiple waves
const pattern~: Pattern~ = [
    oscillate(40kHz),
    oscillate(41.5kHz),
    oscillate(43kHz)
]

// Field type for complex wave interactions
const field~: Field~ = pattern~
    | combine
    | normalize
```

## Program Structure

### Modules
```om
// Importing wave patterns
import { medicalScan~ } from 'medical'
import { brainWave~ } from 'neural'

// Exporting wave operations
export const analyze~ = (wave~: Wave~): Analysis~ => {
    return wave~
        | measure
        | optimize
}
```

### Functions and Operations
```om
// Wave function declaration
function process~(input~: Wave~) {
    return input~
        | normalize
        | validate
}

// Arrow function syntax
const filter~ = (wave~: Wave~) => wave~
    | frequency(41.5kHz)
    | phase(0°)
```

## AI Collaboration Features

### Type Inference
```om
// AI assists with type inference
const wave = oscillate(41.5)  
// AI suggests: "Add unit kHz for medical scanning"
// AI suggests: "Add Wave~ type annotation"

// Corrected version
const wave~: Wave~ = oscillate(41.5kHz)
```

### Progressive Enhancement
```om
// Basic version
function scan(frequency) {
    return measure(frequency)
}

// AI-enhanced version
/**
 * Performs medical frequency scan
 * @param frequency {Frequency~} Input frequency
 * @returns {ScanResult~} Scan results
 */
function scan~(frequency: Frequency~): ScanResult~ {
    return measure(frequency)
        | validate
        | optimize
}
```

## Error Handling

```om
// Wave operation error handling
try~ {
    const result~ = wave~
        | measure
        | validate
} catch~ (error: WaveError~) {
    console.error(`Wave error: ${error.message}`)
}
```

## Best Practices

1. **Unit Specification**
   - Always specify units for frequencies
   - Use standard unit notation (Hz, kHz, MHz)
   - Include degree symbol (°) for phases

2. **Type Annotations**
   - Use wave-native types where appropriate
   - Allow AI to suggest type improvements
   - Add types progressively as code matures

3. **Wave Operations**
   - Use pipe syntax for clarity
   - Chain operations logically
   - Include validation steps

4. **Documentation**
   - Document frequency ranges
   - Specify expected patterns
   - Include usage examples

## Implementation Notes

This specification is implemented with:
- Progressive type system
- AI-assisted development
- Real-time validation
- Wave-native optimizations

## See Also

- [Wave Computing Model](wave-computing.md)
- [Type System](../types/type-system.md)
- [Basic Patterns](../examples/basic-patterns.md)
