# Solid Principles
It is about Readable, Testable, Extensible, Maintainable<br />
Readable code is clear and easy to understand. <br />
Each subclass is independently testable. Test-cases are no longer tightly coupled.<br />
Easily expanded or modified to accommodate new features or requirements without breaking existing features and application flow.<br />
Easy to find and fix bugs, to add new features, and to change existing features. It helps to reduce the cost of software development and maintenance.<br /><br />

* **Single responsibility**: A class should have only one responsibility. This means that a class should only do one thing and do it well.<br />
* **Open-closed**: Class should be open for extension but closed for modification. Add new features to a class without modifying the existing code.<br />
* **Liskov substitution**: Subclasses should be substitutable for their base classes. Functionality that works with parent class must work with child classes.<br />
* **Interface segregation**: Clients should not be forced to depend on interfaces that they do not use. Not implement an interface that it does not need.<br />
* **Dependency inversion**: High-level modules should not depend on low-level modules. Both should depend on abstractions.<br />
### More principles <br />
* **DRY** (Don’t Repeat Yourself) Principle advises avoiding duplicating code to improve maintenance, readability, and efficiency. <br />
E.g. - Create common method for all classes to checking the Empty/Null values or conversions logic or validations in utility class.<br />
* **KISS** (Keep It Super Simple) Principle - suggests prioritizing simplicity in design to enhance clarity, minimize complexity.<br />
