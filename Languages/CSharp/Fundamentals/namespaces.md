# Namespaces

### What is it?

A namespace is a logical container used to group related classes, methods, and other types. Namespaces help organize large projects and avoid naming conflicts when two different libraries happen to define types with the same name.

### Example

Imagine a project split into the areas data access, business logic, and user interface. Each of these areas gets its own namespace, e.g. one for the data-access classes and another for the user-interface classes. If both areas happened to have a class with the same name, both could still be clearly distinguished and used at the same time thanks to their different namespaces.

```csharp
namespace Library.DataAccess
{
    class BookRepository { }
}

namespace Library.UI
{
    using Library.DataAccess;

    class BookListView
    {
        private BookRepository _repository = new BookRepository();
    }
}
```

### How does it work?

Every class belongs to exactly one namespace, which usually matches the project's folder structure. To use a class from another namespace, you either have to reference it with its full name including the namespace, or add a using directive at the top of the file that makes the namespace available, so afterward you only need to write the class name itself. If two included namespaces happen to contain types with the same name, the compiler requires you to use the full name to resolve the ambiguity.

### When should I use it?

* To structure a larger project into logically separated areas
* To avoid naming conflicts between your own code and external libraries
* To make related functionality easier to find

### Common Mistakes

* Cramming everything into a single namespace even though a sensible split would be possible
* Piling up using directives for namespaces that aren't actually used
* Overlooking naming conflicts and being confused by puzzling compiler errors

### Practice

**Task:**
For a small hypothetical project (e.g. a library management system), sketch out a sensible split into at least two namespaces and note which classes would belong to each.

**Goal:**
After this exercise you should be able to explain what namespaces are good for and how using directives work.
