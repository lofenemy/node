# Advanced concepts NodeJS

// In this article I will mention Node meaning NodeJS.

Here will be described a few important Advanced Node concepts.
Before getting started, let's take a look at very base introduce to understand what Node is and what the purpose of using it.

Node is a platform for creating server side application using javascript language.
It was created as powerful system, which allows using all js concepts without any problems with performance.

Because of not too deep elaboration of javascript language as language for server, it could create performance issues.
That's why in order to make Node platform as performanced as possible, developers needed to use other approaches apart from JS.

Node largely contained the C++ code, written to efficiently interact with modules such as a file system, internet system (http modules), etc.
In the majority of cases C++ is used as a powerful tool to make massive (in terms of time or resources) algorithms/processes as powerful and effective as possible.

One of the most useful libraries inside of Node is library libuv which is written on C++ fully.
The second very important component of Node is V8 engine which is used as a core engine for Google Chrome browser.
It’s a necessary core of iterperatating and involving javascript code.


// Event loop. 
// The require function executes all code inside of module as usual js code then caches it and imports that as usual variable
// When event loop has no any functions for executing it shuts down, until any function is received as function for executing.


Event loop is a kind of infinite cycle.
Each iteration is called 'tick'.
There is analogy of the tack of CPU. But unlike tacts, the cycle of event loop can go on for long time. 

On each tick, event loop checks 3 conditons
1) Is there the process with undefined or unresolved setTimeout, setInterval or setImmediate or callback for that. Or should we execute callback relevant callback from callback queu.
2) Is there unfinished or unresolved operations with large process (such as FS modules and etc) // fs module works with file system of operation system and actually it's the one of the most weight operations for Node.
3) Is there pendng operations with OS (such as listening of ports, requests) 

Is the event loop structure of data and manipulation of that? Or just aproach to resolve some issues? Or just big function which run every tick?
Is that written on C++? 
What kind of problems resolve it?

Node is Signle Threaded, but some Node modules are not.
Some libuv functions can execute outside of Event loop of Node and be more efficient.
Node has additional thread to execute some of heavy tasks.

Variable process.env.UV_THREADPOOL_SIZE controls the number of threadpools which will be runned as space for execution.

"Thread pool work scheduling
libuv provides a threadpool which can be used to run user code and get notified in the loop thread. This thread pool is internally used to run all file system operations, as well as getaddrinfo and getnameinfo requests.

Its default size is 4, but it can be changed at startup time by setting the UV_THREADPOOL_SIZE environment variable to any value (the absolute maximum is 1024).

Changed in version 1.30.0: the maximum UV_THREADPOOL_SIZE allowed was increased from 128 to 1024.

The threadpool is global and shared across all event loops. When a particular function makes use of the threadpool (i.e. when using uv_queue_work()) libuv preallocates and initializes the maximum number of threads allowed by UV_THREADPOOL_SIZE. This causes a relatively minor memory overhead (~1MB for 128 threads) but increases the performance of threading at runtime."


// All fs modules have access for threadpool.

Requests such as http, htttps use OS system to listen or make requests.
Fs moduls use threadpool of libuv (4 by default)


const https = require('https');
const crypto = require('crypto');

const start = Date.now() // return number of miliseconds

function doRequest() {
  https.requests('https://gogle.com', res => {
    res.on('data', () => {})
    res.end('end', () => {
      console.log('request', Date.now() - start)
    })
  .end()
}

function doHash() {
  crypto.pbkdf2('a', 'b', 100000, () => {
    console.log('hash', Date.now() - start)
  })
}


function doFs() {
  fs.readFile('example.js', 'utf-8, () => {
    console.log('fs', Date.now() - start)'
  })
}

doRequest();
doFs();
doHash();
doHash();
doHash();
doHash();


For sending request machine uses internal OS system. It means that it doesn't use neither libuv worker nor Node's event loop.
It means that sending request(ping) doesn't work of event loop and can't block the working of Node. 







