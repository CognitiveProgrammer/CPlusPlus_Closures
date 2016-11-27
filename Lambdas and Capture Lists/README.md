## Understand Lambdas and Capture Lists

### Lambdas
*A  lambda is an anonymous function the syntax of which is*
```
[]() -> Returen_type(Optional) {};

```
*A sample lambda can be created as*
```
[](){
    cout<<"A Lambda"<<endl;
};
```
*The lambda can be called by adding () after }*
```
[](){
    cout<<"A Lambda"<<endl;
}(); // Lambda is called
```
### Capture Lists
*The [] represents the capture list of the lambda which denotes the usage of local scope variables inside lambda. The capture list is required because without it there is no way we can use local scope variables. we can't do something like this*
```
int x = 100;
[](){
    x++; // x is not accessible here
}();
```
*A capture list is allows variable to accessed inside a lambda either by value of by reference. Pass by value is done by using '=' inside capture list as '[=]' and pass by reference is done using '&' inside capture list as '[&]'*

__Let's see pass by reference__

```
int x = 100;
[&](){
   x++;
}();
// x is 101 at this point
```   
__Now pass by Value__
```
int x = 100;
[=](){
   // We can't do x++ over here. Compiler will not allows
   // modifying variables pass by value
}();
// x remains unchanged after this point
```   
__Changing variables passed by Value__

*This can be done using mutable keyword*

```
int x = 100;
[=]() mutable {
  x++; // Allowed, but modifies only the copy
}();
// x remains unchanged after this point
```
*we can also provide specific variables in capture list and individually specify pass by value or reference. This is what we need to know about lambdas for understanding the closures*

__A detailed description of C++ lambdas is present at https://github.com/9lean/Cplusplus_Lambda __

__and a video tutorial is location at https://www.youtube.com/watch?v=nF9Z6vi9wKA __ 
