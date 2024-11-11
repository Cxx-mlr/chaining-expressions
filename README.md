# Chaining Expressions

Chaining Expressions is a library for C++ that enables users to chain operations seamlessly using custom `<<` and `>>` operators. This chaining approach simplifies function composition, making code more readable and expressive.

## Features

- **Function Composition:** Easily link multiple functions together.
- **Streamlined Syntax:** Use `<<` and `>>` operators to create intuitive expression chains.
- **Type-Safe Chaining:** Enforces compile-time type checks, ensuring each chained function’s output matches the next function’s input.

## Usage

Here’s an example of chaining several functions to transform and print a result:

```cpp
#include <iostream>
#include <cassert>
#include <string>
#include "ExprChain.hpp"

// Sample functions
std::string get_str()         { return "123";            }
int to_int(std::string value) { return std::stoi(value); }
int transform(int value)      { return value * 2;        }
void c_out(int result)        { std::cout << result;     }

int main() {
    using namespace ExprChain;

    // Chained expression
    int integer = LIFT(get_str) >> LIFT(to_int) >> LIFT(transform) << LIFT(c_out);

    assert(integer == 246);
}

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
