# python-learning

## What is a class 
In Python, a class is a blueprint for creating objects (a particular data structure), providing initial values for state (member variables or attributes), and implementations of behavior (member functions or methods). A class is defined using the class keyword, followed by the name of the class, and a colon. The class definition typically includes a constructor method (__init__), which is used to initialize the state of the object, and other methods that define the behavior of the object.

Here's an example of a basic class definition in Python:
```py
class Dog:
    def __init__(self, name, breed):
        self.name = name
        self.breed = breed
        
    def bark(self):
        print("Woof!")
        
    def sit(self):
        print(f"{self.name} is sitting.")
```

In this example, the class is called Dog and it has two attributes, name and breed which are passed as arguments to the constructor __init__ method. It also has two methods bark() and sit(). These methods are used to define the behavior of the object.

You can create an instance of the class by calling the class name as if it were a function and passing in any necessary arguments for the constructor:

```py
my_dog = Dog("Fido", "Golden Retriever")
```
This creates a new object called my_dog, which is an instance of the Dog class. You can then access the attributes and methods of this object by using the dot notation:

```py
my_dog.bark() # Output: Woof!
my_dog.sit() # Output: Fido is sitting.
```
Additionally, classes can also inherit properties and methods from other classes through inheritance. A derived class (child) inherits properties and methods from its parent class. This allows you to create new classes that are built on existing ones, without having to write the same code over and over again.

A constructor is a special method that is called when an object is created from a class, and it's typically used to initialize the state of the object. In Python, the constructor method is called __init__. This method is called automatically when you create a new object of a class. The constructor method takes the first parameter as self which refers to the object that is currently being created. The self parameter is required and must come first in any method definition inside the class.

A method is a function that is defined inside a class and it's used to define the behavior of the objects of that class. It's like a function but it is bound to an instance of the class. Methods are defined using the def keyword and take the first parameter as self which refers to the instance of the class which the method was called upon.

An object is an instance of a class. When you create an object of a class, you're creating an instance of that class. In python, you create an object using the class name, followed by parentheses, like a function call:

```py
my_dog = Dog("Fido", "Golden Retriever")
```

The above line creates a new object called my_dog, which is an instance of the Dog class. You can have multiple instances of a class, each with its own state and behavior.

An instance is an individual occurrence of a class. An instance is what you get when you create an object from a class. In other words, an instance is a specific object that is created from a class, with its own state and behavior.

For example, in the above example, my_dog is an instance of the Dog class. If you create another object using the same class, you will have another instance.
```py
my_second_dog = Dog("Buddy", "Bulldog")
```

my_second_dog is another instance of the Dog class which has its own state and behavior.

So to sum up, a class is a blueprint, an object is an instance of that blueprint and a constructor is a method that is called when an object is created and it's used to initialize the state of that object, while a method define the behavior of that object.

## Threading

Threading is a way to run multiple threads (smaller units of a program) concurrently, in the same process. It allows you to run multiple operations at the same time, rather than having to wait for one operation to finish before starting another. This can greatly improve the performance and responsiveness of your program, especially when working with I/O operations, network communications or other tasks that can take a significant amount of time to complete.

Python provides a threading module which is built on top of the lower-level _thread module. This module provides a Thread class that you can use to create and manage threads.

Here's an example of how to use the threading module to run two functions concurrently:

```py
import threading

def first_function():
    for i in range(10):
        print("first_function:", i)

def second_function():
    for i in range(10):
        print("second_function:", i)

# Create two threads
t1 = threading.Thread(target=first_function)
t2 = threading.Thread(target=second_function)

# Start the threads
t1.start()
t2.start()

# Wait for the threads to finish
t1.join()
t2.join()
```

In the above example, first_function and second_function are two functions that are going to run simultaneously on different threads. The Thread class takes a target parameter, which is the function that the thread will run. The start() method starts the thread, and the join() method is used to wait for the thread to finish before moving on.

Threads are lightweight, so it is possible to create many thousands of threads in a single process. However, creating too many threads can lead to performance issues because of the overhead of managing and scheduling the threads.

Python also has the concept of a ThreadPool which allows you to limit the number of threads created. This can help prevent a situation where a large number of threads are consuming too many resources, and instead uses a pool of worker threads to execute tasks, where it helps to not to overload the system.

## if name == main 

if __name__ == "__main__": is a common idiom used in Python scripts to make sure that the code inside the if block only gets executed when the script is run directly and not when it is imported as a module in another script.

The __name__ variable is a built-in variable in Python that holds the name of the current module. The value of __name__ is set to "__main__" when the script is run directly. When the script is imported as a module in another script, the value of __name__ is set to the name of the module, not "__main__".

The main use for this idiom is that it allows you to reuse functions, classes and other code from a script without having the script's code execute unnecessarily.

Here's an example:

```py
def some_function():
    print("This function is running")

if __name__ == "__main__":
    some_function()

```
If you run the above script, you will see the message "This function is running" printed on the screen. But if you import this script into another script as a module and call some_function() then the message will not be printed.

This is a handy way of making a script both importable and executable. It allows you to use the functions, classes or other code in the script as a library in another script or to use the script as a standalone program.

This idiom is particularly useful when you want to write test cases or perform the script's specific operations if the script is run directly but not when imported as a module.
