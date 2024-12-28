# Om Language Grammar Specification

> Version: 0.1.0 (Draft)  
> Status: Proposal Stage

## Program Structure

### Basic Structure
```typescript
// Program is a collection of statements
interface Program {
    statements: Statement[];
}

// Different types of statements
type Statement = 
    | WaveDeclaration
    | PatternDeclaration
    | FieldDeclaration
    | FunctionDeclaration
    | TypeDeclaration
    | ExpressionStatement
    | TryStatement;
```

### Declarations
```typescript
// Wave declarations
interface WaveDeclaration {
    kind: 'const' | 'let';
    identifier: string;
    isWave?: boolean;  // presence of ~ symbol
    expression: WaveExpression;
}

// Pattern declarations
interface PatternDeclaration {
    kind: 'const' | 'let';
    identifier: string;
    type: 'Pattern~';
    expression: PatternExpression;
}

// Field declarations
interface FieldDeclaration {
    kind: 'const' | 'let';
    identifier: string;
    type: 'Field~';
    expression: FieldExpression;
}
```

### Expressions
```typescript
// Wave expressions
interface WaveExpression {
    type: 'wave' | 'oscillate';
    frequency: {
        value: number;
        unit: FrequencyUnit;
    };
}

// Units
type FrequencyUnit = 'Hz' | 'kHz' | 'MHz' | 'GHz';
type PhaseUnit = 'deg' | 'rad';
type TimeUnit = 'ms' | 's' | 'min';
type PowerUnit = 'mW' | 'W';
```

### Wave Operations
```typescript
// Pipe expressions
interface PipeExpression {
    base: Expression;
    operations: Operation[];
}

// Operations
interface Operation {
    type: 'phase' | 'amplitude' | 'custom';
    parameters: Parameter[];
}

// Phase operation
interface PhaseOperation {
    type: 'phase';
    value: number;
    unit: PhaseUnit;
}
```

### Example Usage
```typescript
// How the grammar translates to actual Om code
const wave~ = wave(41.5kHz)
    | phase(45deg)
    | amplitude(0.8);

// Represents this structure:
{
    kind: 'const',
    identifier: 'wave',
    isWave: true,
    expression: {
        type: 'wave',
        frequency: {
            value: 41.5,
            unit: 'kHz'
        },
        operations: [
            {
                type: 'phase',
                value: 45,
                unit: 'deg'
            },
            {
                type: 'amplitude',
                value: 0.8
            }
        ]
    }
}
```

### Type System
```typescript
// Type declarations
interface TypeDeclaration {
    name: string;
    isWave?: boolean;  // presence of ~
    properties: Property[];
}

interface Property {
    name: string;
    type: TypeReference;
}

type TypeReference = 
    | 'Wave~'
    | 'Pattern~'
    | 'Field~'
    | 'Number'
    | 'String'
    | 'Boolean'
    | CustomType;
```

### Functions
```typescript
// Function declarations
interface FunctionDeclaration {
    isAsync?: boolean;
    name: string;
    isWave?: boolean;  // presence of ~
    parameters: Parameter[];
    returnType?: TypeReference;
    body: Statement[];
}

// Example in Om:
async function process~(wave: Wave~): Promise<Result~> {
    // ...
}
```

### Error Handling
```typescript
// Try-catch blocks
interface TryStatement {
    body: Statement[];
    catchClause: {
        parameter: {
            name: string;
            type: ErrorType;
        };
        body: Statement[];
    };
}

type ErrorType = 'WaveError~' | 'PatternError~' | 'FieldError~';
```

## Implementation Notes

1. **Parser Implementation**
```typescript
class OmParser {
    parse(source: string): Program {
        // Parse Om code into AST
    }
}
```

2. **Type Checking**
```typescript
class TypeChecker {
    check(ast: Program): void {
        // Validate types and units
    }
}
```

## See Also

- [Syntax Specification](syntax.md)
- [Type System](../analyzer/type-checker.md)
- [Semantic Analysis](../analyzer/semantic.md)
