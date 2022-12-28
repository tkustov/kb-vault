Built-in TypeScript enums considered harmful, because of few quirks in its implementation.
So, proposed way to use enums is:

```typescript
export const Digits = {
  One: 'one',
  Two: 'two',
  Five: 'five'
} as const;

// utility type, might be placed somewhere outside
type ObjectValues<T> = T[keyof T];

export type DigitsEnum = ObjectValues<typeof Digits>; // 'one' | 'two' | 'five'
```