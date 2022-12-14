# Modularization


## The differents ways to look at module concept
### Module as Build Target (build dependency graph node)
Every time you to create a swift module (os a framework) inside an Xcode project, you also create an associated build target.
So, the concepts of module and build target are tighltly related.
This thght relationship comes from the very old ages of C language compilation on Unix, using MakeFile Utility
A target described how to produce .o files from .c files, by Compiling. Target also described how to produce executable file from multiple .o files.

[TODO : Make a Schema for Dep Graph]


### Module as component boundary (Access Control)
When you declare a var (or a let) inside a swift type, without specifiying access control (public/private), like this : 

`struct Stuff { var prop: Int}`

The resulting default access control is `internal`, as if you had wrote : 

`struct Stuff { internal var prop: Int}`

What does mean this internal access control ? it means it's acessible from within the module only, not from other modules

So here we see that Swift modules are also the way to define components boundary : determining the inside/outside for (internal, defaulf) access control

### Module for Dependency Inversion 

Maybe the best article for understanding what Dependency Inversion Principle (DIP) is can be found here : [Dependency Inversion as a Driver to Scale Mobile Development](https://developers.soundcloud.com/blog/dependency-inversion-as-a-driver-to-scale-mobile-development)

The Dependency Inversion Principle  (The 'I' in SOLID principles set from Clean Architecture) is a very powerfull and misusnderstood one.
So as Uncle Bob says, we should use principles pragmatically not dogmatically. So what is encouraged here is to 'be prepared to do dependency inversion' instead of doing in every case.

The rules for this preparation are : 

* Declare abstraction (protocol) on side of caller (Declare Presenter protocol in the file of implementation of the view that depends on and use this protocol)
* Use an Abstract-Factory (or other abstact injection mecanism) to produce the Object implementing the protocol.

[TODO : Make a Schema Before/After DI ]
