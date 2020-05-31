# Introduction

> Go is an open source programming language that makes it easy to build simple, reliable, and efficient software. - Excerpts from Golang.org

### Why need Go

#### Computers Evolved but programming languages haven't

Intelligent machines has evolved. Today we see plathora of intelligent machines; be it computers, mobile devices, IoT devices; interacting with web apps, services and platforms. These intelligent machines comes in different shapes, sizes and varying capabilities; be it Android/iOS powered machines of different screen sizes, resolutions, CPU cores and memory. But when it comes to programming languages and tools out there; there are still lot to cover; to keep up with the evolutions of machines. For example there are bunch of programming languages and tools that still can not leverage all CPU cores at once. Forget about concorrunt programs even achieving parallelism is tough using existing tools.

In addition to capabilities as explained, we also have developers who love to curate efficient products and organisations wants to go to market early to cash in this cut throat compition. Hence this world needed a technology or tool that is simple to curate, fast to prototype, easy to understand, internet aware yet have complex abstraction to leverage capabilities of intelligent machines out there. And this is where **Golang** comes into the picture

#### Choice: Rapid Development or Performance

As a software curator, one have always faced dilemma while choosing the tech stack to develop a software. Given the combinations of tchnology available, one can either choose rapid development or Performance. 

If one does choose Rapid development to hit market early, they need to make choices again to imrove performance if there software become used widely. Take an example of [Twitter](https://twitter.com), early on they used Ruby and Rails for rapid development but after growth they had to rethink their technologu stack

#### Need to scale on the go 

As explained earlier; with existing bunch of technologies if one go for rapid development, performance had to be forgone or to get performance rapid development is thing not known. For example, C is technology that could be made to leverage all CPU cores, but it is neither suited for rapid development nor easy to manage the line of code that is required manage to develop complex software exist today

Similarly, if one chosses Ruby or NodeJS, rapid development can be done but performance is something farfetched for complex projects

#### Built in Concurrency \(Go routines/channels\)

Golang is developed while keeping the challanges in developing software in 21st centuary. While it allows one to leverage complex underlying hardware architecture, at the same time has enough high level abstraction needed for rapid development.

Golang has inbuilt go routine that are lightweight, self contained and scheduled by go itself to achieve parallelism, leveraging all available cores  and at the same times channels make them concurrent while sharing data and states among them as and when required

#### Composition over Inheritance

Many of us have already been worked on some kind of technology using OOPs concept and are familier with Inheritance. Go does not support inheritance while it does implement composition. So what's the difference?, one asks.

Composition is something smaller parts, that when put together makes a big part of that. To understand the difference lets take an example. A vehicle is generic class that can have attributes like fuel, engine, tyres and behavior like start, stop, accelerate. And this can be inherited into Car's definition, since car would have all the properties it has and adds some more, that makes it a car.

While in composition, one creates a component that when put together makes a thing. For example tyres, engines are component, they can be used in car, trucks and pickup alike. That's the difference

Components may not be much better than inheritance, both have there goods and bads. But one thing an experienced programmer understand is that components are tiny parts; that makes it easier to maintain and reuse. Components are also not bound to particular definition, like tyres are not just to be used in vehicle always, they have other uses as well. In inheritance one puts a generic framework that makes it hard to use for things that does not fall well in that framework definition, while components are like, libraries/modules, one can fit these inti anything and they would make there properties and behaviour available.

Another difference is, in Inheritence child class knows what class it is inheriting from, but child component never knows whom it is providing there services to. That's when thought well, makes it decoupled and in programming its a good thing.

#### Modern, Fast and comes with powerful set of standard libraries

Open source has always been on the rage, one would find plathora of solutions out there that would add to existing technologies to leverage something that was either not available when technology was implemented not meant for that

With this comes a lot of libraries/extension/plugins that adds to confusion of developer, sometimes are not well thought or implemented. This makes it risky using third party libraries and plugins

So when go was being written, authors has very well thought out plan for making all heavily used components/features as part of standard libraries. \(e.g \`net-http\`\)



