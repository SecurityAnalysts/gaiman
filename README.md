# Gaiman Engine and Programming Language

![Gaiman: Text based advanture games engine and programming language](assets/banner.svg)

[![Build and test](https://github.com/jcubic/gaiman/actions/workflows/build.yaml/badge.svg)](https://github.com/jcubic/gaiman/actions/workflows/build.yaml)
[![Coverage Status](https://coveralls.io/repos/github/jcubic/gaiman/badge.svg?branch=master)](https://coveralls.io/github/jcubic/gaiman?branch=master)
[![LICENSE GPLv3](https://img.shields.io/badge/license-GPLv3-blue.svg)](https://github.com/jcubic/gaiman/blob/master/LICENSE)

[Gaiman: Storytelling Text Based Game Engine and Programming Language](https://github.com/jcubic/gaiman)

Main part of Gaiman is a minimalist programming language and main purpose is to help create
[Text Adventure Games](https://en.wikipedia.org/wiki/Interactive_fiction). But it can also be used
to create any interactive CLI applications (Web Based Terminal applications).
It support browser based CLI applications and in the future also native command line.

## Installation

```
npm install -g gaiman
```

## Usage

```
gaiman -o directory input.gs
```

This will compile your source file and generate `dir/index.html` and `dir/index.js` files.
And you can open generated html file in browser and run the game.

## Examples


This is Hello world Gaiman DSL example:

```ruby
echo* "Hi, What is your name?", 50 # Typing animattion with 50ms delay
let name = ask "name? "
echo "Hello $name, nice to meet you."
```

More advanced example:

```ruby
def ask_email(message)
   let reply = ask message
   if reply =~ /y|yes/i then
      echo "OK"
   else if reply =~ /n|no/i then
      echo "FAIL"
   else
      global(message)
   end
end

def global(command)
   if command =~ /help/ then
      echo "available commands help"
   else if command =~ /ls/ then
      echo get "/exec?command=ls"
   else
      echo "wrong command"
   end
end

if cookie.visited then
  if cookie.USER_NAME then
    echo "hello $user"
  else if cookie.EMAIL then
    echo "Will contact with with any updates"
  else
    echo "Do you want me to contact you with updates?"
    let confirm = ask "yes/no: "
    if confirm =~ /y|yes/i then
      echo "what is your name?"
      let command = ask "name: "
      if command then
        let user = command
        cookie.user = command
        let response = post "/register", { "name" => user, "email" => email }
        if response then
          echo "Welcome $user. You're successfully registered"
        end
      end
    end
  end
end
```

More examples in [examples directory](https://github.com/jcubic/gaiman/tree/master/examples)
See [Reference Manual](https://github.com/jcubic/gaiman/wiki/Reference-Manual)


## Live Demo

See [Gaiman Playground](https://gaiman.js.org/)

## Operator precedence

| Operator  | Description                              |
|-----------|------------------------------------------|
| []        | array and object access                  |
| ()        | parentheses grouping                     |
| * / %     | Multiplication, division, modulo         |
| + -       | Addition (or concatenation), subtraction |
| < > <= >= | boolean compare                          |
| == !=     | equal, not equal                         |
| and       | Boolean and                              |
| or        | Boolean or                               |
| not       | Boolean not                              |

## Roadmap

See Wiki [TODO & Roadmap](https://github.com/jcubic/gaiman/wiki/TODO-&-Roadmap).

## Name and Origin

Name came from [Neil Gaiman](https://en.wikipedia.org/wiki/Neil_Gaiman),
Author of novels, comic books, graphic novels and films. Great storyteller.

You can read about the origin of the languguage in the begining of the article:
* [How to create programming language that compiles to JavaScript](https://hackernoon.com/creating-your-own-javascript-based-programming-language-has-never-been-easier-wju33by)

## Acknowledge

Logo use:

* Font [Calling Heart](https://www.dafont.com/calling-heart.font)
  by [Lettersiro Studio](https://www.dafont.com/lettersiro-studio.d7440)
* Clipart [Book with bookmarks](https://openclipart.org/detail/280709/book-with-bookmarks)
  by [Kevin David Pointon](https://openclipart.org/artist/Firkin)

## License

Released under GNU GPL v3 or later<br/>
Copyright (c) 2021 [Jakub T. Jankiewicz](https://jcubic.pl/me)
