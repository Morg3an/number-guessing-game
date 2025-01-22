# Number Guessing Game

## Overview

This project is part of the **Day 2** learning challenge in the 30-Day Rust Challenge. It demonstrates the use of control flow in Rust by implementing a simple number guessing game.

## Features

- Randomly generates a secret number between 1 and 100.
- Allows the player to guess the number.
- Provides feedback on whether the guess is too high, too low, or correct.
- Utilizes control flow constructs such as `if`, `else`, `match`, and loops.

## Concepts Covered

- **Control Flow:** `if`, `else`, `loop`, `while`, and `for` loops.
- **Error Handling:** Using `match` to handle invalid input.
- **Standard Library Usage:** `rand` for random number generation and `std::cmp::Ordering` for comparison.

## Code Explanation

```rust
use rand::Rng;
use std::cmp::Ordering;
use std::io;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1..=100);

    loop {
        println!("Please input your guess.");

        let mut guess = String::new();

        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read line");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => {
                println!("Please enter a valid number!");
                return;
            }
        };

        println!("You guessed: {}", guess);

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too small! The secret number was: {}", secret_number),
            Ordering::Greater => println!("Too big! The secret number was: {}", secret_number),
            Ordering::Equal => {
                println!("You win!"); 
                break;
            }
        }
    }
}
```

## How to Use
1. Clone the repository:
   ```bash
   git clone https://github.com/Morg3an/number-guessing-game.git
   ```
2. Navigate to the project directory:
   ```bash
   cd number-guessing-game
   ```
3. Build the project:
   ```bash
   cargo build
   ```
4. Run the project:
   ```bash
   cargo run
   ```
5. Follow the on-screen instructions to select a shape and provide dimensions.

## Example Output
```
Area Calculator
Guess the number!
Please input your guess.
10
You guessed: 10
Too small! The secret number was: 42
Please input your guess.
42
You guessed: 42
You win!

```

## Project Structure
```
src
├── main.rs       # Main application logic
Cargo.toml        # Project metadata and dependencies
```

## Dependencies
This project uses the Rust standard library, and the rand crate for random number generation.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments
- [The Rust Programming Language Book](https://doc.rust-lang.org/book/)
- [Rust Standard Library Documentation](https://doc.rust-lang.org/std/)