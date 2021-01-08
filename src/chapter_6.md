## Ownership

- Each value has a variable called its _owner_
- There can only be one owner at a time
- When the owner goes out of scope, the value is dropped

Ownership applies to data types of non-fixed size stored on the heap

eg. `String` as opposed to string literals:

```rust,ignore
    let mut s = String::from("hello");

    s.push_str(", world!"); // push_str() appends a literal to a String

    println!("{}", s); // This will print `hello, world!`
```

### Variables and Data

```rust,ignore
 let s1 = String::from("hello");
 let s2 = s1;
```

Both `s1` and `s2` are pointers on the stack to data on the heap.

Once a variable goes out of scope, Rust calls the `drop` function to clean up the heap memory for that variable.

Assigning `s1` to `s2` invalidates the reference `s1`. `s1` is _moved_ into `s2`. Invalidating the first variable prevents the _double free_ error.

### Clone

If a deep copy is desired:

```rust,ignore
   let s1 = String::from("hello");
   let s2 = s1.clone();

   println!("s1 = {}, s2 = {}", s1, s2);
```

### Stack-Only Data: Copy

```rust,ignore
    let x = 5;
    let y = x;

    println!("x = {}, y = {}", x, y);
```

Data types of known size are stored on the stack and posess the `Copy` trait.

- Integer types
- Boolean, `bool`
- Floating point types
- Character, `char`
- Tuples, if all elements are type `Copy`
