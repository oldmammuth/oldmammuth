---
layout: post
title: "Rust: Easygoing Tutorial"
ref: rust_easygoing_tut
date: 2017-08-24
categories: Rust tutorial
lang: en
---

Define an easy tutorial... Anyway, I'll try!

## Installation, duh!

This is actually a no-brainer: you definitely need to install the rust environment before getting to the hello-world (-,-) part of it!

```shell
curl https://sh.rustup.rs -sSf | sh
```

Windows users, gret news ahead, just check out the link: [https://rustup.rs](https://rustup.rs). However, take notice of the following disclaimer: 
```
This tutorial is biased toward a *NIX shell. With the opportune mods, it will work also in a Windows CMD or Poweshell, yet I have no knowledge of those. Sorry!
```

## 'nuff said: "hello to you, gorgeous world!"

Let's make a ``` main.rs``` file inside a ```helloworld``` folder.

```shell
mkdir helloworld && cd helloworld
touch main.rs
```
Let's edit that ```main.rs``` however we want, even with a ```cat > main.rs <<EOF``` (Well, you could theoretically use also an IDE or whatever, your choice...)

Anyways the code to write down is the following:
```rust
fn main() {
    println!("Hello, world!");
}
```
Yup!, the ```!``` after ```println``` is totally there, part of the code shtuff...

Now, let's compile and execute (in one move... just in case it fails... well, at this stage it shouldn't fail unless of a typo)

```shell
rustc main.rs && ./main
```
And our glorious ```Hello, world!``` should appear at last!

## Some explaining-me time!

Nothing too fancy:
- Like ```C```, *rust*'s entry point for execution is the ```main``` function.
- Functions are declared with the ```fn``` preceding the name of the function; it can have parameters in parentheses, and return type (nothing in this case). The funcition body goes inside the curly braces. Moreover, it is considered good rust style to start the first curly brace on the same line as the name of the function, separating the curly brace from the parentheses with a blank space.
- Style again: 4 spaces istead of a tab for indentation
- ```println```'s got a exclamation mark: it's not a command, it's a *macro*, not a function (yeah, the printing on the shell is handled by a macro, what a twist on cliches!)
- Last thing to notice: the old c-style languages crush... you already spotted the semicolon, didn't you?

## So what's different from other langs, again?

Well, at this point of the computer science scenario, many languages and tools are converging, and so on, and so forth, but that stuff is for another reflection.
Right now, let's concentrate on rust...

First of all, I like more the show-then-tell process, so let's start all over again.

### Cargo
Rust comes with a package manager as part of the whole package (sorry, it was totally intended!). Smart choice, since, again, the convergence is pointing toward easier packaging; yet while for older language it is hard: many choices of a packaging solution, and you never know which one will stick around longer; for new languages like *rust* and *go* it is easier to start with a package manager as part of the official language environment.

Thus, let us take advantage of it! 

We can start again with another directory called *wecargotheworld*, or *helloworldofcargos*, or, again, *hellocargoworld*...
I myself would set for *helloc*, but wor the purposes of this tutorial, let's try the following:

```shell
mkdir hellocargo && cd hellocargo
pwd
cd .. && rmdir hellocargo
ls hellocarg*
```

Yes, I know! I forgot to tell you that *cargo* will take care of creating the folder... Ok, simply do the following:

```shell
cargo new hellocargo --bin
```
That will create a folder with cargo, ready to take on a new project that will release an executable: yeah, the ```--bin``` part of it! Guess what would be the command for a library? ```--lib``` Bingo! **you got it wrong**: for a library just don't put the ```--bin```: apparently library creation is the default cargo mode!

Now let's ```cd hellocargo``` and start messing around.

### Exploring our cargo

A quick ```ls```-ing around (or ```tree``` if you have it installed), tells us the following revealing stuff:
```
├── Cargo.toml
├── .git
│   ├── ...
├── .gitignore
└── src
    └── main.rs
```

There's a ```.gitignore``` and a ```.git``` directory!? Hello, you gorgeous, may I offer you a *git-cola*???

Next: we got a ```main.rs``` under the ```src``` folder, that looks like the following:
```rust
fn main() {
    println!("Hello, world!");
}
```
Don't I know you already? Didn't we meet somewhere? (go ahead and change the string ```"Hello, world!"``` with a ```"Hello, Cargo!"```)

There's too a *Cargo.toml* (TOML = Tom's Obvious, Minimal Language... I would have guessed a Totally Overrated Markup Language, but as it is, I stand corrected)
The syntax is (obviosly) INI, it's like a INI++

Mine looks like:

```toml
[package]
name = "hellocargo"
version = "0.1.0"
authors = ["oldmammuth <******@gmail.com>"]

[dependencies]
```

