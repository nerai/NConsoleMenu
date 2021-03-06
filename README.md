[![nuget](https://img.shields.io/nuget/v/NConsoleMenu.svg?label=nuget)](https://www.nuget.org/packages/NConsoleMenu/)

# NConsoleMenu
Console menus are easy to build, complex menus are supported, and using them is simple and quick.

NConsoleMenu is a low-ceremony framework for building console menus in .NET. Instead of manually prompting the user for input and parsing it, you define commands in a short, structured and comprehensive way, and let the library handle the rest.

NConsoleMenu aims for low overhead - simple stuff should be simple to implement. If you don't use a feature, you don't need to know anything about it. At the same time, complex scenarios are supported. Large menus can easily be split into several classes. Self-configuration occurs entirely in the background. You do not have to worry about all the annoying details involved in larger menus, it will just work.

Similar to a command shell, NConsoleMenu is built for rapid usage. Commands can be entered abbreviated, a smart parser enables even partial matching. Typing fast and blind is supported - the program will try and prevent you from entering a wrong command by accident. And if the user of your menu got lost at any point, a powerful help feature is integrated.

NConsoleMenu uses the permissive MIT license.


## Quickstart

A single command is comprised of a keyword (selector), an optional help text describing it, and, most importantly, its behavior. The behavior can be defined as a simple lambda.

	var menu = new CMenu ();
	menu.Add ("test", s => Console.WriteLine ("Hello world!"));
	menu.Run ();

	$ test
	Hello world!

To create a command with help text, simply add it during definition. Use the integrated "help" command to view help texts.

	menu.Add ("time",
		s => Console.WriteLine (DateTime.UtcNow),
		"Writes the current time");

	$ time
	2015.10.01 17:54:38
	$ help time
	Writes the current time

NConsoleMenu keeps an index of all available commands and lists them upon user request via typing "help". Moreover, it also automatically assigns abbreviations to all commands (if useful) and keeps them up-to-date when you later add new commands with similar keywords.

	$ help
	Available commands:
	e   | exit
	h   | help
	q   | quit
	ti  | time
	te  | test
	Type "help <command>" for individual command help.
	$ te
	Hello world!



## Further reading

### Common use cases

Refer to [common use cases](doc/basics-and-help.md) for information on:

* Creation and use of basic commands
* Offering help to users (it's automated!)
* Less typing thanks to automated abbreviations
* About case sensitivity

### Big menus

Read up on [building complex menus](doc/nesting.md).

* Inner commands
* Nested menus and default commands
* Sharing code between items
* Short and concise initialization of menu trees

### Input

[About the input queue, immediate & passive mode](doc/input.md)

* Immediate mode: Accessing all commands in a single keystroke
* Accessing and modifying the input queue
* Promptless mode: Only allow scripted input
* For conditional commands, see [here](doc/conditional-commands.md)

### Output

[Changing, formatting, redirecting or cloning console output](doc/output.md)

* Connecting NConsoleMenu output with your logging framework of choice.

### Example project
The source code contains an [example project](doc/example_project.md). It offers commands, which illustrate several (more or less advanced) use cases. It may be useful to reference them in your own projects.

### Advantages
An [overview of the benefits of NConsoleMenu](doc/advantages.md).



## Project history and developer information

Another (much larger) project of mine uses a somewhat complex console menu, and I finally got annoyed enough by repeated, virtually equal code fragments to refactor and extract those pieces of code into a separate project. As I figured it was complete enough to be useful to others, I called it NConsoleMenu and put it on github.

In the future, there are certainly a lot of things to improve about this library, and I would definitely not call it complete or even particularly well made. The changes and issues found on this project are mostly caused by improvements and requirement changes in said larger project. I update NConsoleMenu with the relevant changes in parallel when I find the time and will continue to do so for the foreseeable future.

I'm happy to hear if you found this useful, and am open to suggestions to improve it.

