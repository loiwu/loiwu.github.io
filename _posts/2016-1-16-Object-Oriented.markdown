---
layout: post
title:  "Object Oriented Programming"
date:   2016-1-16 16:00:00 +0000
published:  true
categories: loiwu update
---


Logic will get you from A to B. Imagination will take you everywhere.

{{Redirect|Object-oriented|other meanings of object-oriented|Object-orientation (disambiguation){{!}}Object-orientation}}
{{redirects here|Object-oriented programming language|a list of object-oriented programming languages|List of object-oriented programming languages}}
{{Programming paradigms}}

'''Object-oriented programming''' ('''OOP''') is a [[programming paradigm]] based on the concept of "[[Object (computer science)|objects]]", which are [[data structure]]s that contain [[data]], in the form of [[Field (computer science)|fields]], often known as ''attributes;'' and code, in the form of procedures, often known as ''[[Method (computer science)|methods]].'' A distinguishing feature of objects is that an object's procedures can access and often modify the data fields of the object with which they are associated (objects have a notion of "[[this (computer programming)|this]]" or "self"). In OO programming, computer programs are designed by making them out of objects that interact with one another.<ref>{{Cite journal
| last = Kindler | first =  E.
| last2 = Krivy | first2 = I.
| title = Object-Oriented Simulation of systems with sophisticated control
| publisher = International Journal of General Systems
| year = 2011 | pages = 313–343}}</ref><ref>{{Cite book|last=Lewis|first=John|last2=Loftus|first2= William|title=Java Software Solutions Foundations of Programming Design 6th ed|publisher=Pearson Education Inc.|year=2008|isbn=0-321-53205-8}}, section 1.6 "Object-Oriented Programming"</ref> There is significant diversity in object-oriented programming, but most popular languages are [[Class-based programming|class-based]], meaning that objects are [[instance (computer science)|instance]]s of [[class (computer science)|class]]es, which typically also determines their [[data type|type]].

