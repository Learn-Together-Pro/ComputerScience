# :chart_with_upwards_trend: Data Structure Concepts

##### Tail Recursion

Tail recursion is a special form of recursion where the recursive call is the last thing executed in the function.

This has important implications for optimization because it allows the language's runtime to reuse the current function's stack frame for the recursive call, rather than creating a new one.

###### Tail Recursion Example

```rust
fn print( n : i32 )
{
    if n < 0
    {
        return;
    }
    println!( "{}", n );

    // The last executed statement is the recursive call
    print( n - 1 );
}
```
