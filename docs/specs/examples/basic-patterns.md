# Om Basic Patterns

> Version: 0.1.0 (Draft)  
> Status: Proposal Stage

## Introduction

This document provides common patterns and examples for Om-lang programming, focusing on practical applications and best practices.

## Medical Scanning Patterns

### Basic Medical Scan
```om
// Standard medical scanning frequency
const basicScan~ = () => {
    const wave~ = oscillate(41.5kHz)
        | amplitude(0.5)
        | validate

    return wave~
        | measure
        | analyze
}

// With error handling
const safeScan~ = async () => {
    try~ {
        const result~ = await basicScan~()
        return result~ | optimize
    } catch~ (error: WaveError~) {
        console.error(`Scan error: ${error.message}`)
        return null
    }
}
```

### Pattern Matching
```om
// Define medical pattern
const medicalPattern~: Pattern~ = {
    base: wave(41.5kHz),
    variations: [
        wave(41.0kHz),
        wave(42.0kHz)
    ],
    threshold: 0.9
}

// Pattern matching function
const matchPattern~ = (signal~: Wave~) => {
    return signal~
        | normalize
        | match(medicalPattern~)
        | validate
}
```

## Brain Wave Analysis

### Alpha Wave Detection
```om
// Alpha wave frequency range (8-12 Hz)
const alphaWave~ = {
    range: 8Hz to 12Hz,
    baseline: wave(10Hz),
    threshold: 0.8
}

// Alpha detection
const detectAlpha~ = (input~: Wave~): boolean => {
    return input~
        | filterRange(alphaWave~.range)
        | match(alphaWave~.baseline)
        | threshold(alphaWave~.threshold)
}
```

### Multi-Band Analysis
```om
// Brain wave bands
const brainWaves~ = {
    delta: 0.5Hz to 4Hz,
    theta: 4Hz to 8Hz,
    alpha: 8Hz to 12Hz,
    beta: 12Hz to 30Hz
}

// Analyze all bands
const analyzeBrain~ = (signal~: Wave~) => {
    return Object.entries(brainWaves~)
        .map(([band, range]) => ({
            band,
            power: signal~
                | filterRange(range)
                | power
                | normalize
        }))
}
```

## Wave Field Patterns

### 2D Field Generation
```om
// Create 2D wave field
const createField~ = (
    dimensions: [number, number],
    frequency: Frequency~
): Field~ => {
    return Field~.create({
        dimensions,
        wave: wave(frequency),
        interference: 'constructive'
    })
}

// Field manipulation
const processField~ = (field~: Field~) => {
    return field~
        | partition(8)      // Split for parallel processing
        | map(normalize)    // Normalize each partition
        | combine          // Merge results
        | validate        // Ensure quality
}
```

### Interference Patterns
```om
// Create interference pattern
const interference~ = (
    wave1~: Wave~,
    wave2~: Wave~
): Pattern~ => {
    return [wave1~, wave2~]
        | combine
        | analyze
        | visualize
}

// Complex interference
const complexPattern~ = (waves~: Wave~[]): Field~ => {
    return waves~
        | distribute2D([10, 10])
        | interference('matrix')
        | optimize
}
```

## Real-time Processing

### Stream Processing
```om
// Create real-time stream
const stream~ = Stream~.create({
    frequency: 41.5kHz,
    buffer: 1024,
    mode: 'realtime'
})

// Process stream
stream~.process(wave~ => {
    wave~
        | filter(bandpass(40kHz, 43kHz))
        | analyze
        | match(medicalPattern~)
        | alert.if(matched)
})
```

### Adaptive Filtering
```om
// Adaptive filter
const adaptiveFilter~ = (target~: Wave~) => {
    let state~ = initialize()

    return (input~: Wave~) => {
        state~ = state~
            | update(input~)
            | optimize

        return input~
            | filter(state~)
            | match(target~)
    }
}
```

## Best Practices

### Error Handling
```om
// Robust error handling
const robustScan~ = async (frequency: Frequency~) => {
    try~ {
        // Validate input
        if (!isValidFrequency(frequency)) {
            throw new WaveError~('Invalid frequency')
        }

        // Process with timeout
        const result~ = await timeout(5s, 
            measure(wave(frequency))
        )

        return result~ | validate
    } catch~ (error: WaveError~) {
        logError(error)
        return fallback~
    }
}
```

### Resource Management
```om
// Clean resource handling
const withWave~ = async (
    frequency: Frequency~,
    operation: (wave: Wave~) => Promise<Result~>
) => {
    const wave~ = create(frequency)
    try~ {
        return await operation(wave~)
    } finally {
        wave~.dispose()
    }
}
```

## Implementation Notes

These patterns are designed to be:
- Efficient
- Type-safe
- Easy to understand
- Maintainable

## See Also

- [Advanced Patterns](advanced-patterns.md)
- [Language Overview](../core/language-overview.md)
- [Wave Computing](../core/wave-computing.md)
- [Type System](../types/type-system.md)
