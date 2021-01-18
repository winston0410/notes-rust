# Notes for Rust

## Types

### unsigned integers

`u8 u16 u32 u64 u128` for representing nonnegative whole numbers

### signed integers

`i8 i16 i32 i64 i128` for representing whole numbers

### pointer sized integers

`usize isize` for representing indexes and sizes of things in memory

**Unsigned integers vs signed integers?**

## Casing

Constant names are always in `SCREAMING_SNAKE_CASE`.

Variable names are always in `snake_case`.

Function names are always in `snake_case`.

Array is fix-lengthed, known at compile time

If no return type is specified for a function, it returns an empty tuple, also known as a unit.

## Loop

`loop`

No condition, `break` as you need to Value can be returned from `loop`

`while`

exit if the condition evaluates to `false`

`for…in`

exit if all items have been iterated

## Special way to return value

If the last statement in an if, match, function, or scope block is an expression without a `;`, Rust **will return it as a value from the block**.

Scope block:

Not a function, but it will help preventing global pollution

```rust
let v = {
        // This scope block lets us get a result without polluting function scope
        let a = 1;
        let b = 2;
        a + b
    };
    println!("from block: {}", v);
```

## Memory

### Data memory

For data that is **fixed in size and static**. e.g. `"hello world"`,

### Stack memory

For data that is **declared as variables** within a function.

### Heap memory

For data that is created **while the application is running**(runtime memory?).

## `struct`

```rust
struct SeaCreature {
    animal_type: String,
    name: String,
    arms: i32,
    legs: i32,
    weapon: String,
}
```

- `struct` do not have to have any fields at all.

- you can create `struct` that are used like a tuple.

```rust
struct Location(i32, i32);

fn main() {
    // This is still a struct on a stack
    let loc = Location(42, 32);
    println!("{}, {}", loc.0, loc.1);
}
```

## `enum`

- `enum` allow you to create **a new type** that can have a value of **several tagged elements** <https://tourofrust.com/29_en.html>

- `enum` with data (Read later) <https://tourofrust.com/30_en.html>

## Generic Types
