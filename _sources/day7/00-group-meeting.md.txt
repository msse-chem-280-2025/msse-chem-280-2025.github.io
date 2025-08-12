# Class Warm‑Up 

For today's class warm up, you will be applying concepts learned about C++ yesterday and comparing code and behavior to Python.
Write your answers on the class Google Presentation

---

1. **What is the difference between a C++ executable and a Python script? Define what each is and how they are created. What is the difference in the way you run each?**
------

2. **Consider the two code blocks below. First, try to predict what will happen in each. After you make a prediction, try running each one to observe the behavior. Write your observations in the class Google presentation. Are there any differences?**


````{tab-set-code} 

```{code-block} python
name = "Dr. Nash"

for i in range(3):
    name = "Dr. Pritchard"
    print("Inside loop:", name)
print("Outside loop:", name)
```
````
````{tab-set-code}
```{code-block} cpp
#include <iostream>
#include <string>

int main() {

    std::string name = "Dr. Nash";

    for (int i = 0; i < 3; i++) {
        std::string name = "Dr. Pritchard";
        std::cout << "Inside loop: " << name << std::endl;
    }
    std::cout << "Outside loop: " << name << std::endl; 
    return 0;
}
```
````
--------
3. **Consider the two code blocks below. First, try to predict what will happen in each. After you make a prediction, try running each one to observe the behavior. Write your observations in the class Google presentation. Are there any differences?**

````{tab-set-code} 

```{code-block} python
for i in range(3):
    name = "Dr. Pritchard"
    print("Inside loop:", name)
print("Outside loop:", name)
```
````

````{tab-set-code} 

```{code-block} cpp
#include <iostream>
#include <string>

int main() {
    for (int i = 0; i < 3; i++) {
        std::string name = "Dr. Pritchard";
        std::cout << "Inside loop: " << name << std::endl;
    }
    std::cout << "Outside loop: " << name << std::endl; 
    return 0;
}
```
````

4. Each code block below has an error on the last line. Try running each code block and observe how long it takes for an error to occur. 
If you observe a difference, give a reason based on the difference between how Python and C++ run.

````{tab-set-code} 

```{code-block} python
s = 0
for i in range(100000000):  # long loop
    s += i

print(result)  # intentional error: NameError (result is undefined)
```
````

````{tab-set-code} 

```{code-block} cpp
#include <iostream>

int main() {

    long long s = 0; //this is an integer data type for large numbers.
    for (long long i = 0; i < 100000000; ++i) {
        s += i;
    }

    std::cout << s << std::endl // <-- intentional error: missing semicolon

    return 0;
}
```
````
