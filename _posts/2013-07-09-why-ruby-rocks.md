---
layout: post
title: Why Ruby rocks
---
It's a common notion that the only good reason to learn Ruby is to learn its killer framework, Ruby on Rails. As such, people are often hesitant to learn Ruby, especially if they are already happy with its step-cousin Python, which is more popular and has a wider variety of frameworks and libraries. However, Ruby is a uniquely pleasant and versatile language and I believe that it has much potential waiting to be unlocked.

There are various interwoven reasons for this, but the biggest thing that makes Ruby shine in my eyes is its *objects*.

In a Ruby object, all variables are internal; the only way to interface with an object from the outside is by calling its methods. So to manipulate an object's variable, one would use getter and setter methods. Since method calls do not need a pair of parentheses and it is convenient to define methods with operators, a couple of methods can practically be a variable! With Ruby, one is liberated from accessing properties using `.getHealth()` or `.get('health')`, or not really being sure whether one is dealing with an instance method (`.health()`) or an instance variable (`.health`) until after they look it up. One never has to write daemonic incantations like `programmer.set('sanity', programmer.get('sanity') - 1)`.

Instead, the whole thing can look something like this:

{% highlight ruby %}
class Person
  def initialize
    @sanity = 50
  end

  def sanity
    @sanity
  end

  def sanity=(val)
    @sanity = val
  end
end

programmer = Person.new
programmer.sanity += 1000000
programmer.sanity #=> 1000050
{% endhighlight %}

I think that's great.

Notice that `Person` is instantiated by calling its `new` method, instead of passing the class into a `new` operator as is typical. This works because classes are actually objects in Ruby, along with other things you wouldn't expect to be objects, like strings and integers. As a result, there are fewer special operators and global functions (like ones to convert between strings and integers) in favor of that functionality residing within objects.

An object doesn't even need to have its methods formally defined. If an object has a `method_missing` method, it will handle any method calls that don't match its defined methods.

{% highlight ruby %}
class Useless
  def method_missing(name, *params)
    puts "Sorry, I wish I could #{name}..."
    if params.any?
      puts "Here, you can have your #{params.join(', ')} back."
    end
  end
end

Useless.new.reticulate :splines
#=> "Sorry, I wish I could reticulate..."
#=> "Here, you can have your splines back."
{% endhighlight %}

This combination of things and other things I haven't mentioned allows one to write very elegant and enjoyable interfaces with Ruby. This has been fully exploited in the back-end web development world with Ruby on Rails and its ecosystem, but I'm certain that Ruby can find a home in other fields, like game development. Overall, I have a feeling that Ruby's power has not been fully appreciated yet, and I wish to see more people give Ruby a shot and use it to create awesome opinionated tools for things that could use them.

To get started, I highly recommend reading *[Programming Ruby - The Pragmatic Programmer's Guide](http://www.ruby-doc.org/docs/ProgrammingRuby/)*.
