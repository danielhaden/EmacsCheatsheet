## Tail Recursion
In 'traditional' recursion, recursive calls are performed first, then one or more computations are performed to return the final result. For example,

```csharp
int length(List list)
{
    if 
}


```


```csharp    
int fib (int n)
{
    if ((n == 1) || (n == 0))
        return n;

    return fib(n - 1) + fib(n - 2)
}
```

To calculate the 4th Fibonacci number,
```
fib(4)
fib(3) + fib(2)
fib(2) + 1 + 1 + 0
1 + 0 + 1 + 1 + 0
3
```

One could introduce memoization to avoid duplicate calls to fib with the same argument.


In tail recursion, the last function call should return the final result. In other words, instead of travelling down the call tree and then calculating as we backtrack up, in tail recursion, we use an accumulator variable to keep track of the running total as we traverse down the call tree. This is desirable because many compilers can transform such code into a loop. So you get the elegance of recursion in your source code without the performance hit with recursive function calls at runtime.

In fact, tail-recursion is equivalent to looping but not all compilers are capable of recognizing tail-recursion and converting it to an equivalent loop structure. 

```csharp
int fib (int n)
{
    int current = 1, int previous = 0;
    while (i < n)
    {
        current += previous
        previous = current - previous

        console.Writeline(current, previous);
    }

    return current;
}

```
1 0
2 1
3 2

```


```csharp

int fib(int n)
{
    if (n == 0)
        return 0;
    
    return tailFib(n-1, 1, 0);
}

int tailFib(int n, int current, int previous)
{
    if (n == 1)
        return current;
    
    return tailFib(n-1, current + previous, current);
}
```

Now to calculate the 4th Fibonacci number,
```
fib(4)
tailFib(4, 1, 0)
tailFib(3, 1, 1)
tailFib(2, 2, 1)
tailFib(1, 3, 0)
tailFib(0, 3, 0)
3
```

