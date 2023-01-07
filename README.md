### What is Inheritance?
_Inheritance_ is when an object or a class is based on another object or a class (parent), using the same implementation and/or the same values.

For example, class Animal has property `numberOflegs` and method `walk()`. Class Dog can inherit this property and method.

### JS Prototypal Inheritance
Unlike object oriented inheritance, which is based on classes and is much more complex and has a lot of rules that you have to memorize and has different intricacies, prototypal inheritance is based on object instances and is very simple and straightforward. 

The original object instance becomes the prototype for all subsequently created objects. 

For example, we have an object called `parent` and it has a type property that is equal to the string "parent" and a method with the name "method".
```
    parent
type : "parent"
method()
```
Then, if we create a child object that is going to be based on our parent object, that child object will start off with being simply an empty object. 
```
    child
    {}
```
However, if we try to value an expression, `child.type?`, the JavaScript engine will look into the child object and look to see if it has the type property. 

In this case, it doesn't, so what it will do, the JavaScript engine will then look to the prototype chain to see which object is actually the parent of this child object. And in this case, it's the parent object itself. And we'll ask that parent object, whether or not there's a type property that belongs to it. In this case, there is one, and it evaluates to the parent string, so therefore it will get resolve, the type property will get resolve to the parent object. Which means `child.type` expression will then get resolved to the string parent. 

Now, the reason it's called the prototype chain is because it doesn't have to be limited to just one object in its subsequent child. It can have grandchildren, great-grandchildren, and so on and so forth. In other words you could create yet another object that is based on the child object and therefore the current parent will then become the grandparent of that newly created object. 

However what will happen if instead of evaluating child.type expression we set a `child.type="child"` property on the child object? 
```
    child
type : "child"
```
What will happen is that the child object will no longer be empty. It will actually have a property called type that will evaluate to the string child. What will then happen if you try to evaluate `child.type` in this case? What will happen is that since the `child.type` property actually masks the type that is inherited from the prototype of this object, which is the type property of the parent object, this will get evaluated and resolved immediately. Which means it will not go looking up the prototype chain to the parent object. Therefore, in this case `child.type` expression will get evaluated to the string child.