Well... it actually got my correct name and email from git...
(you can use ```CARGO_EMAIL``` and ```CARGO_NAME``` env variables to change them if you'd like to)

Obviously (thanks Tom, now I will keep repeating *obviosulsy* the entire tut...) the ```[dependencies]``` section is empty, since we as yet don't need any, and the info on the package is quite scanty (name, version, and author only)

So, now, how do we run it?
Well, one possibility is building the project (```cargo build```) and running it from the newly created folder (```./target/debug/hellocargo```), but an actual:

```shell
cargo run
```
will decide for itself wether the project needs building, or re-building, or none of the above, then it will run it. 
Give it a try... 

(Notice that with cargo run we level up development in Lin,Win, and Mac, since the same commands are valid in them all... So here it is where I lift my disclaimer, and we ca happily go on programming all like a big family!)

Incidentally, a ```tree ./target/debug/``` will reveal that *cargo* can do a whole lot more than just compile the project nice and sweet for you...

We also got a new *Cargo.lock* file in the project root alongside the *.toml* file responsible to mantain info through the various building phases of you project.

#### Note on release
If you want to build for release, the you definitely need to run a 
```shell
cargo build --release
```
which will build the project inside the *./target/release/* and optimize the final executable.

### Let's get messy
Enough with the Cargo talk, let's get going a meatier example! (I <3 meat lover's pizza!)

#### My brand new greeting prog
Just create a new cargo project (```cargo new greetings --bin```), or modify the existing one.

**src/main.rs**:
```rust
/* 
 * file: src/main.rd
 */
/// Program to make good first impressions on your *rust* environment
/// Go ahead, and `` ` ```` ` ```` ` ``cargo run`` ` ```` ` ```` ` `` it!
use std::io;

fn main() {
    let mut yourname = String::new();
    // ask for an imput
    println!("What is your name?");
    io::stdin().read_line(&mut yourname)
        .expect("Huston, we have a problem!");
    // print it out
    println!("Hello, {}!", yourname);
}
```

### As a (not so) good politician used to say: "let me explain it!"
What's going on in the code above is the following.

#### Comments: 
- Block comments: ```/* a comment */```
- Single line: ```// comment till the end of line```
- Documenting comment (Markdown is totally acceptable here): ```/// A documenting comment can be handled with *rustdoc* tool```

#### Use
```rust
use std::io;
```

Thus, apart from the cargo system of dependencies, *rust*'s got also a standard library called ```std```.

We can import in our program's scope a package with the *use* kewyword.

```std::io``` is responsible for the I/O ops, as its name suggests.

#### let (mut)
Rust declares "variables" with the ```let``` keyword, even though they are all constants. To make them variable (mutable) you need to specify it with the ```mut``` keyword. And notice that variables are declared with ```let```, not with ```var``` since they are immutable by default....

This is in stark contrast to other languages where the variables are mutable by default, but can be made immutable with a ```const``` keyword; but rust is very much concerned in type safety, and what's more safe than declaring everything constant by default? I kinda like it in principle, because coming from c/c++, boys how many times I forgot/didn't care to declare as ```const``` my constants, which is a (minor, but yer real)threat to type safety...

#### ...and there's a String library here too...
Boys, how I wish statically typed languages were not so annoying with strings! Really? are we still in the '70 caring for each bit of byte we could spare, with the default typing systems? Why not create a regular text type to hold text, without resorting to masked arrays of chars and so on and so forth?

Anyway there you have it, a line wich declares a mutable variable of type String (text), using a "*static method*", ```new()```, which in rust is known as *associated function*, because is a function associated to a type (static method is a way to refer to them in other langs)

```rust
let mut yourname = String::new();
```
Notice too our old friend *semicolon*!

#### What-a 'bout I/O?

1. ```io::stdin()``` is responsible for the standard input (STDIN)
2. ```.read_line()``` reads a whole line (till carriage return) from STDIN: it saves it into a mutable variable: notice how we call it with a ```&mut``` which means it is mutable(mut) and passed by reference(the ampersand). Wait a moment. Did we not already established that yourname was going to be mutable? Well yes, but variables are passed to function as immutable and by value... but in this case we need it to store the result of the question to the user, so it needs to be passed by value, and to be mutable, so ve have to specify it woth a ```&mut``` before the variable name...
3. *read_line()* in reality returns something more than just the line sought for... you can get to handle errors as well; so we do it in a simple way with the ```expect()``` func, wich gets a string to return in case of error...

The result is a line
```rust
io::stdin().read_line(&mut yourname).expect("Huston, we have a problem!");
```
which in the code we broke in 2 just before the *.expect()* part. We could have done it in 3, as in:
```rust
io::stdin()
    .read_line(&mut yourname)
    .expect("Huston, we have a problem!");
```
``````

#### Printing out the variable
Easy peasy: just like in the new *python* way, with placeholders...

```rust
println!("Hello, {}!", yourname);
```

where the curly braces are a placeholder for the var passed to the println macro.
Notice that *println* can paste many var inside a string, with multiple placeholders, such as:

```rust
println!("Hello, {}, are you {}?", yourname, guessedage);
```
And this concludes the program's execution

## Conclusions
Obviously, this is just dipping the toes in the rusty waters...

I still am toying around with rust, and I don't know wther make it my next language crush or not... but as yet there are many things I like and few I wish they'd done better... Anyways, you can't please anyone with any language, can you?

Thus, for now: happy Rust coding, folks!
