# Introduction

> Go is an open-source programming language that makes it easy to build simple, reliable, and efficient software. - Excerpts from Golang.org

### Why need Go

#### Computers Evolved but programming languages haven't

Intelligent machines have evolved. Today we see a plethora of intelligent machines; be it computers, mobile devices, IoT devices; interacting with web apps, services and platforms. These intelligent machines come in different shapes, sizes and varying capabilities; be it Android/iOS powered machines of different screen sizes, resolutions, CPU cores and memory. But when it comes to programming languages and tools out there; there is still a lot to cover; to keep up with the evolutions of machines. For example, there are a bunch of programming languages and tools that still can not leverage all CPU cores at once. Forget about concurrent programs even achieving parallelism is tough using existing tools.

In addition to capabilities as explained, we also have developers who love to curate efficient products and organizations want to go to market early to cash in this cut-throat competition. Hence this world needed technology or tool that is simple to curate, fast to prototype, easy to understand, internet aware yet have complex abstraction to leverage capabilities of intelligent machines out there. And this is where **Golang** comes into the picture

#### Choice: Rapid Development or Performance

As a software curator, one has always faced a dilemma while choosing the tech stack to develop software. Given the combinations of technology available, one can either choose rapid development or Performance. 

If one does choose Rapid development to hit the market early, they need to make choices again to improve performance if their software becomes widely used. Take an example of [Twitter](https://twitter.com), early on they used Ruby and Rails for rapid development but after growth, they had to rethink their technology stack

#### Need to scale on the go 

As explained earlier; with existing bunch of technologies if one goes for rapid development, the performance had to be forgone or to get performance; rapid development is a thing not known. For example, C is the technology that could be made to leverage all CPU cores, but it is neither suited for rapid development nor easy to manage the line of codes that are required to develop complex software that exists today

Similarly, if one chooses Ruby or NodeJS, rapid development can be done but performance is something farfetched for complex projects

#### Built in Concurrency \(Go routines/channels\)

Golang is developed while keeping the challenges in developing software in the 21st century. While it allows one to leverage complex underlying hardware architecture, at the same time has enough high-level abstraction needed for rapid development.

Golang has inbuilt goroutines, that are lightweight, self-contained and scheduled by go itself to achieve parallelism, leveraging all available cores  and at the same times channels make them concurrent while sharing data and states among them as and when required

#### Composition over Inheritance

Many of us have already been worked on some kind of technology using OOPs concept and are familiar with Inheritance. Go does not support inheritance while it does implement composition. So what's the difference?, one asks.

Composition is something smaller parts, that when put together makes a big part of that. To understand the difference lets take an example. A vehicle is a generic class that can have attributes like fuel, engine, tires and behavior like start, stop, accelerate. And this can be inherited into Car's definition since the car would have all the properties it has and adds some more, that makes it a car.

While in composition, one creates a component that when put together makes a thing. For example tires, engines are components, they can be used in car, trucks and pickup alike. That's the difference

Components may not be much better than inheritance, both have there pros and cons. But one thing an experienced programmer understands is that components are tiny parts; that make it easier to maintain and reuse. Components are also not bound to a particular definition like tires are not just to be used in vehicle always, they have other uses as well. In inheritance one puts a generic framework that makes it hard to use for things that do not fall well in that framework definition, while components are like, libraries/modules, one can fit these into anything and they would make there properties and behavior available.

Another difference is, in Inheritence child class knows what class it is inheriting from, but child component never knows whom it is providing there services to. That's when thought well, makes it decoupled and in programming its a good thing.

#### Modern, Fast and comes with a powerful set of standard libraries

Open source has always been on the rage, one would find a plethora of solutions out there that would add to existing technologies to leverage something that was either not available when technology was implemented not meant for that

With this comes a lot of libraries/extensions/plugins that add to confusion of developers, sometimes are not well thought or implemented. This makes it risky using third party libraries and plugins

So when go was being written, authors have a very well thought out plan for making all heavily used components/features as part of standard libraries (e.g `net-http`)
