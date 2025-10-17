Decorators
********************

staticmethod
#####################

https://stackoverflow.com/questions/23508248/why-do-we-use-staticmethod

`@staticmethod` is a decorator used to define a method inside a calss that does not require access to the following
* instance (self)
* class (cls)
It behaves like a regular function but is logically grouped within a class

.. code-block:: console

    class MathOperations:
        @staticmethod
        def add(x, y):
            return x + y

    # Calling static method using the class
    print(MathOperations.add(3, 5))  # Output: 8

    # Calling static method using an instance
    math_obj = MathOperations()
    print(math_obj.add(10, 20))  # Output: 30

The above code `add(x, y)` does not require `self` or `cls`, making it a perfect candiate for `@staticmethod`