Many of the most widely used programming languages are [[multi-paradigm programming language]]s that support object-oriented programming to a greater or lesser degree, typically in combination with [[imperative programming|imperative]], [[procedural programming]]. Significant object-oriented languages include [[Python (programming language)|Python]], [[C++]], [[Objective-C]], [[Smalltalk]], [[Delphi (programming language)|Delphi]], [[Java (programming language)|Java]], [[Swift (programming language)|Swift]], [[C Sharp (programming language)|C#]], [[Perl]], [[Ruby (programming language)|Ruby]] and [[PHP]].

==Features==

Object-oriented programming by definition uses '''objects''', but not all of the associated techniques and structures are supported directly in languages which claim to support '''OOP'''.  The features listed below are, however, common among languages considered strongly class- and object-oriented (or [[multi-paradigm]] with OOP support), with notable exceptions mentioned.<ref name="ArmstrongQuarks">Deborah J. Armstrong. ''The Quarks of Object-Oriented Development''. A survey of nearly 40 years of computing literature which identified a number of fundamental concepts found in the large majority of definitions of OOP, in descending order of popularity: Inheritance, Object, Class, Encapsulation, Method, Message Passing, Polymorphism, and Abstraction.</ref><ref>[[John C. Mitchell]], ''Concepts in programming languages'', Cambridge University Press, 2003, ISBN 0-521-78098-5, p.278.  Lists: Dynamic dispatch, abstraction, subtype polymorphism, and inheritance.</ref><ref>Michael Lee Scott, ''Programming language pragmatics'', Edition 2, Morgan Kaufmann, 2006, ISBN 0-12-633951-1, p. 470.  Lists encapsulation, inheritance, and dynamic dispatch.</ref><ref name="pierce">{{Cite book|last=Pierce|first=Benjamin|title=[[Types and Programming Languages]]|publisher=MIT Press|year=2002|isbn=0-262-16209-1}}, section 18.1 "What is Object-Oriented Programming?"  Lists: Dynamic dispatch, encapsulation or multi-methods (multiple dispatch), subtype polymorphism, inheritance or delegation, open recursion ("this"/"self")</ref>

{{See also|Comparison of programming languages (object-oriented programming)|List of object-oriented programming terms}}

===Shared with non-OOP predecessor languages===

Object-oriented programming languages typically share low-level features with high-level [[procedural programming]] languages (which were invented first).  The fundamental tools that can be used to construct a program include:
* [[Variable (computer science)|Variables]] which can store information formatted in a small number of built-in [[data type]]s like [[Integer (computer science)|integers]] and alphanumeric [[Character (computing)|characters]].  This may include [[data structures]] like [[String (computer science)|strings]], [[List (abstract data type)|lists]] and [[hash table]]s that are either built-in or result from combining variables using [[Pointer (computer programming)|memory pointers]]
* Procedures - also known as functions, methods, routines, or [[subroutine]]s - that take input, generate output, and manipulate data.  Modern languages include [[structured programming]] constructs like [[Loop (computing)|loops]] and [[Conditional (computer programming)|conditionals]].

[[Modular programming]] support provides the ability to group procedures into files and modules for organizational purposes.  Modules are [[namespace]]d so code in one module will not be accidentally confused with the same procedure or variable name in another file or module.

===Objects and classes===
Languages that support object-oriented programming typically use [[Inheritance (object-oriented programming)|inheritance]] for code reuse and extensibility in the form of either [[Class-based programming|classes]] or [[Prototype-based programming|prototypes]]. Those that use classes support two main concepts:

* [[Class (computer science)|Class]]es - the definitions for the data format and available procedures for a given type or class of object; may also contain data and procedures (known as class methods) themselves
* [[Object (computer science)|Objects]] - instances of classes

Objects sometimes correspond to things found in the real world. For example, a graphics program may have objects such as "circle", "square", "menu". An online shopping system might have objects such as "shopping cart", "customer", and "product".<ref>{{cite book|last=Booch|first=Grady|title=Software Engineering with Ada|year=1986|publisher=Addison Wesley|isbn=978-0805306088|page=220|url=https://en.wikiquote.org/wiki/Grady_Booch|quote=Perhaps the greatest strength of an object-oriented approach to development is that it offers a mechanism that captures a model of the real world.}}</ref> Sometimes objects represent more abstract entities, like an object that represents an open file, or an object which provides the service of translating measurements from U.S. customary to metric.

Each object is said to be an [[instance (computer science)|instance]] of a particular class (for example, an object with its name field set to "Mary" might be an instance of class Employee).  Procedures in object-oriented programming are known as [[Method (computer science)|methods]]; variables are also known as [[Field (computer science)|fields]], members, attributes, or properties.  This leads to the following terms:

* [[Class variable]]s - belong to the ''class as a whole''; there is only one copy of each one
* [[Instance variable]]s or attributes - data that belongs to individual ''objects''; every object has its own copy of each one
* [[Member variable]]s - refers to both the class and instance variables that are defined by a particular class
* Class methods - belong to the ''class as a whole'' and have access only to class variables and inputs from the procedure call
* Instance methods - belong to ''individual objects'', and have access to instance variables for the specific object they are called on, inputs, and class variables

Objects are accessed somewhat like variables with complex internal structure, and in many languages are effectively [[Pointer (computer programming)|pointers]], serving as actual references to a single instance of said object in memory within a heap or stack.  They provide a layer of [[Abstraction (computer science)|abstraction]] which can be used to separate internal from external code. External code can use an object by calling a specific instance method with a certain set of input parameters, read an instance variable, or write to an instance variable. Objects are created by calling a special type of method in the class known as a [[Constructor (object-oriented programming)|constructor]].  A program may create many instances of the same class as it runs, which operate independently.  This is an easy way for the same procedures to be used on different sets of data.

Object-oriented programming that uses classes is sometimes called [[class-based programming]], while [[prototype-based programming]] does not typically use classes. As a result, a significantly different yet analogous terminology is used to define the concepts of ''object'' and ''instance''.

In some languages classes and objects can be composed using other concepts like [[Trait (computer programming)|traits]] and [[Mixin|mixins]].

===Dynamic dispatch/message passing===
By definition, it is the responsibility of the object, not the external code, to 'on-demand' select the procedural code to run/execute in response to a method call, typically by looking up the method at run time in a table associated with the object.  This feature is known as [[dynamic dispatch]], and distinguishes an object from an [[abstract data type]] (or module), which has a fixed (static) implementation of the operations for all instances.  If there are multiple methods that might be run for a given name (which may require some language support), it is known as [[multiple dispatch]].

A method call is also known as [[message passing]].  It is conceptualized as a message (the name of the method and its input parameters) being passed to the object for dispatch.  

===Encapsulation===
If a class disallows calling code from accessing internal object data and forces access through methods only, this is a strong form of abstraction or information hiding known as [[Encapsulation (object-oriented programming)|encapsulation]].  Some languages (Java, for example) let classes enforce access restrictions explicitly, for example denoting internal data with the <code>private</code> keyword and designating methods intended for use by code outside the class with the <code>public</code> keyword.  Methods may also be designed public, private, or intermediate levels such as <code>protected</code> (which typically allows access from other objects of the same class, but not objects of a different class).  In other languages (like Python) this is enforced only by convention (for example, naming <code>private</code> methods starting with an underscore).  This is useful because it prevents the external code from being concerned with the internal workings of an object.  This facilitates [[code refactoring]], for example allowing the author of the class to change how objects of that class represent their data internally without changing any external code (as long as "public" method calls work the same way).  It also encourages programmers to put all the code that is concerned with a certain set of data in the same class, which organizes it for easy comprehension by other programmers.  Encapsulation is often used as a technique for encouraging [[Coupling (computer programming)|decoupling]].

===Composition, inheritance, and delegation===
Objects can contain other objects in their instance variables; this is known as [[object composition]].  For example, an object in the Employee class might contain (point to) an object in the Address class, in addition to its own instance variables like "first_name" and "position".  Object composition is used to represent "has-a" relationships: every employee has an address, so every Employee object has a place to store an Address object.

Languages that support classes almost always support [[inheritance (object-oriented programming)|inheritance]].  This allows classes to be arranged in a hierarchy that represents "is-a-type-of" relationships.  For example, class Employee might inherit from class Person.  All the data and methods available to the parent class also appear in the child class with the same names.  For example, class Person might define variables "first_name" and "last_name" with method "make_full_name()".  These will also be available in class Employee, which might add the variables "position" and "salary".  This technique allows easy re-use of the same procedures and data definitions, in addition to potentially mirroring real-world relationships in an intuitive way.  These classes and subclasses correspond to sets and subsets in [[mathematical logic]]. Rather than utilizing database tables and programming subroutines, the developer utilizes objects the user may be more familiar with: objects from their application domain.<ref>{{cite book|last=Jacobsen|first=Ivar|title=Object Oriented Software Engineering|year=1992|publisher=Addison-Wesley ACM Press|isbn=0-201-54435-0|pages=43–69|author2=Magnus Christerson |author3=Patrik Jonsson |author4=Gunnar Overgaard }}</ref>

Subclasses can override the methods defined by superclasses.  [[Multiple inheritance]] is allowed in some languages, though this can make resolving overrides complicated.  Some languages have special support for [[mixin]]s, though in any language with multiple inheritance, a mixin is simply a class that does not represent an is-a-type-of relationship.  Mixins are typically used to add the same methods to multiple classes.  For example, class UnicodeConversionMixin might provide a method unicode_to_ascii() when included in class FileReader and class WebPageScraper, which don't share a common parent.

[[Abstract class]]es cannot be instantiated into objects; they exist only for the purpose of inheritance into other "concrete" classes which can be instantiated.  In Java, the <code>[[final (Java)|final]]</code> keyword can be used to prevent a class from being subclassed.

The doctrine of [[composition over inheritance]] advocates implementing is-a-type-of relationships using composition instead of inheritance.  For example, instead of inheriting from class Person, class Employee could give each Employee object an internal Person object, which it then has the opportunity to hide from external code even if class Person has many public attributes or methods.  Some languages, like [[Go (programming language)|Go]] do not support inheritance at all.

The "[[open/closed principle]]" advocates that classes and functions "should be open for extension, but closed for modification".

[[Delegation (programming)|Delegation]] is another language feature that can be used as an alternative to inheritance.

===Polymorphism===
[[Subtyping]], a form of [[polymorphism (computer science)|polymorphism]], is when calling code can be agnostic as to whether an object belongs to a parent class or one of its descendants.  For example, a function might call "make_full_name()" on an object, which will work whether the object is of class Person or class Employee.  This is another type of abstraction which simplifies code external to the class hierarchy and enables strong [[separation of concerns]].

===Open recursion===

In languages that support [[open recursion]], object methods can call other methods on the same object (including themselves), typically using a special variable or keyword called <code>this</code> or <code>self</code>.  This variable is ''[[name binding|late-bound]]''; it allows a method defined in one class to invoke another method that is defined later, in some subclass thereof.

==History==
Terminology invoking "objects" and "oriented" in the modern sense of object-oriented programming made its first appearance at [[MIT]] in the late 1950s and early 1960s. In the environment of the [[artificial intelligence]] group, as early as 1960, "object" could refer to identified items ([[LISP]] atoms) with properties (attributes);<ref>{{Cite journal
|last = McCarthy |first =  J. |editor-link = John McCarthy
|last2 = Brayton |first2 = R. |author2-link = Robert Brayton (computer scientist)
|last3 = Edwards |first3 = D. |author3-link = Daniel Edwards (programmer)
|last4 = Fox     |first4 = P. |author4-link = Phyllis Fox
|last5 = Hodes   |first5 = L. |author5-link = Louis Hodes
|last6 = Luckham |first6 = D. |author6-link = David Luckham
|last7 = Maling  |first7 = K. |author7-link = Klim Maling (programmer)
|last8 = Park    |first8 = D. |author8-link = David Park (computer scientist)
|last9 = Russell |first9 = S. |author9-link = Steve Russell

|title = LISP I Programmers Manual
|place = [[Boston]], [[Massachusetts]]
|publisher = Artificial Intelligence Group, [[M.I.T. Computation Center]] and [[Research Laboratory of Electronics at MIT|Research Laboratory]]
|date=March 1960
|page = 88f  |pages =
|url = http://history.siam.org/sup/Fox_1960_LISP.pdf
|quote = In the local M.I.T. patois, association lists [of atomic symbols] are also referred to as "property lists", and atomic symbols are sometimes called "objects".
|postscript = <!--None-->}}</ref><ref>{{Cite book
|url = http://community.computerhistory.org/scc/projects/LISP/book/LISP%201.5%20Programmers%20Manual.pdf
|title = LISP 1.5 Programmer's Manual
|publisher = [[MIT Press]]
|first1 = John       |last1 = McCarthy  |author-link  = John McCarthy (computer scientist)
|first2 = Paul W.    |last2 = Abrahams
|first3 = Daniel J.  |last3 = Edwards   |author3-link = Daniel Edwards (programmer)
|first4 = swapnil d. |last4 = Hart
|first5 = Michael I. |last5 = Levin
|isbn = 0-262-13011-4
|year = 1962
|page = 105
|quote = Object&nbsp;— a synonym for atomic symbol}}</ref>
[[Alan Kay]] was later to cite a detailed understanding of LISP internals as a strong influence on his thinking in 1966.<ref name=alanKayOnOO>{{Cite web|url= http://www.purl.org/stefan_ram/pub/doc_kay_oop_en |title=Dr. Alan Kay on the Meaning of "Object-Oriented Programming" |year= 2003|accessdate=11 February 2010}}</ref>
Another early MIT example was [[Sketchpad]] created by [[Ivan Sutherland]] in 1960–61; in the glossary of the 1963 technical report based on his dissertation about Sketchpad, Sutherland defined notions of "object" and "instance" (with the class concept covered by "master" or "definition"), albeit specialized to graphical interaction.<ref>{{Cite web
|author=Sutherland, I. E.
|title=Sketchpad: A Man-Machine Graphical Communication System
|date=30 January 1963
|url=http://handle.dtic.mil/100.2/AD404549
|publisher=Technical Report No. 296, Lincoln Laboratory, Massachusetts Institute of Technology via Defense Technical Information Center (stinet.dtic.mil)
|format=PDF|accessdate=3 November 2007}}
</ref>
Also, an MIT [[ALGOL]] version, AED-0, established a direct link between data structures ("plexes", in that dialect) and procedures, prefiguring what were later termed "messages", "methods", and "member functions".<ref name=simuladev>
The Development of the Simula Languages,
[[Kristen Nygaard]], [[Ole-Johan Dahl]],
p.254
[http://cs-exhibitions.uni-klu.ac.at/fileadmin/template/documents/text/The_development_of_the_simula_languages.pdf Uni-kl.ac.at]
</ref><ref>{{Cite web
|last = Ross   |first = Doug
|title = The first software engineering language
|work = LCS/AI Lab Timeline:
|publisher = MIT Computer Science and Artificial Intelligence Laboratory
|url = http://www.csail.mit.edu/timeline/timeline.php?query=event&id=19
|doi =
|accessdate =13 May 2010 }}
</ref>

The formal programming concept of objects was introduced in the 1960s in [[Simula]] 67, a major revision of Simula I, a programming language designed for [[discrete event simulation]], created by [[Ole-Johan Dahl]] and [[Kristen Nygaard]] of the [[Norwegian Computing Center]] in [[Oslo]].<ref>{{Cite journal
|last = Holmevik  |first = Jan Rune
|title = Compiling Simula: A historical study of technological genesis
|journal = IEEE Annals of the History of Computing
|volume = 16  |issue = 4 |pages = 25–37
|publisher =  |year = 1994
|url = http://www.idi.ntnu.no/grupper/su/publ/simula/holmevik-simula-ieeeannals94.pdf| doi =   10.1109/85.329756
|accessdate =12 May 2010 }}
</ref>
Simula 67 was influenced by [[SIMSCRIPT]] and [[Tony Hoare|C.A.R. "Tony" Hoare']]s proposed "record classes".<ref name=simuladev/><ref>{{Cite journal
|last = Hoare
|first = C. A.
|author-link = Tony Hoare
|title = Record Handling
|journal = [[ALGOL Bulletin]]
|issue = 21
|pages = 39–69
|date=Nov 1965
|doi = 10.1145/1061032.1061041
|postscript = <!--None--> }}
</ref>
Simula introduced the notion of classes and instances or objects (as well as subclasses, virtual procedures, coroutines, and discrete event simulation) as part of an explicit programming paradigm. The language also used automatic [[garbage collection (computer science)|garbage collection]] that had been invented earlier for the [[functional programming]] language [[Lisp (programming language)|Lisp]]. <!-- The invention of automatic garbage collection is often erroneously attributed to OOP --> Simula was used for physical modeling, such as models to study and improve the movement of ships and their content through cargo ports. The ideas of Simula 67 influenced many later languages, including Smalltalk, derivatives of LISP ([[CLOS]]), [[Object Pascal]], and [[C++]].

The [[Smalltalk]] language, which was developed at [[Xerox PARC]] (by [[Alan Kay]] and others) in the 1970s, introduced the term ''object-oriented programming'' to represent the pervasive use of objects and messages as the basis for computation. Smalltalk creators were influenced by the ideas introduced in Simula 67, but Smalltalk was designed to be a fully dynamic system in which classes could be created and modified dynamically rather than statically as in Simula 67.<ref name="st">{{Cite web|first=Alan|last=Kay|url=http://gagne.homedns.org/~tgagne/contrib/EarlyHistoryST.html|title=The Early History of Smalltalk|accessdate=13 September 2007}}</ref> Smalltalk and with it OOP were introduced to a wider audience by the August 1981 issue of ''[[Byte (magazine)|Byte Magazine]]''.

In the 1970s, Kay's Smalltalk work had influenced the [[Lisp (programming language)#Language innovations|Lisp community]] to incorporate [[Lisp (programming language)#Object systems|object-based techniques]] that were introduced to developers via the [[Lisp machine]]. Experimentation with various extensions to Lisp (such as LOOPS and [[Flavors (programming language)|Flavors]] introducing [[multiple inheritance]] and [[mixins]]) eventually led to the [[Common Lisp Object System]], which integrates functional programming and object-oriented programming and allows extension via a [[Meta-object protocol]]. In the 1980s, there were a few attempts to design processor architectures that included hardware support for objects in memory but these were not successful. Examples include the [[Intel iAPX 432]] and the [[Linn Products|Linn Smart]] [[Rekursiv]].

In 1985, [[Bertrand Meyer]] produced the first design of the [[Eiffel (programming language)|Eiffel language]]. Focused on software quality, Eiffel is among the purely object-oriented languages, but differs in the sense that the language itself is not only a programming language, but a notation supporting the entire software lifecycle. Meyer described the Eiffel software development method, based on a small number of key ideas from software engineering and computer science, in [[Object-Oriented Software Construction]]. Essential to the quality focus of Eiffel is Meyer's reliability mechanism, [[Design by Contract]], which is an integral part of both the method and language.

Object-oriented programming developed as the dominant programming methodology in the early and mid 1990s when programming languages supporting the techniques became widely available. These included Visual [[FoxPro]] 3.0,<ref>1995 (June) Visual [[FoxPro]] 3.0, FoxPro evolves from a procedural language to an object-oriented language. Visual FoxPro 3.0 introduces a database container, seamless client/server capabilities, support for ActiveX technologies, and OLE Automation and null support. [http://www.foxprohistory.org/foxprotimeline.htm#summary_of_fox_releases Summary of Fox releases]</ref><ref>FoxPro History web site: [http://www.foxprohistory.org/tableofcontents.htm Foxprohistory.org]</ref><ref>1995 Reviewers Guide to Visual FoxPro 3.0: [http://www.dfpug.de/loseblattsammlung/migration/whitepapers/vfp_rg.htm DFpug.de]</ref> [[C++]],<ref>https://books.google.co.uk/books?id=MHmqfSBTXsAC&pg=PA16&lpg=PA16</ref> and [[Embarcadero Delphi|Delphi]]{{Citation needed|date=February 2010}}. Its dominance was further enhanced by the rising popularity of [[graphical user interface]]s, which rely heavily upon object-oriented programming techniques. An example of a closely related dynamic GUI library and OOP language can be found in the [[Cocoa (software)|Cocoa]] frameworks on [[Mac OS X]], written in [[Objective-C]], an object-oriented, dynamic messaging extension to C based on Smalltalk. OOP toolkits also enhanced the popularity of [[event-driven programming]] (although this concept is not limited to OOP).

At [[ETH Zürich]], [[Niklaus Wirth]] and his colleagues had also been investigating such topics as [[data abstraction]] and [[modularity (programming)|modular programming]] (although this had been in common use in the 1960s or earlier). [[Modula-2]] (1978) included both, and their succeeding design, [[Oberon (programming language)|Oberon]], included a distinctive approach to object orientation, classes, and such.

Object-oriented features have been added to many previously existing languages, including [[Ada (programming language)|Ada]], [[BASIC]], [[Fortran]], [[Pascal (programming language)|Pascal]], and [[COBOL]]. Adding these features to languages that were not initially designed for them often led to problems with compatibility and maintainability of code.

More recently, a number of languages have emerged that are primarily object-oriented, but that are also compatible with procedural methodology. Two such languages are [[Python (programming language)|Python]] and [[Ruby programming language|Ruby]]. Probably the most commercially important recent object-oriented languages are [[Java (programming language)|Java]], developed by [[Sun Microsystems]], as well as [[C Sharp (programming language)|C#]] and [[Visual Basic.NET]] (VB.NET), both designed for Microsoft's [[.NET Framework|.NET]] platform. Each of these two frameworks shows, in its own way, the benefit of using OOP by creating an abstraction from implementation. VB.NET and C# support cross-language inheritance, allowing classes defined in one language to subclass classes defined in the other language.

==OOP languages==
{{Unreferenced section|date=August 2009}}
{{See also|List of object-oriented programming languages}}

[[Simula]] (1967) is generally accepted as being the first language with the primary features of an object-oriented language. It was created for making [[Computer simulation|simulation program]]s, in which what came to be called objects were the most important information representation. [[Smalltalk]] (1972 to 1980) is an early example, and the one with which much of the theory of object-oriented programming was developed. Concerning the degree of object orientation, the following distinctions can be made:
*Languages called "pure" OO languages, because everything in them is treated consistently as an object, from primitives such as characters and punctuation, all the way up to whole classes, prototypes, blocks, modules, etc. They were designed specifically to facilitate, even enforce, OO methods. Examples: [[Eiffel (programming language)|Eiffel]], [[Emerald (programming language)|Emerald]],<ref>{{cite web|url=http://www.emeraldprogramminglanguage.org/|title=The Emerald Programming Language| date=2011-02-26}}</ref> [[JADE (programming language)|JADE]], [[Obix programming language|Obix]], [[Ruby (programming language)|Ruby]], [[Scala (programming language)|Scala]], [[Smalltalk]], [[Self (programming language)|Self]].
*Languages designed mainly for OO programming, but with some procedural elements. Examples: [[Object Pascal|Delphi/Object Pascal]], [[C++]], [[Java (programming language)|Java]], [[C Sharp (programming language)|C#]], [[VB.NET]].
*Languages that are historically [[Procedural programming|procedural languages]], but have been extended with some OO features. Examples: [[Pascal (programming language)|Pascal]], [[Visual Basic]] (derived from BASIC), [[MATLAB]], [[Fortran]], [[Perl]], [[COBOL]] 2002, [[PHP]], [[ABAP]], [[Ada (programming language)|Ada 95]].
*Languages with most of the features of objects (classes, methods, inheritance), but in a distinctly original form. Examples: [[Oberon (programming language)|Oberon]] (Oberon-1 or Oberon-2).
*Languages with [[abstract data type]] support which may be used to resemble OO programming, but without all features of object-orientation. This includes [[object-based|object-''based'']] and [[Prototype-based programming|prototype-based]] languages. Examples: [[Modula-2]], [[Pliant]], [[CLU (programming language)|CLU]], [[JavaScript]], [[Lua (programming language)|Lua]].
*Chameleon languages that support multiple paradigms, including OO. [[Tcl]] stands out among these for TclOO, a hybrid object system that supports both [[prototype-based programming]] and class-based OO.

===OOP in dynamic languages===
In recent years, object-oriented programming has become especially popular in [[dynamic programming language]]s. [[Python (programming language)|Python]], [[Ruby (programming language)|Ruby]] and [[Groovy (programming language)|Groovy]] are dynamic languages built on OOP principles, while [[Perl]] and [[PHP]] have been adding object-oriented features since Perl 5 and PHP 4, and [[ColdFusion]] since version 6.

The [[Document Object Model]] of [[HTML]], [[XHTML]], and [[XML]] documents on the Internet has bindings to the popular [[JavaScript]]/[[ECMAScript]] language. JavaScript is perhaps the best known [[prototype-based programming]] language, which employs cloning from prototypes rather than inheriting from a class (contrast to [[class-based programming]]). Before [[ECMAScript]] 6, only a prototype-based object model was supported. Another scripting language that takes this approach is [[Lua (programming language)|Lua]].

===OOP in a network protocol===
The messages that flow between computers to request services in a client-server environment can be designed as the linearizations of objects defined by class objects known to both the client and the server.  For example, a simple linearized object would consist of a length field, a code point identifying the class, and a data value.  A more complex example would be a command consisting of the length and code point of the command and  values consisting of linearized objects representing the command's parameters.  Each such command must be directed by the server to an object whose class (or superclass) recognizes the command and is able to provide the requested service. Clients and servers are best modeled as complex object-oriented structures. [[Distributed Data Management Architecture]] (DDM) took this approach and used class objects to define objects at four levels of a formal hierarchy:

* Fields defining the data values that form messages, such as their length, codepoint and data values. 
* Objects and collections of objects similar to what would be found in a [[Smalltalk]] program for messages and parameters.
* Managers similar to [[AS/400 object]]s, such as a directory to files and files consisting of metadata and records. Managers conceptually provide memory and processing resources for their contained objects.
* A client or server consisting of all the managers necessary to implement a full processing environment, supporting such aspects as directory services, security and concurrency control.

The initial version of DDM defined distributed file services.  It was later extended to be the foundation of [[DRDA|Distributed Relational Database Architecture]] (DRDA).

==Design patterns==
Challenges of object-oriented design are addressed by several methodologies. Most common is known as the [[Design Patterns (book)|design patterns codified by Gamma ''et al.'']]. More broadly, the term "[[design pattern (computer science)|design patterns]]" can be used to refer to any general, repeatable solution to a commonly occurring problem in software design. Some of these commonly occurring problems have implications and solutions particular to object-oriented development.

===Inheritance and behavioral subtyping===
{{See also|Object-oriented design}}<!-- not "further" because that article is mostly blather and does not even mention this -->
It is intuitive to assume that inheritance creates a [[program semantics|semantic]] "[[is a]]" relationship, and thus to infer that objects instantiated from subclasses can always be ''safely'' used instead of those instantiated from the superclass. This intuition is unfortunately false in most OOP languages, in particular in all those that allow [[mutable]] objects. [[Subtype polymorphism]] as enforced by the [[type checker]] in OOP languages (with mutable objects) cannot guarantee [[behavioral subtyping]] in any context. Behavioral subtyping is undecidable in general, so it cannot be implemented by a program (compiler). Class or object hierarchies must be carefully designed, considering possible incorrect uses that cannot be detected syntactically. This issue is known as the [[Liskov substitution principle]].

===Gang of Four design patterns===
{{Main|Design pattern (computer science)}}
''[[Design Patterns (book)|Design Patterns: Elements of Reusable Object-Oriented Software]]'' is an influential book published in 1995 by [[Erich Gamma]], [[Richard Helm]], [[Ralph Johnson (computer scientist)|Ralph Johnson]], and [[John Vlissides]], often referred to humorously as the "Gang of Four". Along with exploring the capabilities and pitfalls of object-oriented programming, it describes 23 common programming problems and patterns for solving them.
As of April 2007, the book was in its 36th printing.

The book describes the following patterns:

*''[[Creational pattern]]s'' (5): [[Factory method pattern]], [[Abstract factory pattern]], [[Singleton pattern]], [[Builder pattern]], [[Prototype pattern]]
*''[[Structural pattern]]s'' (7): [[Adapter pattern]], [[Bridge pattern]], [[Composite pattern]], [[Decorator pattern]], [[Facade pattern]], [[Flyweight pattern]], [[Proxy pattern]]
*''[[Behavioral pattern]]s'' (11): [[Chain-of-responsibility pattern]], [[Command pattern]], [[Interpreter pattern]], [[Iterator pattern]], [[Mediator pattern]], [[Memento pattern]], [[Observer pattern]], [[State pattern]], [[Strategy pattern]], [[Template method pattern]], [[Visitor pattern]]

===Object-orientation and databases===
{{Main|Object-relational impedance mismatch|Object-relational mapping|Object database}}
Both object-oriented programming and [[relational database management systems]] (RDBMSs) are extremely common in software {{As of|2006|alt=today}}. Since [[relational database]]s don't store objects directly (though some RDBMSs have object-oriented features to approximate this), there is a general need to bridge the two worlds. The problem of bridging object-oriented programming accesses and data patterns with relational databases is known as [[object-relational impedance mismatch]]. There are a number of approaches to cope with this problem, but no general solution without downsides.<ref name="RDMDBobjectmis">{{Cite web| first = Ted| last=Neward |title = The Vietnam of Computer Science| date=26 June 2006|accessdate=2 June 2010| publisher = Interoperability Happens| url=http://blogs.tedneward.com/2006/06/26/The+Vietnam+Of+Computer+Science.aspx}}</ref> One of the most common approaches is [[object-relational mapping]], as found in [[Integrated development environment|IDE]] languages such as [[Visual FoxPro]] and libraries such as [[Java Data Objects]] and [[Ruby on Rails]]' ActiveRecord.

There are also [[object database]]s that can be used to replace RDBMSs, but these have not been as technically and commercially successful as RDBMSs.

===Real-world modeling and relationships===
OOP can be used to associate real-world objects and processes with digital counterparts. However, not everyone agrees that OOP facilitates direct real-world mapping (see [[object-oriented programming#Criticism|Criticism]] section) or that real-world mapping is even a worthy goal; [[Bertrand Meyer]] argues in ''[[Object-Oriented Software Construction]]''<ref name="Meyer230">Meyer, Second Edition, p. 230</ref> that a program is not a model of the world but a model of some part of the world; "Reality is a cousin twice removed". At the same time, some principal limitations of OOP had been noted.<ref>M.Trofimov, ''OOOP - The Third "O" Solution: Open OOP.'' First Class, [[Object Management Group|OMG]], 1993, Vol. 3, issue 3, p.14.</ref>
For example, the [[circle-ellipse problem]] is difficult to handle using OOP's concept of [[inheritance (object-oriented programming)|inheritance]].

However, [[Niklaus Wirth]] (who popularized the adage now known as [[Wirth's law]]: "Software is getting slower more rapidly than hardware becomes faster") said of OOP in his paper, "Good Ideas through the Looking Glass", "This paradigm closely reflects the structure of systems 'in the real world', and it is therefore well suited to model complex systems with complex behaviours" (contrast [[KISS principle]]).

[[Steve Yegge]] and others noted that natural languages lack the OOP approach of strictly prioritizing ''things'' (objects/[[noun]]s) before ''actions'' (methods/[[verb]]s).<ref name="executioniKoN">{{Cite web| first = Steve| last=Yegge |title = Execution in the Kingdom of Nouns| date=30 March 2006|accessdate=3 July 2010| publisher = steve-yegge.blogspot.com| url=http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html}}</ref> This problem may cause OOP to suffer more convoluted solutions than procedural programming.<ref name="executioniKoN2">{{Cite web| first = Timothy| last= Boronczyk |title = What's Wrong with OOP| date=11 June 2009|accessdate=3 July 2010| publisher = zaemis.blogspot.com| url=http://zaemis.blogspot.com/2009/06/whats-wrong-with-oop.html}}</ref>

===OOP and control flow===
OOP was developed to increase the [[code reuse|reusability]] and [[software maintenance|maintainability]] of source code.<ref name="realisticcodereuse">{{Cite web| first = Scott| last= Ambler| title = A Realistic Look at Object-Oriented Reuse| date=1 January 1998| accessdate=4 July 2010| publisher = www.drdobbs.com| url=http://www.drdobbs.com/184415594}}</ref> Transparent representation of the [[control flow]] had no priority and was meant to be handled by a compiler. With the increasing relevance of parallel hardware and [[thread (computer science)|multithreaded coding]], developing transparent control flow becomes more important, something hard to achieve with OOP.<ref name="flaws">{{Cite web| first = Asaf| last= Shelly |title = Flaws of Object Oriented Modeling| date=22 August 2008|accessdate=4 July 2010| publisher = Intel Software Network| url=http://software.intel.com/en-us/blogs/2008/08/22/flaws-of-object-oriented-modeling/}}</ref><ref name="multithreadingisaverb">{{Cite web| first = Justin |last= James| title = Multithreading is a verb not a noun| date=1 October 2007|accessdate=4 July 2010| publisher = techrepublic.com| url=http://blogs.techrepublic.com.com/programming-and-development/?p=518}}</ref><ref name="multicore">{{Cite web| first = Asaf| last= Shelly| title = HOW TO: Multicore Programming (Multiprocessing) Visual C++ Class Design Guidelines, Member Functions| date=22 August 2008| accessdate=4 July 2010| publisher = support.microsoft.com| url=http://support.microsoft.com/?scid=kb%3Ben-us%3B558117}}</ref><ref>{{cite web|url=http://existentialtype.wordpress.com/2011/04/17/some-advice-on-teaching-fp/|title=Some thoughts on teaching FP|author=[[Robert Harper (computer scientist)|Robert Harper]] |publisher=Existential Type Blog|accessdate=5 December 2011|date=17 April 2011}}</ref>

===Responsibility- vs. data-driven design===

[[Responsibility-driven design]] defines classes in terms of a contract, that is, a class should be defined around a responsibility and the information that it shares. This is contrasted by Wirfs-Brock and Wilkerson with [[data-driven design]], where classes are defined around the data-structures that must be held. The authors hold that responsibility-driven design is preferable.

===SOLID and GRASP guidelines===

[[SOLID (object-oriented design)|SOLID]] is a mnemonic invented by Michael Feathers that stands for and advocates five programming practices:
* [[Single responsibility principle]]
* [[Open/closed principle]]
* [[Liskov substitution principle]]
* [[Interface segregation principle]]
* [[Dependency inversion principle]]

[[GRASP (object-oriented design)|GRASP]] (General Responsibility Assignment Software Patterns) is another set of guidelines advocated by [[Craig Larman]].

==Criticism==

The OOP paradigm has been criticised for a number of reasons, including not meeting its stated goals of reusability and modularity,<ref name="badprop"/><ref name="armstrongjoe"/> and for overemphasizing one aspect of software design and modeling (data/objects) at the expense of other important aspects (computation/algorithms).<ref name="stepanov"/><ref name="hickey"/>

[[Luca Cardelli]] has claimed that OOP code is "intrinsically less efficient" than procedural code, that OOP can take longer to compile, and that OOP languages have "extremely poor modularity properties with respect to class extension and modification", and tend to be extremely complex.<ref name="badprop">{{Cite journal| first=Luca| last=Cardelli|title=Bad Engineering Properties of Object-Oriented Languages |url=http://lucacardelli.name/Papers/BadPropertiesOfOO.html| year=1996| accessdate=21 April 2010| doi=10.1145/242224.242415| journal = ACM Comput. Surv.| volume=28| issn = 0360-0300| pages = 150| publisher = ACM| authorlink=Luca Cardelli| issue=4es}}</ref> The latter point is reiterated by [[Joe Armstrong (programming)|Joe Armstrong]], the principal inventor of [[Erlang (programming language)|Erlang]], who is quoted as saying:<ref name="armstrongjoe">Armstrong, Joe. In ''Coders at Work: Reflections on the Craft of Programming.'' Peter Seibel, ed. [http://www.codersatwork.com/ Codersatwork.com], Accessed 13 November 2009.</ref>

{{quote|The problem with object-oriented languages is they've got all this implicit environment that they carry around with them. You wanted a banana but what you got was a gorilla holding the banana and the entire jungle.}}

A study by Potok et al. has shown no significant difference in productivity between OOP and procedural approaches.<ref>{{Cite journal| url=http://www.csm.ornl.gov/~v8q/Homepage/Papers%20Old/spetep-%20printable.pdf| title=Productivity Analysis of Object-Oriented Software Developed in a Commercial Environment| last=Potok| first=Thomas|author2=Mladen Vouk |author3=Andy Rindos |journal=Software&nbsp;– Practice and Experience| volume=29|issue=10|pages=833–847 |year=1999 |accessdate=21 April 2010| doi=10.1002/(SICI)1097-024X(199908)29:10<833::AID-SPE258>3.0.CO;2-P}}</ref>

[[Christopher J. Date]] stated that critical comparison of OOP to other technologies, relational in particular, is difficult because of lack of an agreed-upon and rigorous definition of OOP;<ref name="DatePage650">C. J. Date, Introduction to Database Systems, 6th-ed., Page 650</ref> however, Date and Darwen have proposed a theoretical foundation on OOP that uses OOP as a kind of customizable [[data type|type system]] to support [[RDBMS]].<ref name="ThirdManifesto">C. J. Date, Hugh Darwen. ''Foundation for Future Database Systems: The Third Manifesto'' (2nd Edition)</ref>

In an article Lawrence Krubner claimed that compared to other languages (LISP dialects, functional languages, etc.) OOP languages have no unique strengths, and inflict a heavy burden of unneeded complexity.<ref name="lawrence">{{Cite web| last=Krubner| first=Lawrence| title=Object Oriented Programming is an expensive disaster which must end| url=http://www.smashcompany.com/technology/object-oriented-programming-is-an-expensive-disaster-which-must-end| publisher=smashcompany.com| accessdate=14 October 2014}}</ref>

[[Alexander Stepanov]] compares object orientation unfavourably to [[generic programming]]:<ref name="stepanov">{{Cite web| url=http://www.stlport.org/resources/StepanovUSA.html| title=STLport: An Interview with A. Stepanov| last=Stepanov| first=Alexander| accessdate=21 April 2010| authorlink=Alexander Stepanov}}</ref>

{{quote|I find OOP technically unsound.. It attempts to decompose the world in terms of interfaces that vary on a single type. To deal with the real problems you need multisorted algebras&nbsp;— families of interfaces that span multiple types. I find OOP philosophically unsound. It claims that everything is an object. Even if it is true it is not very interesting&nbsp;— saying that everything is an object is saying nothing at all.}}

[[Paul Graham (computer programmer)|Paul Graham]] has suggested that OOP's popularity within large companies is due to "large (and frequently changing) groups of mediocre programmers". According to Graham, the discipline imposed by OOP prevents any one programmer from "doing too much damage".<ref name="graham">{{Cite web| last=Graham| first=Paul| title=Why ARC isn't especially Object-Oriented.| url=http://www.paulgraham.com/noop.html| publisher=PaulGraham.com| accessdate=13 November 2009| authorlink=Paul Graham (computer programmer)}}</ref>

[[Steve Yegge]] noted that, as opposed to [[functional programming]]:<ref name="yegge">[http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html Stevey's Blog Rants]</ref>

{{quote|Object Oriented Programming puts the Nouns first and foremost. Why would you go to such lengths to put one part of speech on a pedestal? Why should one kind of concept take precedence over another? It's not as if OOP has suddenly made verbs less important in the way we actually think. It's a strangely skewed perspective.}}

[[Rich Hickey]], creator of [[Clojure]], described object systems as overly simplistic models of the real world. He emphasized the inability of OOP to model time properly, which is getting increasingly problematic as software systems become more concurrent.<ref name="hickey">Rich Hickey, JVM Languages Summit 2009 keynote, [http://www.infoq.com/presentations/Are-We-There-Yet-Rich-Hickey Are We There Yet?] November 2009.</ref>

[[Eric S. Raymond]], a [[Unix]] programmer and [[open-source software]] advocate, has been critical of claims that present object-oriented programming as the "One True Solution", and has written that object-oriented programming languages tend to encourage thickly layered programs that destroy transparency.<ref name="Eric S. Raymond 2003">{{cite web|url=http://www.catb.org/esr/writings/taoup/html/unix_and_oo.html|title=The Art of Unix Programming: Unix and Object-Oriented Languages|author=Eric S. Raymond|date=2003|accessdate=2014-08-06}}</ref> Raymond compares this unfavourably to the approach taken with Unix and the [[C (programming language)|C programming language]].<ref name="Eric S. Raymond 2003"/>

==Formal semantics==
{{see also|Formal semantics of programming languages}}
Objects are the run-time entities in an object-oriented system. They may represent a person, a place, a bank account, a table of data, or any item that the program has to handle.

There have been several attempts at formalizing the concepts used in object-oriented programming. The following concepts and constructs have been used as interpretations of OOP concepts:

*[[F-Coalgebra|co algebraic data types]]<ref name=poll97>{{cite web|last=Poll|first=Erik|title=Subtyping and Inheritance for Categorical Datatypes|url=http://www.cs.ru.nl/E.Poll/papers/kyoto97.pdf|accessdate=5 June 2011}}</ref>
*[[abstract data type]]s (which have [[existential types]]) allow the definition of [[module (programming)|modules]] but these do not support [[dynamic dispatch]]
*[[recursive type]]s
*encapsulated state
*[[Inheritance (object-oriented programming)|inheritance]]
*[[Record (computer science)|records]] are basis for understanding objects if [[function literal]]s can be stored in fields (like in functional programming languages), but the actual calculi need be considerably more complex to incorporate essential features of OOP. Several extensions of [[System F-sub|System F<sub><:</sub>]] that deal with mutable objects have been studied;<ref name="AbadiCardelli"/> these allow both [[subtype polymorphism]] and [[parametric polymorphism]] (generics)

Attempts to find a consensus definition or theory behind objects have not proven very successful (however, see Abadi & Cardelli, [http://portal.acm.org/citation.cfm?id=547964&dl=ACM&coll=portal ''A Theory of Objects'']<ref name="AbadiCardelli">{{Cite book| first=Martin| last=Abadi |title=A Theory of Objects| url=http://portal.acm.org/citation.cfm?id=547964&dl=ACM&coll=portal| year=1996| accessdate=21 April 2010| isbn = 0-387-94775-2| publisher = Springer-Verlag New York, Inc.| authorlink=Martin Abadi|author2=Cardelli, Luca }}</ref> for formal definitions of many OOP concepts and constructs), and often diverge widely. For example, some definitions focus on mental activities, and some on program structuring. One of the simpler definitions is that OOP is the act of using "map" data structures or arrays that can contain functions and pointers to other maps, all with some [[syntactic sugar|syntactic and scoping sugar]] on top. Inheritance can be performed by cloning the maps (sometimes called "prototyping").

==See also==
{{Portal|Computer programming}}

*[[Comparison of programming languages (object-oriented programming)]]
*[[Comparison of programming paradigms]]
*[[Component-based software engineering]]
*[[Design by contract]]
*[[Object association]]
*[[Object database]]
*[[Object modeling language]]
*[[Object-oriented analysis and design]]
*[[Object-relational impedance mismatch]] (and [[The Third Manifesto]])
*[[Object-relational mapping]]

===Systems===
*[[CADES]]
*[[Common Object Request Broker Architecture]] (CORBA)
*[[Distributed Component Object Model]]
*[[Distributed Data Management Architecture]]
*[[Jeroo]]

===Modeling languages===
*[[IDEF4]]
*[[Interface description language]]
*[[Lepus3]]
*[[Unified Modeling Language|UML]]

==References==
{{Reflist|2}}

==Further reading==
*{{Cite book
|first=Martin
|last=Abadi
|authorlink=Martin Abadi
|author2=[[Luca Cardelli]]
|year=1998
|title=A Theory of Objects
|publisher=[[Springer Verlag]]
|isbn=0-387-94775-2
}}
*{{Cite book
|first=Harold
|last=Abelson
|authorlink=Harold Abelson
|author2=[[Gerald Jay Sussman]]
|year=1997
|title=Structure and Interpretation of Computer Programs
|url=http://mitpress.mit.edu/sicp/
|publisher=[[MIT Press]]
|isbn=0-262-01153-0
}}
*{{Cite journal
|first = Deborah J.
|last = Armstrong
|date=February 2006
|title = The Quarks of Object-Oriented Development
|journal = Communications of the ACM
|volume = 49
|issue = 2
|pages = 123–128
|issn = 0001-0782
|url =http://portal.acm.org/citation.cfm?id=1113040
|accessdate =8 August 2006
|doi = 10.1145/1113034.1113040
}}
*{{Cite book
|first=Grady
|last=Booch
|authorlink=Grady Booch
|year=1997
|title=Object-Oriented Analysis and Design with Applications
|publisher=[[Addison-Wesley]]
|isbn=0-8053-5340-2
}}
*{{Cite book
|first=Peter
|last=Eeles
|authorlink=
|author2=[[Oliver Sims]]
|year=1998
|title=Building Business Objects
|publisher=[[John Wiley & Sons]]
|isbn=0-471-19176-0
}}
*{{Cite book
|first=Erich
|last=Gamma
|authorlink=Erich Gamma
|coauthors=[[Richard Helm]], [[Ralph Johnson (computer scientist)|Ralph Johnson]], [[John Vlissides]]
|year=1995
|title=Design Patterns: Elements of Reusable Object Oriented Software
|publisher=Addison-Wesley
|isbn=0-201-63361-2
}}
*{{Cite book
|first=Paul
|last=Harmon
|authorlink=Paul Harmon (management author)
|author2=William Morrissey
|year=1996
|title=The Object Technology Casebook - Lessons from Award-Winning Business Applications
|publisher=John Wiley & Sons
|isbn=0-471-14717-6
}}
*{{Cite book
|first=Ivar
|last=Jacobson
|authorlink=Ivar Jacobson
|year=1992
|title=Object-Oriented Software Engineering: A [[Use case|Use Case]]-Driven Approach
|publisher=Addison-Wesley
|isbn=0-201-54435-0
}}
*{{Cite book
|first=Alan
|last=Kay
|authorlink=Alan Kay
|title=The Early History of Smalltalk
|url=http://gagne.homedns.org/%7etgagne/contrib/EarlyHistoryST.html
}}
*{{Cite book
|first=Bertrand
|last=Meyer
|authorlink=Bertrand Meyer
|year=1997
|title=[[Object-Oriented Software Construction]]
|publisher=[[Prentice Hall]]
|isbn=0-13-629155-4
|url=
}}
*{{Cite book
|first=Rudolf
|last=Pecinovsky
|year=2013
|title=OOP - Learn Object Oriented Thinking & Programming
|publisher=Bruckner Publishing
|isbn=978-80-904661-8-0
|url=http://pub.bruckner.cz/titles/oop
|ref=harv
}}
*{{Cite book
|first=James
|last=Rumbaugh
|authorlink=James Rumbaugh
|author2=Michael Blaha |author3=William Premerlani |author4=Frederick Eddy |author5=William Lorensen
|year=1991
|title=Object-Oriented Modeling and Design
|publisher=Prentice Hall
|isbn=0-13-629841-9
}}
*{{Cite book
|first=Stephen
|last=Schach
|authorlink=
|year=2006
|title=Object-Oriented and Classical Software Engineering, Seventh Edition
|publisher=[[McGraw-Hill]]
|isbn=0-07-319126-4
}}
*{{Cite book
|first=Axel-Tobias
|last=Schreiner
|year=1993
|title=Object oriented programming with ANSI-C
|publisher=Hanser
|isbn=3-446-17426-5
|id={{hdl|1850/8544}}
}}
*{{Cite book
|first=David A.
|last=Taylor
|year=1992
|title=Object-Oriented Information Systems - Planning and Implementation
|publisher=John Wiley & Sons
|isbn=0-471-54364-0
}}
*{{Cite book
|first=Matt
|last=Weisfeld
|authorlink=|year=2009
|title=The Object-Oriented Thought Process, Third Edition
|publisher=[[Addison-Wesley]]
|isbn=0-672-33016-4
}}
*{{Cite book
|first=David
|last=West
|authorlink=|year=2004
|title=Object Thinking (Developer Reference)
|publisher=[[Microsoft Press]]
|isbn=0735619654
}}

==External links==
{{Wikiquote|Object-orientation}}
{{Wikiversity|at=Topic:Object-Oriented Programming}}
{{Wikibooks|Object Oriented Programming}}

*{{dmoz|Computers/Programming/Methodologies/Object-Oriented|Object-oriented programming}}
*[http://www.codeproject.com/Articles/22769/Introduction-to-Object-Oriented-Programming-Concep Introduction to Object Oriented Programming Concepts (OOP) and More] by L.W.C. Nirosh
*[http://software.intel.com/en-us/blogs/2008/08/22/flaws-of-object-oriented-modeling/ Discussion about the flaws of OOD]
*[http://java.sun.com/docs/books/tutorial/java/concepts/index.html OOP Concepts (Java Tutorials)]
{{Programming language}}
{{Software engineering}}

{{Use dmy dates|date=September 2010}}

{{Authority control}}
{{DEFAULTSORT:Object-Oriented Programming}}
[[Category:Object-oriented programming| ]]
[[Category:Programming paradigms]]
