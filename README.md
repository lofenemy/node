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


Event loop is a kind of infinite cycle. Each iteration is called as 'tick'.  Here there is analogie of tack of CPU. But unlike tacts, the cycle of event loop can go on for long time. 

On each tick, event loop checks 3 conditons
1) Is there the process with undefined or unresolved setTimeout, setInterval or setImmediate or callback for that.
2) Is there unfinished or unresolved operations with large process (such as FS modules and etc) // fs module works with file system of operation system and actually it's the one of the most weight operations for Node.
3) Is there pendng operations with OS (such as listening of ports, requests) 

Is the event loop structure of data and manipulation of that? Or just aproach to resolve some issues? Or just big function which run every tick?
Is that written on C++? 
What kind of problems resolve it?
