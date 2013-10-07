---
title: Why am I making Yeah?
layout: post
---
Making a video game tends to be a [long, tedious, frustrating process][igtm]. The overarching reason I am making [Yeah][yeah] is to change that. Yeah is a Ruby video game framework with a focus on optimizing the process of creating a game.

Modern video game development tools fall between two extremes: the statically typed compiled languages with native media APIs, and the drag-and-drop game creation programs.

<svg id="game-tools-spectrum">
  // horizontal line
  <line x1="5%" x2="95%" y1="50%" y2="50%" />
  // left arrow head
  <line x1="5%" x2="7.5%" y1="50%" y2="55%" />
  <line x1="5%" x2="7.5%" y1="50%" y2="45%" />
  // right arrow head
  <line x1="95%" x2="92.5%" y1="50%" y2="55%" />
  <line x1="95%" x2="92.5%" y1="50%" y2="45%" />
  // ticks
  <line x1="10%" x2="10%" y1="52.5%" y2="40%" />
  <line x1="30%" x2="30%" y1="60%" y2="47.5%" />
  <line class="major"x1="50%" x2="50%" y1="55%" y2="40%" />
  <line class="hilite" x1="60%" x2="60%" y1="60%" y2="46%" />
  <line x1="70%" x2="70%" y1="52.5%" y2="40%" />
  <line x1="90%" x2="90%" y1="60%" y2="47.5%" />
  // labels
  <text x="5%" y="25%">C++ with
    <tspan x="5%" y="35%">media APIs</tspan>
  </text>
  <text x="23%" y="70%">Java/C# with
    <tspan x="23%" y="80%">media APIs or</tspan>
    <tspan x="23%" y="90%">game library
  </text>
  <text x="40%" y="15%">Python/JavaScript/
    <tspan x="40%" y="25%">ActionScript with</tspan>
    <tspan x="40%" y="35%">game library</tspan>
  </text>
  <text class="hilite-text" x="57%" y="70%">Yeah</text>
  <text x="65%" y="15%">Development environments
    <tspan x="65%" y="25%">with a domain-specific</tspan>
    <tspan x="65%" y="35%">language, map editor...</tspan>
  </text>
  <text x="80%" y="70%">Drag-and-drop
    <tspan x="80%" y="80%">game creators</tspan>
  </text>
</svg>

Technology on the right side of the spectrum is typically designed to help people without much programming experience make video games, though it is generally thought that to create a serious game, your tools need to lean to the left side.

One reason for this is performance. I do not expect Yeah, a Ruby framework, to ever beat C++ and OpenGL in this area. However, I believe that when one is starting a video game or any creative work, it is best to be able to experiment and iterate as quickly and easily as possible. The early focus of a game should be creating interesting and satisfying mechanics. Thinking about performance details at this point is a complete waste of time and inspiration. Down the line when it makes sense to hunt down bottlenecks, one might find that [Ruby is surprisingly optimizable][rbopt], and can even be extended with C. Another interesting thing is that the creator of Ruby is currently working on a [Ruby implementation that compiles Ruby code down to C][mruby], which may give Yeah games a nice performance boost in the future.

A broader reason is that friendlier tools get in the way of advanced users. They tend to be approachable and easy to learn, but as one becomes wiser in the ways of game development, features that were once perceived as nice and helpful become speed bumps. Eventually it becomes worthwhile to just move on to more generic, lower level tools for greater control. However, I believe that it is not intrinsic of friendlier tools to eventually hinder their users. In fact, a framework that is on the friendly side would be the *ideal* tool for constructing quality video games *if made correctly*. This means...

1. Designing an API that makes decisions for you based on best practices by default, but also makes it simple to override them. This will minimize boilerplate without being restrictive, letting one focus on the design of their game.

2. Making the code open source, modular, and comprehensively tested. Any serious modern software development tool will have these traits.

3. Building visual tools like sprite and map editors as individual, substitutable programs, rather than being combined into one mega-app.

4. Optimizing for productivity for when one knows what they are doing, rather than for when they do not.

Here are some specific ideas I have for the framework:

* A `yeah new` command that generates a project file structure à la Ruby on Rails.

* Dynamic properties for entities. If an entity has a #position, it should implicitly have #x, #y, and #z shorthands. If it has a #velocity, it should implicitly have a corresponding #speed and #direction.

* Ability to write code once and run it anywhere by interfacing with the underlying platform as a black box. The first bindings will be to the native desktop, and later there will be a set for the web powered by [Opal][opal]. Hypothetically, anything could be a Yeah platform.

* A `yeah build` command that offers headache-free building and packaging.

* A sprite and map editor that is optimized for efficient keyboard control, like vim and dwm.

* Implicit linkage between entities and visuals with matching file names in the project file structure.

* A debug mode with live code and data reloading.

* A way to implement networked multiplayer that is simpler than manually sending packets around. [BYOND][byond] has an interesting approach to this - it networks games implicitly - but it uses a high-latency approach that is far from ideal for many games.

* RSpec integration to make automated video game testing easy with test maps, input simulation, and frame-/time-based expectations. Automated testing is nearly unheard of in video game development, but the field would definitely benefit from being more aware of it.

* Color symbols generated from [Wikipedia's lists of colors][wikicol]. For example, :sae_ece_amber for "SAE/ECE Amber (Color)".

Those are some of the bigger ideas, but I plan on making this the ideal tool for game development through not only big ideas but also consideration of every detail. My intention with Yeah is to make game development maximally pleasant and efficient and to facilitate the creation of inspired, creative video games, by veterans and newcomers alike.

Yeah is [on Github][yeah] and is very much a work in progress at the time of writing.

[igtm]: http://www.thunderboltgames.com/feature/burden-of-digital-dreams
[yeah]: https://github.com/skofo/yeah
[rbopt]: http://www.adit.io/posts/2013-03-04-How-I-Made-My-Ruby-Project-10x-Faster.html
[mruby]: https://github.com/mruby/mruby
[opal]: http://opalrb.org
[byond]: http://www.byond.com
[wikicol]: https://en.wikipedia.org/wiki/List_of_colors:_A%E2%80%93F
