# @tszig/types

TypeScript type definitions for TSZig IDE support.

## Overview

This package provides TypeScript declaration files that enable IDE features like IntelliSense, type checking, and error highlighting for TSZig-specific functions and annotations.

## Installation

```bash
npm install --save-dev @tszig/types
```

## Setup

Add to your `tsconfig.json`:

```json
{
  "compilerOptions": {
    "types": ["@tszig/types"]
  }
}
```

Or reference directly in your TypeScript file:

```typescript
/// <reference types="@tszig/types" />
```

## Features

### Global Functions

```typescript
// printf() - C-style formatted output
printf("Hello, %s! Value: %d\n", name, value);

// console.log() - JavaScript-style logging (enhanced)
console.log("Message:", value);
console.log(a, b, c);
```

### Format Specifiers

| Specifier | Description | Example |
|-----------|-------------|---------|
| `%s` | String | `printf("%s", name)` |
| `%d`, `%i` | Integer | `printf("%d", count)` |
| `%f` | Float | `printf("%f", price)` |
| `%c` | Character | `printf("%c", char)` |
| `%%` | Literal % | `printf("100%%")` |

### @defer Annotation

```typescript
// @defer marks variables for automatic cleanup
function processFile(path: string): string {
    // @defer - file will be automatically closed
    const file = fs.openSync(path, "r");
    const content = fs.readFileSync(file, "utf8");
    return content;
}
```

## Type Definitions

### globals.d.ts

```typescript
declare function printf(format: string, ...args: any[]): void;

declare namespace console {
    function log(...args: any[]): void;
    function error(...args: any[]): void;
    function warn(...args: any[]): void;
}
```

### fs.d.ts

```typescript
declare namespace fs {
    function readFileSync(path: string, encoding: string): string;
    function writeFileSync(path: string, data: string): void;
    function openSync(path: string, flags: string): FileHandle;
    function existsSync(path: string): boolean;
}
```

## Included Files

- `globals.d.ts` - Global functions (printf, console)
- `fs.d.ts` - File system module types
- `path.d.ts` - Path module types
- `runtime.d.ts` - Runtime helper types
- `index.d.ts` - Main export

## License

MIT License - see [LICENSE](LICENSE) for details.

## Contributing

See [CONTRIBUTING.md](https://github.com/TSZig/.github/blob/main/CONTRIBUTING.md) for guidelines.
