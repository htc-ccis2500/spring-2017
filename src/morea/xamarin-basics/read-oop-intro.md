---
title: "Intro to Object-oriented Programming"
published: true
morea_id: read-oop-intro
morea_summary: "A general introduction to object-oriented programming concepts and terminology."
morea_type: reading
morea_sort_order: 1
morea_labels:
 - oop

---

# {{ page.title }}
If you're new to OOP (or if it's just been a while) here are a few key terms and concepts you should know.

## What is OOP?
In object-oriented programming we structure our code around objects. An object is conceptually a "thing" that you might imagine. Often these tie to physical things that we represent in our program code - like a Person, a Car, an InventoryItem, a Server, a UserGroup, etc.  The things we might represent in code with objects fall out of our application domain.  If we have a program to monitor a network of servers, we might have a Server object or a Router object, but we probably wouldn't have a Car object or a Person object.  On the other hand if we were managing a fleet of vehicles for a document delivery service, those Car and Person objects make more sense.

In object-oriented programming, the code is organized first into objects, but we still use the same tools - variables, functions, and control structures - that you are familiar with from non-object-oriented code.  However in object-oriented code, these variables and functions often exists inside of objects.  Variables that belong to objects are called __properties__ and functions that belong to objects are called __methods__.  

## Objects, Classes, & Instances
These three terms come up a lot in object oriented programming and understanding what each term means and how it is different from the others is important when discussing object object-oriented program code.

An __object__ is a conceptual thing.  It is the thing you are representing in your code by making a class.

A __class__  defines how to make an object.  It isn't an object itself, it just the definition of what that object is, like a blueprint or a template.  This definition is used to make instances of your object.

An __instance__ is one of many possible "real" (in the code sense) objects that could be made from your class.  

## Car Example
We might have a class define a Car to have some __properties__ like make, model and year.  These properties are things that help us differentiate one car from another.  They are things that the Car object *HAS*.  A Car HAS-A make. It HAS-A model.  It HAS-A (model) year.

We talked about things that objects *have*, their properties, but objects are usually also able to do things.  A Car wouldn't be much fun if it didn't drive, right?  We call these things that objects can do __behaviors__ and they correspond to methods that are defined for that object in our program code.  

To drive our car, we might add some *behaviors* to the class such as accelerate, brake, turn right, turn left, reverse direction, etc.  Behaviors are things that the object can do, and they correspond to __methods__ on the class.  We tend to use the word behavior when designing and method when coding.

Going back to the Car object, you might have behaviors to accelerate, brake, turn right, turn left, reverse direction, etc. When we talk about properties and behaviors, that is generally while considering the *design* of our object.  When designing, we are imagining what it might be like and deciding what pieces are important to our application. These behaviors are *implemented* or made real in the application by adding methods to the Car class definition.

Once our class is defined, then we can start making actual cars in our program code.  We might make a 2000 Toyota Celica, or a 2010 Mini Cooper, or a 2016 Honda Civic.  Each individual car we make is an *instance* of the Car class, and each one is also considered a (instance of a) Car object.  (I put that in parenthesis because it is true, but wordy and people usually leave that off.)


## Inheritance
Objects often (but not always) come in families.  There are many similarities between cars, trucks, SUVs, vans, etc.  Depending on what properties and behaviors we care about for each of those things, they might all be represented by the same class, and maybe that would be better called MotorVehicle?  (Naming is something that tends to change a lot in the design or imagining phase.)  

What about a motorcycle though? It's certainly similar in some ways.  It has the same properties and behaviors we mentioned above.  We would say that a Motorcycle __IS-A__ MotorVehicle, because it is shares all those properties and behaviors.  However, the Motorcycle is clearly visually different.  It only has 2 wheels, and it's not enclosed. There are many ways it is different from a car or truck.  Depending on the program, those things may or may not matter.  

If the differences do matter, we may want to create a different object to represent Motorcycles, but perhaps we want to use some of the same properties and behaviors that we had for our more generic MotorVehicle.  We can do that by extending the MotorVehicle class.  When we extend a class, we __inherit__ it's properties and behaviors.  We also say that the new class is a __child__ of the class we are extending.  The class we are extending is the __parent__ of the new class we are making.  

Classes can be extended to have a child class, and child classes can also be further extended.  Have you ever looked at animal taxonomy from a Biology book?  

{% include img-small.html url="/morea/xamarin-basics/images/redfox-taxonomy.png" alt="Taxonomic classification of a red fox" %}
(Image created by Annina Breen, used under the [CC BY-SA 4.0](CC BY-SA 4.0) license.)

If we had the same RedFox class in code, it might inherit properties & methods from Vulpes (its Genus) which might inherit from Canidae (its Family) which might inherit from Carnivora (its Order) and so on up to the Eukarya Domain. In practice though, class hierarchies in applications are often very shallow, only a few levels deep.  

There are several benefits to extending classes in this way.  By re-using the properties and methods in the base class, you are getting code that is already tested.  Changes that need to be made are made in one place (the parent class) and then shared by all the child classes.  New child classes can be added easily without affecting the existing parent class or any other child classes.  Changes to the parent affect all children, but changes to children do not affect the parent or any other children.

## IS-A vs. HAS-A
The IS-A and HAS-A language comes up frequently in object-oriented design and programming.  I will expect you to understand the differences between the two concepts.  This often falls out pretty naturally when talking about the objects.  The IS-A terminology is used for extending classes (inheritance), while the HAS-A terminology is used for instance variables, or properties of a class.

For example, if we are designing a car, which relationship would we use when thinking about the driver?  

A Car HAS-A Driver.  
OR  
A Car IS-A driver.  

Unless we've got self-driving cars, the statement a Car IS-A driver, doesn't make much sense, so it's more likely that our Car HAS-A driver.  That means we would give our Car a property (or instance variable) for the driver instead of having our Car class extend a Driver class.

## Polymorphism
Inheritance allows for sharing of properties and methods that are similar, but when you inherit from a parent class, you get all of those shared properties and behaviors.  What if some behavior isn't right for that child?  Methods on a parent class can be overridden (or altered) in a child class.  This allow some objects to behave differently based on its exact type.  

To explain this further, let's go back to animals.  Most (but not all) animals make noise, but they all make different noises.  Perhaps we have a parent animal class that defines a method for make noise and to keep it simple (and allow for the silent types) let's say it does nothing.  The Animal class make noise method, makes no noise.

Now let's say we have a class Lion, which inherits from Animal.  Here we can alter the behavior of the make noise method so that the lions roar.  When we add another class for Wolf, we can have them howl.  If we add another class for Cow, it can moo, and Ducks can quack, etc.

Inheritance allows us to say these are all animals, but they all behave differently when we tell them to make noise.  That is polymorphism.  An animal object may have *many forms* - lions, wolves, ducks, cows - and they can show different behaviors when they do the same action.  

Polymorphism in applications is generally not as fun to describe as the animal example, but you might think about all the various types of files on your computer.  You might have text files, music files, videos, pictures.  Those are all files, right?  You might expect that you could define a class for a File.  A behavior on that class might be open.  When you open a video file you expect that to open in a way that is different than a text file.  That is also polymorphism.
