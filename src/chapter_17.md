## _vector_

Vectors are a collection whose values must be of the same type.

#### Creating a New Vector

```rust,ignore
let v: Vec<i32> = Vec::new();
```

#### Updating a Vector

```rust,ignore
    let mut v = Vec::new();

    v.push(5);
    v.push(6);
    v.push(7);
    v.push(8);
```

#### Dropping a Vector Drops Its Elements

A vector is freed when it goes out of scope.

```rust,ignore
    {
        let v = vec![1, 2, 3, 4];

        // do stuff with v
    } // <- v goes out of scope and is freed here
```

#### Reading Elements of Vectors

```rust,ignore
    let v = vec![1, 2, 3, 4, 5];

    let third: &i32 = &v[2];
    println!("The third element is {}", third);

    match v.get(2) {
        Some(third) => println!("The third element is {}", third),
        None => println!("There is no third element."),
    }
```

The `[]` method gives a reference and will cause a panic if it references a nonexistant element.

The `get` method gives an `Option<T>` and will return `None` without panicking if the index passed is outside the vector.

When the program has a valid reference, the borrow checker enforeces ownership and borrowing rules on the reference.

The following will panic:

```rust,ignore
    let mut v = vec![1, 2, 3, 4, 5];

    let first = &v[0];

    v.push(6);

    println!("The first element is: {}", first);
```

Adding a new element onto the end of the vector might require allocating new memory and copying the old elements to the new space, if there isn’t enough room to put all the elements next to each other where the vector currently is. In that case, the reference to the first element would be pointing to deallocated memory.

#### Iterating over the Values in a Vector

```rust,ignore
    let v = vec![100, 32, 57];
    for i in &v {
        println!("{}", i);
    }
```

Iterating over mutable references to make changes to all elements:

```rust,ignore
    let mut v = vec![100, 32, 57];
    for i in &mut v {
        *i += 50;
    }
```

To change the value that the mutable reference refers to, we have to use the dereference operator (`*`) to get to the value in `i` before we can use the `+=` operator.

#### Using an Enum to Store Multiple Types

```rust,ignore
    enum SpreadsheetCell {
        Int(i32),
        Float(f64),
        Text(String),
    }

    let row = vec![
        SpreadsheetCell::Int(3),
        SpreadsheetCell::Text(String::from("blue")),
        SpreadsheetCell::Float(10.12),
    ];
```

Using an enum plus a `match` expression means that Rust will ensure at compile time that every possible case is handled.
