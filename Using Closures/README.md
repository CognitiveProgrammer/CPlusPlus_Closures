## Using Closures


# What is a Closure in C++?
*Closure can be best understood by looking at the code below, where we create a function which returns a lambda. The lambda function is then called later at another function*
```
std::function<void(void)> callFn() {
  int var_x = 10;
  return [=]() -> void {
     cout<<"The value of variable x is = "<<var_x<<endl;
  };
}
int main() {
  auto newFn = callFn();
  newFn(); // Prints var_x = 10;
  return 0;
}
```
*From this function we can see that the return lambda function contains a reference of the* __var_x__ *defined in the local scope of the callFn(). The variable* __var_x__ *has no existence outside the function callFn(), still we're able to access the variable in main()*

*__This behaviour is called closure__*

#Defining closure
*A closure is a lambda function in C++ where capture list variables becomes the part of lambda function itself and will exist even if the original scope where the variable was created is destroyed.*

#Capture List Pass by value
*When we pass anything in capture list by value, a copy is created within the scope of lambda function, so it doesn't matter if the original variable goes out of memory*

*As with other lambdas we can change the value of the variable using* *__mutable__* *keyword.*
```
std::function<void(void)> callFn() {
  int var_x = 10;
  return [=]() mutable -> void {
     cout<<"The value of variable x is = "<<var_x<<endl;
     var_x++;
  };
}
int main() {
  auto newFn = callFn();
  newFn();  // Prints 10
  newFn();  // Prints 11
  newFn();  // Prints 12
}
```
#Pass by reference
*Unfortunately, A Pass by reference will face the same problem as with other pass by reference parameter. Since its not a copy a new variable will not be create and using the same may result in unpredictable behaviour*
