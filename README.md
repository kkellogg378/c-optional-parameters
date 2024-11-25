# c-optional-parameters

```C
// function to give optional parameter functionality to
void func(int var1, int var2) {
  return (var1 + var2);
}

// default value for var2
#define VAR2_DEFAULT_VALUE 1

// make var2 optional
#define third(_1, _2, _3, ...) _3
#define func(...) third(__VA_ARGS__, func(__VA_ARGS__), func(__VA_ARGS__, VAR2_DEFAULT_VALUE))

/*
The third() macro selects the third parameter given to it as the output. The way that this works
is as follows: The __VA_ARGS__ represents the parameters inputted into the func() macro. When the
func() macro is given one parameter, that means the third parameter given to the third() macro is
func(__VA_ARGS__, VAR2_DEFAULT_VALUE), sending the default value to the func() function. When the
func() macro is given two parameters, that means the third parameter given to the third() macro is
func(__VA_ARGS__), which sends both inputted parameters to the func() function. This makes it so
a default value can be given to var2 of the function.
*/

// example usage
void main() {
  printf("%d\n", func(1, 2)); // output: 3
  printf("%d\n", func(2));    // output: 3
}
