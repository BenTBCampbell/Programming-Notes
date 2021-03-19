## C#

### Basics

Use `Console.Write()` and `Console.WriteLine()` to print messages to consoles.

Some syntax examples:
```c#
// import external things with "using"
using System;

// organize things with namespaces
namespace Franciscan {
    // and classes
    class Household {

        // Fields are regular old variables that don't have special
        // gettters or setters. 
        // camelCase with lowercase first letter.
        int age;
        string name;
        string[] members;

        // Properties are special variables that have getter and setter
        // functions. They are good for public variables.
        // CamelCase with uppercase first letter.
        public string Name {
            get { return name; } 
            set { name = value; }
        }

        // Methods start with an uppercase letter.
        public void AddMember(name) {
            // ...
        }

        // example of a constructor
        public Household (string name, string[] members) {
            // ...
        }

    }
}
```