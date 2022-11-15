# TypeShell project

## Introduction
TypeShell is the project aiming to improve the usability of the usual CLI.

At the moment this file contains the overall "wish-list" of the features we want to bring with the TypeShell.

## The shortcomings of the TE + Bash
We are all used to interact with the OS through the 
1) Terminal Emulator (TE);
2) Shell program.

The shell (typically bash or zsh or something even more decent) is responsible for processing the user input.
It defines programming language (either self-made like bash, or external one like python-shell) and just runs the interpreter every time you type a line.

Terminal emulator is responsible for displaying the input-output pairs of the typed commands.
It could also perform in another mode (non-canonical) which is used by some utils like `screen`.

Today these two parts of the one system (which we are used to call CLI) are not integrated in any sense apart from pressed keys events.
You could run any shell in any TE.
This design comes with the pros:
- Unification;
- Simplicity.

However, I believe there are cons too.
Lack of the integration prevents us to build more complex communication scenarios.
For instance, text which is printed to the screen is just a text.
It does not hold any relation to the object it was before printing.
The best modern TEs could do is to catch the URLs and ask system to open the web browser when user clicks it.
Maybe there are a bit more functionality actually, but I hope you get what I'm talking about.
We could formulate this in a few words: there is **no types** of the printed objects.
Everything which is printed is text. I know that it perfectly fits with the general Unix philosophy: everything is file with text.

_But what if we could go beyond and add typing? Not just to the interpreter but to the printed text too._

## Wishlist
### Types
So the first thing-to-improve is **typing**.

What typing could give us?
- **Safety**.
In statically typed languages, type checking is performed before the program is run.
While there is no guarantee that type-checking could catch all the errors, it sometimes catches important ones.
- **Interactivity**
If everything printed to the TE was typed, you'd create a lot of interactions with it.
Want to open special editor if the printed text is JSON? Okay.
Want to iterate over **objects** printed by previous command with your `Ctrl+↑` and copy-paste one of them to the new command?
No problem.
Want to auto-prettify YAML by clicking on it? I hope you get my point.
- **Customizibility**
You could set up your own representation of different types.
Display errors, strings, paths, URLs, floats, integers, lists as you want rather than as it was hardcoded in the app you're running.

As you can see, types are the bridge between the program and the representation.
Why not to construct one?

### Async execution
Given a usual TE + shell you have very few options:
- Run commands synchronously, e.g. one by one;
- Run command asynchronously with `&`.
Output would be unrecognizably mixed among different commands;
- Run command and "pause" it with `Ctrl+Z`. Output is mixed again;

That's pretty all?
If you know any other way to async your work (I mean your work, not computer work like with pipes), please let me know.

What I consider as a **wish** in this section is a system very similar to "Jupyter" one.
If you're familiar with it, you could skip the following spoiler.
<details>
    <summary>Jupyter</summary>
    Jupyter provides us a number of "cells" with separate input-output areas on the one web page.
    Cells have common scope so the variables initialized in one cell are available in other cells within the one "notebook" (note that Python has no variable declarations).
    Cells could be run separately in any order (also you could run one cell many times in row).
    You could switch between them with ease and run them all consistently with a single keyboard shortcut. 
</details>

There are shortcomings of Jupyter of course.
Printed text is still a text, and it works in a web browser, which we consider unacceptably costly for the purposes of the TE.
But **the very idea of splitting something to separate cells** fits greatly to the system we want to bring.

What does splitting to cells give us?
- Control and manage the outputs of the commands which are run asynchronously;
- Re-run any cell at any moment without retyping or copy-pasting something;
- Save your whole setting like you do with Jupyter notebook.

Note that this is already implemented to the certain extent with windowed TEs (like iTerm).
What is lacking again is integration between cells which we believe will give this idea a new breath.

## Conclusion
I hope that this wish list will grow, and finally reach the size of [SRS](https://en.wikipedia.org/wiki/Software_requirements_specification).
After that I believe we'll be able to implement it and make our wishes real.

**If you have any thoughts or suggestions upon any topic presented here, please feel free to express them via any communication channel (PR, issue, email, twitter) you'll find.**