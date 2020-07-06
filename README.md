# Advanced concepts NodeJS

// In this article I will call NodeJS as Node and will mean it as NodeJS as well.

Here will be described a few important Advanced Node concepts.
Before getting start, let's take a look at very base introduce to understand what NodeJS is and what the purpose of using it.

Node JS is a platform for creating server side application using javascript language.
It was creating as powerful system, which allows to use all js concepts without any problems with performance.

Because of not too deep elaboration of javascript language as language for server, it could create performance issues.
What's why to make Node platform as performanced as possible, developers needed to use other approaches beside js.

NodeJS largely contained the C++ code, written to efficiently interact with modules such as a file system, internet system (http modules) and etc.
In majority of cases C++ uses as a powerful tool to make massive (in terms of time or resources) algorithms/processes as powerful and efficient as possible.

The one of the most useful library inside of Node is library libuv which is written on C++ fully.
The second a very important component of Node is V8 engine which is using as core engine for Google Chrome browser. It’s a necessary core of iterperatating and involving javascript code.


// Event loop. Concurency in Node with through libuv library.
// Require function execute all code inside of module as a usual javascript code then caches it and import that as usual variable
// When event loop has no any functions for executing it shots down, until any function will be received as function for executing.
