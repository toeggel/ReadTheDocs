---
tags:
  - frontend
---

# Types

## Mapped types

> When you don’t want to repeat yourself, sometimes a type needs to be based on another type. 

> You can extend the name, remove readonly modifier, change types, ... generally map from one type property to another.


```typescript
type Events = {
    add:  string;
    delete: string;
}

type OnEvents = {
    [Property in keyof Events as `on${Capitalize<Property>}`] : () => any;
}

const userActions: OnEvents = {
    onAdd: () => {},
    onDelete: () => {}
}

// access type of property
type IsString = Events['add'];
//    ^? 

// keyof
type EventKeys = keyof Events;
//    ^? 

const invalidKey: EventKeys = 'move';


type Paths<T> = T extends object ?
    { [K in keyof T]-?: [K] | [K, ...Paths<T[K]>]  }[keyof T]
    : never;

type DeepReadonly<T> = {
    readonly [K in keyof T]: T[K] extends object ? DeepReadonly<T[K]> : T[K];
    };
```

## Template literals

> Template literal types build on string literal types, and have the ability to expand into many strings via unions.

```typescript
type ChessLetters = 'A' | 'B' | 'C' | 'D' | 'E' | 'F' | 'G' | 'H';
type ChessNumbers = 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8;

type BoardPositions = `${ChessLetters}${ChessNumbers}`[];

const b: BoardPositions = ['A1'];

type RgbCssType = `rgb(${number},${number},${number})`;

const rgbWrong: RgbCssType = 'asdf';
const rgbCorrect: RgbCssType = 'rgb(1,1,1)';

```

## Never

```typescript
type IsAnythingAssignableToNever = boolean extends never ? true : false;
//    ^?

type IsNeverAssignableToAnything = never extends boolean ? true : false;
//    ^?


type Locations = 'Oslo' | 'London';
//    ^?


// keep js usage save
function getValidLocationCountry(location: Locations): string {
    switch (location) {
        case 'Oslo':
            return 'Norway';
        case 'London':
            return 'England';
        default: 
            throw new Error(`${location} not known`);
    }
}
getValidLocationCountry("Oslo");

//compile
function getValidLocationCountryCompile(location: Locations): string {
    switch (location) {
        case 'Oslo':
            return 'Norway';
        case 'London':
            return 'England';
        default: 
            const exhaustiveCheck: never = location; // now the compiler complains when we extend the Locations enum an pass in the new value.
            throw new Error(`${location} not known`);
    }
}

getValidLocationCountryCompile('Oslo');

type NoEmptyString<T extends string> = T extends '' ? never : T;

function isEmptyString<T extends string>(nonEmpty: NoEmptyString<T>) {

}

isEmptyString('');
```

## infer

```typescript
type MyReturnType<T> = T extends (...args: any[]) => infer R ? R : never;

function add(a: number, b: number): number {
  return a + b;
}

type AddReturnType = MyReturnType<typeof add>;
//   ^?


type RgbInfer<T> = T extends `rgb(${infer first},${infer second},${infer third})`
? [first, second, third] : never;

type RgbInferNumber<T> = T extends `rgb(${infer first extends number},${infer second extends number},${infer third extends number})`
? [first, second, third] : never;

type ValidRgb = RgbInfer<'rgb(1,2,3)'>;
//    ^?
type ValidRgbNumber = RgbInferNumber<'rgb(1,2,3)'>;
//    ^? 


type InvalidRgb = RgbInferNumber<'rgb(1,2,a)'>;
//    ^? 

```

## Recursive

```typescript
// builtin type: Awaited

type Resolved = Awaited<Promise<Promise<Promise<string>>>>;
//    ^? 

type Tupel<Type, Length extends number, Tupel extends Type[] = []> = Tupel['length'] extends Length ? Tupel : TupelSized<Type, Length, [Type, ...Tupel]>;


type T3 = Tupel<number, 4>;
//   ^?

// MAX depth 1000 

interface Form {
    a: string;
    b: {
        c: {
            d: string;
        }
    }
}

type ArrayOrNever<T> = T extends any[] ? T : never;

type Path<T> = T extends object ? {[Key in keyof T]: [Key] | [Key, ...Path<T[Key]>]}[keyof T] : never;
type R = Path<Form>;
//   ^?
```

## Branded types

> The idea is to create a more specific and unique data type with greater clarity and specificity, this is accomplished by adding attributes or labels to an existing type to create a new, more specific type.

```typescript

// simple version

type Email = string & {__brand: 'Email'}; // general pattern for branded types

function isValidEmail(input: string): input is Email {
    ...
}

function sendEmail(input: Emai) {

}

if(isValidEmail(email)){
    sendEamil(email); // only compiles when "IsValidEmail" was called first
}


// more complex
function branded<PrimitiveType, BrandName, Brand extends PrimitiveType & {__brand: BrandName}>(
    checkFn: (input: PrimitiveType) => boolean, brandName: BrandName
): [(input: PrimitiveType) => input is Brand, Brand] {
    const isBrand = function (input: PrimitiveType): input is Brand {
        return checkFn(input);
    }

    return [isBrand, {} as Brand];
}

const [isEmail, EmailObject] = branded((input: string) => true, 'ValidEmail' as const);

type ValidEmail = typeof EmailObject;

function sendEmail(input: ValidEmail) {

}

const email = 'mail';
if(isEmail(email)) {
    const validEmail: ValidEmail = email;
    sendEmail(email);
}

const invalidEmail: ValidEmail = email;
```
