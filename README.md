# Node Built-in Debugger Workflow

I spent a good chunk of time searching for a very basic workflow for the [built-in node debugger](http://nodejs.org/docs/latest/api/debugger.html). After searching for a simple REPL-like solution and reading countless StackOverflow posts suggesting I use [node-inspector](https://github.com/node-inspector/node-inspector), I decided to write this quick post for anyone else looking for something similar.

## Basic Example

```javascript
// node-builtin-debugger/app.js
var test = 'hi';
debugger
```

If you've used tools like [Pry](http://pryrepl.org/) for Ruby, you'd expect that the debugger will pause after the 'test' variable goes through assignment at which point you could inspect the value of 'test' from the debugger. It's possible, but not quite as straight-forward as you'd expect.

From the command line:
```
$ cd node-builtin-debugger
$ node debug app
```

![Var](http://i.imgur.com/nGzTH64.png)

At this point, you can notice from the command line that 'var' is highlighted. I assumed that the program would only pause on my debugger breakpoints, but it seems to step into each method. To continue, type `cont`.

![Continue](http://i.imgur.com/ve1T3SI.png)

Now we're at our breakpoint, but we can't just inspect variables from here.

![Inspect](http://i.imgur.com/YNvqXsA.png)

We need to first call the REPL which will load the Node REPL in our current context.

![REPL](http://i.imgur.com/YbuawIs.png)

That's it! Like I said, it's a basic workflow, but it's not completely obvious.