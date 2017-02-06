---
title: "OO Programming in C#"
published: true
morea_id: read-oop-csharp
morea_summary: "An overview of Object-Oriented Programming in C#."
morea_type: reading
morea_sort_order: 2
morea_labels:
 - oop
---

## {{ page.title }}
{{ page.morea_summary }}

## Prerequisites
Before you can make sense of Object-Oriented Programming (OOP) in C#, you'll need to have some idea what OOP is:

- [Intro to Object-oriented Programming]({{ site.baseurl }}/morea/xamarin-basics/read-oop-intro)

## Additional Reference
More information on Object-Oriented Programming in C# can be found on the Microsoft Developer Network:

- [Object-Oriented Programming](https://msdn.microsoft.com/en-us/library/mt656686.aspx)  

{% include alert.html type="warning"
  content="The code we will be building for our mobile applications is object-oriented.  You'll need to understand the basic concepts of OOP and the appropriate syntax used in C#."
%}

## Basic Animal Example
Let's create a basic Animal class.  We define a class using the keyword `class` and wrap the body of the class in curly braces {}.

{% highlight csharp %}
class Animal
{

}
{% endhighlight %}

Next let's add a property for the animal's age.  We will use an auto-implemented property that provides a trivial get & set for us.  This public value is backed by an internal private value.  With auto-implemented properties, there is always a get and set.

{% highlight csharp %}
class Animal
{
    public int Age { get; set; }
}
{% endhighlight %}

What if we don't want to have either a get or set, or if we want to add additional code?  Then we need to write out the code ourselves.  Let's do that for the name property, which we will only allow set in the constructor.

First we define the property with a private (hidden) field `_name` and then the public accessor.  This time however we have to define the get behavior explicitly.  Note that we do not define a set.

{% highlight csharp %}
class Animal
{
    public int Age { get; set; }

    // Property with only get and no set
    private String _name;
    public String Name {
        get { return _name; }
    }

}
{% endhighlight %}

Next, we'll add the constructor which will set the name.  The constructor is similar to a method, but it __MUST__ have the name of your class and does not return a value.  In the constructor, we set the private property for the name, `_name` and give the age a default value of 0.

{% highlight csharp %}
class Animal
{
    ... previous code hidden ...

    // Class constructor
    public Animal(String name)
    {
        this._name = name;
        this.Age = 0;
    }
}
{% endhighlight %}

Finally, let's add a method to the class so the animals can make some noise.  Because there isn't just one way an Animal can make noise, we define this method as `virtual` so that the inheriting child classes can override or change its behavior.

{% highlight csharp %}
class Animal
{
  ... previous code hidden ...

    // Generic behavior with virtual method
    // Each child class needs to override to change behavior
    public virtual void makeNoise()
    {
        Console.WriteLine("...");
    }
}
{% endhighlight %}

The full code for the Animal class is shown below:

{% gist mbMosman/9337264d4d2cd70c32e0e067273be393 Animal.cs %}



## Inheritance
Next let's inherit from the Animal class to add Lions & Bears.  For each child class, we will override the behavior of the makeNoise method to be appropriate for each specific Animal.

First let's create the Lion class, extending (or inheriting from) our Animal class. To do this, after the name of our new class we use a colon followed by the name of the class we want to extend.

{% highlight csharp %}
class Lion : Animal
{

}
{% endhighlight %}

Because we added a constructor that takes an argument, the name, we need to ensure a value is passed into the Animal part of our constructor for the Lion class.  There is no need to *do* anything inside the constructor, so we just include the empty curly braces { }. Our parent Animal class is handling all of our properties for us in this example.

{% highlight csharp %}
class Lion : Animal
{
    public Lion(String name):base(name) { }
}
{% endhighlight %}

Finally, we need to override our makeNoise method so that our lions can roar.  Note that we use the `override` keyword to indicate that we are changing the behavior from the parent class.

{% highlight csharp %}
class Lion : Animal
{
    ... previous code hidden ...

    // Here we override the base class method to
    // make our lion's roar.
    public override void makeNoise()
    {
        Console.WriteLine("Roar!");
    }
}
{% endhighlight %}


The full code for the Lion class is shown below:

{% gist mbMosman/9337264d4d2cd70c32e0e067273be393 Lion.cs %}

The bear class is similar, but we have the bears say grrr:

{% gist mbMosman/9337264d4d2cd70c32e0e067273be393 Bear.cs %}


## Making and Using Objects
Now that we have these classes, how can we use them?  Let's create a Lion called Simba.

To create an *instance* of our class, we use the keyword `new` with the constructor.  
Here we must give the name as an argument to the constructor.

{% highlight csharp %}

    // Make a new lion
    Lion lion = new Lion("Simba");

{% endhighlight %}

We can get and set the lion's age by using the accessors.  We use object notation syntax to do this, the variable reference, followed by a `.`, followed by the property accessor name.
{% highlight csharp %}

    // Set and get auto-implemented age
    lion.Age = 5;
    Console.WriteLine("Simba is " + lion.Age + " years old.");

{% endhighlight %}

What about the lion's name?  We can see it:
{% highlight csharp %}

    Console.WriteLine("The lion's name is " + lion.Name);

{% endhighlight %}

However we cannot set it.  This will give an error:
{% highlight csharp %}

    lion.Name = "Can't do this";

{% endhighlight %}

Once we have created an instance of a class, we can call methods on that instance.  To do this, we use object notation syntax, just like for setting a property, but with the method name.

{% highlight csharp %}

    lion.makeNoise();

{% endhighlight %}

### Object Initializer Syntax
There is another way that we can create an object and set properties (that are not arguments for the constructor) at the same time.  This is called *Object Initializer* syntax.

Create a new Bear named Baloo and set his age to 12.
{% highlight csharp %}

    Bear bear = new Bear("Baloo")
    {
        Age = 12
    };

{% endhighlight %}

### Polymorphism
When an object can behave in different ways or *show different forms*, this is called Polymorphism.  It is a fundamental part of object-oriented programming.  To illustrate this, we can make an array that holds references to Animal objects.  

Remember that a Lion IS-A Animal and that a Bear IS-A Animal because they inherit from the Animal class.  Because of this, we can put our lion and bear into the Animal array.  

{% highlight csharp %}

    Animal[] animals = { lion, bear };

{% endhighlight %}

When we do this, it's no longer clear what the exact type of the items in the array are, only that they follow the rule IS-A Animal.

Now, let's use a loop to go through the array and call the makeNoise method.  

{% highlight csharp %}

    Console.WriteLine("Let's see all the animals make noise!");
    Console.WriteLine("Can you guess what animal they are?");
    foreach (Animal a in animals)
    {
        Console.WriteLine("Meet " + a.Name + ".");
        a.makeNoise();
    }

{% endhighlight %}

When the code runs, as you might expect our lion roars and the bear grrrs.  While this might be what you would expect, it is actually some rather nifty OOP *polymorphism* magic that you should not take for granted.  

The full Program.cs code is shown below:
{% gist mbMosman/9337264d4d2cd70c32e0e067273be393 Bear.cs %}
