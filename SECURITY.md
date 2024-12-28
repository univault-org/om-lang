# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 0.1.x   | :white_check_mark: |

## Reporting a Vulnerability

We take the security of Om seriously. If you discover a security vulnerability, please follow these steps:

1. **Do Not** open a public issue
2. Email us at security@univault.org
3. Include detailed information about the vulnerability
4. Allow up to 48 hours for an initial response

### What to Include

```typescript
interface SecurityReport {
    details: {
        description: string;    // Clear description of the issue
        reproduction: string;   // Steps to reproduce
        impact: string;        // Potential impact
        mitigation?: string;   // Suggested fixes (if any)
    };
    
    metadata: {
        version: string;       // Om version
        platform: string;      // OS/platform
        context: string;       // Usage context
    };
}
```

## Security Measures

### Wave Operation Safety
```typescript
interface WaveSecurity {
    validation: {
        frequency: "Range checks",
        amplitude: "Power limits",
        units: "Type safety"
    };
    
    medical: {
        compliance: "IEC 60601-1",
        validation: "Pre-operation checks",
        logging: "Audit trail"
    };
}
```

## Disclosure Policy

1. Report received and acknowledged
2. Investigation and validation
3. Fix developed and tested
4. Security advisory published
5. Fix released

## See Also

- [Contributing Guidelines](CONTRIBUTING.md)
- [License](LICENSE)
