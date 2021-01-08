## Structs

#### Defining

```rust,ignore
struct User {
    username: String,
    email: String,
    sign_in_count: u64,
    active: bool,
}
```

#### Instantiating

```rust,ignore
    let mut user1 = User {
        email: String::from("someone@example.com"),
        username: String::from("someusername123"),
        active: true,
        sign_in_count: 1,
    };
```

An entire instance must be either immutable or mutable.

#### Field Init Shorthand when Variables and Fields Have Same Name

```rust,ignore
fn build_user(email: String, username: String) -> User {
    User {
        email,
        username,
        active: true,
        sign_in_count: 1,
    }
}
```

#### Creating Instances from Other Instances

```rust,ignore
    let user2 = User {
        email: String::from("another@example.com"),
        username: String::from("anotherusername567"),
        active: user1.active,
        sign_in_count: user1.sign_in_count,
    };
```

or

```rust,ignore
    let user2 = User {
        email: String::from("another@example.com"),
        username: String::from("anotherusername567"),
        ..user1
    };
```

### Tuple Structs without Named Fields

```rust,ignore
    struct Color(i32, i32, i32);
    struct Point(i32, i32, i32);

    let black = Color(0, 0, 0);
    let origin = Point(0, 0, 0);
```

### Example Program Using Structs

```rust,ignore
#[derive(Debug)]
struct Rectangle {
    width: u32,
    height: u32,
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    println!("rect1 is {:?}", rect1);

    println!(
        "The area of the rectangle is {} square pixels.",
        area(&rect1)
    );
}

fn area(rectangle: &Rectangle) -> u32 {
    rectangle.width * rectangle.height
}
```

The specifier `:?` tells `println!` to use format `Debug`

To implement the `Debug` trait on `Rectangle` we must add the annotation `#[derive(Debug)]` before the struct.
