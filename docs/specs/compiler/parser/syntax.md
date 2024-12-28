# Om Language Syntax Specification

> Version: 0.1.0 (Draft)  
> Status: Proposal Stage

## Overview

Om's syntax is designed to be wave-native, supporting direct expression of wave patterns, phases, and fields while maintaining readability and AI-friendliness.

## Lexical Structure

### Keywords
```om
const keywords~ = [
    // Wave operations
    'wave', 'pattern', 'field',
    
    // Flow control
    'if~', 'else~', 'try~', 'catch~',
    
    // Type system
    'type', 'interface', 'enum',
    
    // Modifiers
    'const', 'async', 'export'
]
```

### Operators
```om
const operators~ = {
    // Wave pipe operator
    '|': 'pipe wave operations',
    
    // Wave marker
    '~': 'wave type indicator',
    
    // Range operator
    'to': 'frequency range specifier'
}
```

### Units
```om
const units~ = {
    // Frequency units
    frequency: ['Hz', 'kHz', 'MHz', 'GHz'],
    
    // Phase units
    phase: ['deg', 'rad'],
    
    // Time units
    time: ['ms', 's', 'min'],
    
    // Power units
    power: ['mW', 'W']
}
```

## Grammar

### Wave Declarations
```om
// Basic wave creation
wave_declaration:
    ['const' | 'let'] IDENTIFIER '~'? '=' wave_expression

wave_expression:
    'wave' '(' frequency_value unit ')'
    | 'oscillate' '(' frequency_value unit ')'
    | pattern_expression
    | field_expression

frequency_value:
    NUMBER ['Hz' | 'kHz' | 'MHz' | 'GHz']
```

### Wave Operations
```om
// Wave operation chaining
operation_chain:
    wave_expression
    ('|' operation)*

operation:
    IDENTIFIER '(' parameters ')'
    | phase_operation
    | amplitude_operation

phase_operation:
    'phase' '(' NUMBER phase_unit ')'
    
phase_unit:
    'deg' | 'rad'

amplitude_operation:
    'amplitude' '(' NUMBER ')'
```

### Pattern Syntax
```om
// Pattern definitions
pattern_declaration:
    ['const' | 'let'] IDENTIFIER '~'? ':' 'Pattern~' '=' pattern_expression

pattern_expression:
    '[' wave_expression (',' wave_expression)* ']'
    | 'pattern' '(' wave_expression ')'
```

### Field Syntax
```om
// Field declarations
field_declaration:
    ['const' | 'let'] IDENTIFIER '~'? ':' 'Field~' '=' field_expression

field_expression:
    'Field~' '.' 'create' '(' field_parameters ')'

field_parameters:
    '{' 
        'dimensions' ':' '[' NUMBER ',' NUMBER ']' ','
        'wave' ':' wave_expression
    '}'
```

## Type Annotations

### Basic Types
```om
// Type declarations
type_declaration:
    'type' IDENTIFIER '~'? '=' type_expression

type_expression:
    '{' (property_declaration)* '}'
    | union_type
    | intersection_type

property_declaration:
    IDENTIFIER ':' type_reference
```

### Wave Types
```om
// Wave-specific type annotations
wave_type_annotation:
    ':' ('Wave~' | 'Pattern~' | 'Field~')
    | ':' custom_wave_type

custom_wave_type:
    IDENTIFIER '~'
```

## Functions

### Wave Functions
```om
// Wave function declarations
wave_function:
    ['async'?] 'function' IDENTIFIER '~'?
    '(' parameters? ')' [':' return_type]
    block_statement

// Arrow functions
wave_arrow_function:
    ['async'?] '(' parameters? ')' [':' return_type] '=>'
    (expression | block_statement)
```

## Error Handling

### Try-Catch Blocks
```om
// Wave error handling
try_statement:
    'try~' block_statement
    'catch~' '(' IDENTIFIER ':' error_type ')' block_statement

error_type:
    'WaveError~'
    | 'PatternError~'
    | 'FieldError~'
```

## Comments and Documentation

### Documentation Comments
```om
// Single-line comment
// This is a comment

/* Multi-line comment
   Supports multiple lines
*/

/**
 * Documentation comment
 * @param frequency {Frequency~} Input frequency
 * @returns {Wave~} Processed wave
 */
```

## Examples

### Complete Program Example
```om
// Wave processing program
type ProcessConfig~ = {
    frequency: Frequency~,
    phase: Angle~,
    amplitude: Number~
}

/**
 * Process wave pattern
 */
async function processWave~(config: ProcessConfig~): Promise<Wave~> {
    try~ {
        const wave~ = wave(config.frequency)
            | phase(config.phase)
            | amplitude(config.amplitude)
            
        return wave~
            | normalize
            | validate
    } catch~ (error: WaveError~) {
        console.error(`Processing error: ${error.message}`)
        throw error
    }
}
```

### Phase Operations
```om
// Phase operations
const wave1~ = wave(41.5kHz)
    | phase(45deg)      // Using degrees
    | amplitude(0.8)

const wave2~ = wave(41.5kHz)
    | phase(0.785rad)   // Using radians
    | amplitude(0.5)

// Invalid: phase without unit
const invalid~ = wave(41.5kHz)
    | phase(45)         // Error: Phase angle must specify unit
```

## Implementation Notes

1. **Lexer Considerations**
   - Case-sensitive keywords
   - Unit-aware tokenization
   - Wave marker (~) handling

2. **Parser Features**
   - Recursive descent parsing
   - Error recovery
   - AST generation

3. **Syntax Extensions**
   - AI-assisted syntax
   - Domain-specific extensions
   - Custom operators

## See Also

- [Grammar Specification](grammar.md)
- [Type System](../analyzer/type-checker.md)
- [Semantic Analysis](../analyzer/semantic.md)
