# 77-777's OCaml - The Manual

> Pragmatic information about Functional Programming and OCaml.

> Written with a belief in "learning by example" and "acquire through osmosis" approach.

<br>
<br>
<br>


DRAFT.

Work in progress. Early stage. Will change abruptly.

<br>
<br>

## Audience

Click the sections below to expand.

<br>
<br>

<details>
  <summary> For Intermediate Programmers </summary>

---

### Spawning a project & building

* Ecosystem & Environment
  * dune - primary build and project manager
  * opam - package manager
  * LSP - server for your editor/IDE to provide intellisense.
  * ocamlc - the Ocaml Compiler. 

Please use your respective *nix package manager.

`sudo apt-get install ocaml utop opam`


`dune init proj your_project_name`


`dune build` # cd inside.


`dune exec your_project_name`

<br>
<br>
<br>

### Console Arguments & Printing

```ocaml
open Sys;;
(* For `argv` array and print_endline*)

let () =
    let my_args = argv and
        let first_arg = argv.(0) and
        let second_arg = argv.(1) and
        let arg_length = Array.length args in
            print_endline (string_of_int arg_length);;
```

### File IO

```ocaml
open Sys;;
(* For input_line, close_in and close_out, stdout .*)

(* Reading files. *)
let () =
    let my_file = "file-to-open.txt" in
    let input_channel = open_in my_file in
        let line = input_line input_channel in
            print_endline line;
            close_in input_channel;
            exit 0;;

            (* Need while loop example here. *)


(* Writing files. *)
let () =
    let my_file = "file-to-open.txt" in
    let output_channel = open_out my_file in
        Print.fprintf output_channel "Some Message.";
            flush stdout;
            close_out output_channel;
            exit 0;;
```

### Directory & File Operations

* also list files in directory, todo.

```ocaml
(* Directory & File Manipulation *)
let () =
    let my_dir = mkdir "test" 777 ();;

    (*
        > functions from Sys module.

        is_directory ...
        file_exists ...
        remove ...
        rename ...
        mkdir ...
        rmdir ...
    *)
```

### Data Type Conversion

```ocaml
(* Typecasting. *)

let () =
    let some_string = "240" in
        let some_int = string_of_int some_string in
            let some_float = float_of_int some_int in
                let some_integer_logic = int_of_bool true in
                    exit 0;;
```

### String Handling

```ocaml
(* You can also use the ^ operator for concatenation. *)

let () =
    let my_string = String.concat "Hi" " there." and
    let bool_val = String.equal my_string "Hi there." and
    let tokens = String.split_on_char '_' "Hi_there." in

        let len = String.length "Test." and
        let token_length = Array.length tokens and
        let substring = String.sub "mountain" 0 4 and
        let contains = String.contains "gah" 'c' and
        let trimmed = String.trim " spaces out " in
            ...
            (* 
                String.starts_with ...
                String.ends_with ...
                String.map ...
            *)
```

### Threading & Process Handling

```ocaml
(* Executing other programs. *)

let () = 
    let return_val = command "echo \"Hi\"";;

(* Creating Threads *)

let () = 
    let 

(* Manipulating Processes *)

let () = 


```

### Sockets

```ocaml
open Sys;
open Unix;

(*Synchronous*)
let () =
    let ipaddr = "127.0.0.1" and
    let port = 8080 and
    let sock = socket AF_INET SOCK_STREAM 0 in
        connect sock (ADDR_INET(ipaddr, port));
        match fork () with
            | 0 -> send sock data len
            | _ -> some error.

(*Asynchronous*)
let () =
    todo.
```

### GUI

```ocaml
open Tk;;

let spawnWidgets parent = 
    let btn = Button.create 
        ~text: "Click me" 
        ~command: (fun () -> closeTk ()) parent;
    pack [btn];

let setupWnd wnd title xy = 
    Wm.title_set wnd title;
    Wm.geometry_set wnd xy;

let () = 
    let main_wnd = openTk () in
        setupWnd main_wnd "GUI Application" "400 x 200" ();
        spawnWidgets wnd ();

    mainLoop ();;
```

### Web Requests

```ocaml
(* Example provided by https://github.com/anmonteiro/piaf *)

open Piaf;;
open Lwt_result.Syntax;;

let get_sync url = 
    Lwt_main.run begin
        print_endline("Sending request...");

        let* response = Client.Oneshot.get (Uri.of_string url) in
            if (Status.is_successful response.status) then
                Body.to_string response.body
            else
                let message = Status.to_string response.status in
                Lwt.return (Error (`Msg message))
    end

let () =
    match get_sync "https://example.com" with
        | Ok body -> print_endline body
        | Error error -> let message = Error.to_string error in
                            prerr_endline ("Error: " ^ message)
    
```

### Web Framework

```ocaml
(* Example provided by https://aantron.github.io/dream/ *)
  
open Dream;;
  
let hello who = 
    <html>
        <body>
            <h1>Hello, <%s who %>!</h1>
        </body>
    </html>

let () = 
    Dream.run
        @@ Dream.logger
        @@ Dream.router [
            Dream.get "/" (fun _ -> Dream.html (hello "world"));
        ]
    
```
      
### Web Automation

```ocaml
(* Example provided by https://github.com/art-w/ocaml-webdriver *)

module W = Webdriver_cohttp_lwt_unix
open W.Infix

let test =
  let* () = W.goto "https://github.com/art-w/ocaml-webdriver" in
    let* commits = W.find_first `xpath "//a[@href='/art-w/ocaml-webdriver/commits/master']//strong" in
      let* nb = W.text commits in
        let nb = int_of_string nb in
          Printf.printf "number of commits = %i\n%!" nb ;
          W.return ()
      
let host = "http://127.0.0.1:4444"
      
let () = 
  Lwt_main.run (W.run ~host Capabilities.firefox_headless test)
```

### Data Structures

```ocaml

```

### Logging
```ocaml

```

### Config Storage

```ocaml
(* API provided by external library - config-file, get via OPAM. *)

open Config;;

let () =
  ...

```

### Regex & Levenshtein

```ocaml

let () =
  let regex = Str.regexp "^regex$" in
    let result = Str.string_match regex "your_string" 0
    
let () =
  let first_str = "this" and second_str = "that" in
    let distance = Levenshtein.S.distance first_str second_str
```

### Cryptography
      
```ocaml
open Cryptokit;;
      
let () =
  let plain_text = "my message" and
  let cipher_text = "" and
  let key = "my key" in
      let aes_cipher = new Cryptokit.Block.aes_encrypt key in
        aes_cipher#transform
        ...
```

### Parsing HTML/JSON/XML
      
* HTML/XML

```ocaml
(* Example provided by https://aantron.github.io/lambdasoup/ *)
      
open Soup;;

let () = 
  let soup = read_channel stdin |> parse in
    soup $ "title" |> R.leaf_text |> print_endline;

    soup $$ "a[href]"
    |> iter (fun a -> print_endline (R.attribute "href" a));

    let ul = soup $ "ul" in
      ul $$ "li"
      |> iter (fun li ->
        trimmed_texts li |> String.concat "" |> print_endline)
```

* JSON
      
```ocaml
(* Example provided by https://github.com/ocaml-community/yojson *)
      
open Yojson;;

let () =
  let json_str = {|
    {
      "number" : 42,
      "string" : "yes",
      "list": ["for", "sure", 42]
    }
  |} in
      let json = Yojson.Safe.from_string json_str in
        Format.printf "Parsed to %a" Yojson.Safe.pp json
```

### Error Handling & Exceptions

### Timers, Events, Promises

Lwt.

### Database Access / ORM

### Graphics

### Keywords in OCaml

```ocaml
(* Declarations of variables and functions*)
let, in, and, where, function, fun, ref

(* Control Flow and switches *)
if, else, elseif, match, with, catch, begin, end

(* Loops *)
for, to, do, while, rec

(* Arrays *)
array

(* Structures, Variants & OOP *)
type, class, object, struct, val, method, mutable, of

(* Modules *)
open, module, external, include

(* Types *)
int, string, float, bool, bytes, list, char, unit, tuples, array, exn, format, option, records, ref, variants, objects

Fancy, Pair, Boring, Any, None, Some, Nothing, ()/unit, True, False, Empty
```

### Symbols in OCaml

* State Symbols

```ocaml
<- (* Assignment of data/state to mutable IO (e.g arrays or variables in objects) *)
;; (* Terminate expression in utop toplevel. *)
; (*Separate record fields and terminate expression in code.*)
_ (* Anonymous / ambiguous slot for "any" variable *)
arr.(0) (* Index access *)
```

* Structure Symbols

```ocaml
:: (* Append to a list *)
[| a ; b ; c |] (* Create a list *)
( * ) or (a : b) (* Create a tuple *)
:= (* Create a reference *)
| (* Pattern matching and variants. *)
@@ (* Function composition. Where f(x) is f x, f @@ x is just f x *)
-> (* Lambda *)
$ (* Contextual symbol *)
|> (* Similar to bash piping. Call a function, pass the result to the next function. myFunction |> myOtherFunction |> someFunction *)

(* Lists *)
let myEmptyList = [1; 2; 3];

(* Tuples *)
let myTuples = (a : "b" : 3);

(* Labels *)
~someLabel:int
```

* Operator Symbols

```ocaml
(* These two below are exactly the same. *)
(+) 3 6;; (* Infix function/symbol operator *)
3 + 6;; (* Prefix function/symbol operator *)

^ (* Concatenate strings *)
= (* Is the equality operator (==) *)
<> (* Is the not equal to operator *)
~ (* Labeling *)

** (* Exponential *)

(* Comparison *)
!=
>
<
<=
>=
!
```

* Misc Symbols

```ocaml
# (* Equivalent to accessing methods from object e.g myObject#myMethod *)
! (* Negation *)

1_000_000;; (* Comma/underscore notation *)
1,000,000;; (* Comma/underscore notation *)

0.5 *. 4.0;; (* Floats *)
0.5 /. 4.0;;(* Floats *)
```

<br>
<br>

</details>

<details>
  <summary> For Beginner Programmers </summary>

---

### Types & Records

```ocaml
(* The phantom type *)
type dog;;

(* The simple type declaration *)
type number = int;;

(* The record type definition *)
type person = { name: string; age: int; employed: bool };;

(* The variant type creation (enum, polymorphism/generic, constraints) *)
type animal = dog | wolf | cat | rat | bird;;

type salary = Some int | Nothing;;

(* Type parametrization (templates) *)
type paramType actualType = { field_member: paramType };;

(* Type granular modelling/specification *)
type Magic = Number of Int | Number of Float;;

(* Making a record's types mutable *)
type person = { mutable name: string; mutable age: int; employed: bool };;

(* First Class Fields *)
todo
```

### Modules

```ocaml
(* Declaration *)
module Vehicle = 
struct
    type speed = int
    type colour = string

    let drive () = 
        ...;;
    
    let get_speed =
        ...;;

    let get_colour = 
        ...;;
end;;

(* Import *)
open Vehicle;;

(* Usage *)
Vehicle.drive;;
```

### Functions

```ocaml
(* "Official" Functional declaration *)
let myFunction = fun x y z -> x + y + z;;

(* Most Common, Synctatic Sugar, Functional declaration *)
let myFunction x y z = ...;;

(* Functional declaration with explicit type *)
let myFunction x : int y : float z : string = ...;; (* What about labels and naming the arguments? *)

(* Functional declaration with labelled arguments (agnostic of position) *)
let myFunction ~fileDest ~fileSrc = ...;;

(* Pure Functional declaration with "function" having built-in pattern matching *)
let myFunction = function
   | Some y -> y
   | None -> 0
;;

(* Function calling *)
myFunction 1 2 3;;

(* Recursive functions *)
let rec myFunction arg1 = ...;

(* Anonymous function *)
fun x -> x * 2;;

let y = (fun x -> x * 2);;

(fun x -> x * 2) 20;; (* Since the value being returned is a function "f", you get "f 20" which is calling it on 20. *)

(* Redifining the meaning of an operator (contextual/custom) *)
let (/$) x y = x + y;;

(* Function calling with composition *)
myFunction @@ anotherFunction @@ someFunction;;

(* Piping values from returned functions directly to other functions. *)
myFunction1 |> myFunction2 |> myFunction3;;

(* Optional arguments (? symbol) *)
let myFunction ?arg x = ...;;

(* Unit/IO based impure function declaration *)
let myFunction () = ...;;

(* First Class Module declaration. *)
let myModule = (module ModuleName : moduleSignature);;
```

### Globals, Mutables & Object Creation

```ocaml

let mutable name = "my_global";;

let () = 
  name <- "some new name";
  exit 0;;
  
type my_record = {
  peanuts : int;
  cashews  : int
};;

let () = 
  let nuts = { peanuts : 20; cashews : 30 };;
  exit 0
```

### Variants & Polymorphism

```ocaml
(* Depending on how it's used, it can act as an alias, an enum or a generic. *)
  
type my_type = int | float | string | dog | cat of steel;;

type 'type_of container = flat | cat of steel;;
```

### Variables

```ocaml
(* Simple variable without explicit type.*)
let age = 30;;

(* Simple variable with explicit type. *)
let age : int = 30;;

(* In, and, where - used for nesting, scope and multiple declaration. *)
let age = 30 and
let name = "John" and
let gender = Male in

let my_age = increment age in
let my_name = capitalize name in
let my_gender = display gender

(* Arrays *)
let my_numbers : int array = [|1; 2; 3; 4; 5|];;

(* Assignment of impure data. *)
my_numbers.(0) <- 30;;
```

### If Statements

```ocaml
(* If & else statement *)
let is_big x =
    if x > 10000 then
        True
    else
        False;;

(* Guards *)
let switch_state x =
    match x with
        | 10 -> "Ten"
        | 20 -> "Twenty"
        | 0 -> "Zero";;
```

### Looping & Control Flow

```ocaml
(* Pure Recursive Function *)
let rec call_inwards x =
    if x = 0 then
        x
    else
        call_inwards (x - 1);;

(* For Loop *)
let count_upwards () =
    for i = 0 to 10 do
        ...
    done;;

(* While Loop *)
let run_until () =
    let running = true in
        while running do
            ...
        done;;

(* Do While? / Iterator way using Seq and | *)
```

### Recursion & List Manipulation/Patterns

```ocaml

(* Provide base case, recursive case. *)

(* Mention advanced Recursion and tail Recursion. *)

let myFunction = 
   | 0 -> ...
   | hd :: tl -> myFunction hd tl

let rec myFunction =
   ...;;

```


### OOP Handling

```ocaml
(* Without constructor *)
class MyCamel = 
object
   val mutable name = name'
   method sayName = putStrLn name
end;;

(* Usage *)
let john = new MyCamel;;
(* need to mutate the setter here... *)
john#sayName;;


(* With constructor *)
class MyCamel name' = 
object
   val name = name'
   method sayName = putStrLn name
end;;

(* Usage *)
let john = new MyCamel "John";;
john#sayName;;

(* Destructor *)

(* Accessor & Mutators *)
```

### Interfaces (Module & Class Types)

```ocaml
module type My_Interface :
sig
   val create = int -> string
end;;
  
class type My_Interface :
sig
    val create = int -> string
    method ...
end;;
```
  
### .mli Files
  
```ocaml
(* Akin to header files in C, for storing interfaces and signatures, separate from implementation. *)


```

### Generics & Constructor Parametrization

```ocaml
(Jfhdzb) Result
```

### Functors

### Pointers/Refs

<br>
<br>

</details>

<details>
  <summary> For Expert Programmers </summary>

---

### FFI

The foreign function interface for interoping with native code and the os.

### DLLs / Shared Libraries

Accessing functions directly from shared libraries.

### Compiler/Interpreter Tweaks

Optimization, compiling or interpreting, linking, bytecode generation, garbage collection, etc.

### Project Layout & Code Structure

1 module file can contain multiple nested submodules. 
Scaffolding/ers.

### Architecture

Patterns. Functors and Monads.

### Good Practice

Clarity. Avoid surprises. DRY principle. SOLID principle if using OOP.

<br>
<br>

</details>

<details>
  <summary> For Functional Programming Dummies </summary>

---

### Terminology

* Purity
  * Functions that produce no side effects. Given an input, the ouput should be the same on said input no matter what the state of the system is. If this rule is broken, the function is not pure.

* State
  * Commonly used to refer to structures, variables, code or the system which can change at any moment in time. Code changing in other places other than their grouped scope is considered bad practice.

* Side Effect
  * When a function emits the notion of modyfing state outside of it's scope such as globals or dependencies.

* Unit/IO Notation
  * Commonly known/referred as the "void" type, (), this notation is used to indicate that a function will do or "return" an IO side effect operation that changes some system/program state.

* Expression
  * Also called compute/computation, is any calculation or subexpression that MUST return a value as a result. In the functional mindset, a program is a series of expressions and subexpressions but ultimately going down to a single value outputted. ("Figure of speech")

* Immutability
  * Data created/assigned with values at spawn time which cannot be changed afterwards. Can be predicted since it is constant.

* Mutable Data
  * Data that can be affected by side effects/IO.

* Records
  * Groups of types aligned together under a single type. It is the "structure/struct" aspect of functional programming.

* First Class Citizen
  * Any entity that can be treated as you treat a variable, which means you can add it to another, compute it, pass it as an argument to another function and/or return it as a value.

* Functions as First Class Citizens
  * Functional paradigm prides itself on the notion that some (depends on language) functions are ultimately variables, can be declared as such, can be passed as arguments and can be returned. This is the notion of function pointers for those who know C. Commonly used for callbacks, events and other procedural code.

* Higher Order Functions
  * Functions that are treated as First Class Citizens. Basically function pointers. Ocaml functions are all higher order. In Haskell, not all functions are higher order functions.

* Function Composition
  * Calling functions which rely on values returned by calling another function. E.g. f(g(x)).

* Arity
  * The number of parameters a function has. Lengthy parameters for a function (e.g high Arity) smells of a badly coded function or a complex one.

* Currying
  * Complex functions which have a high arity need to be broken down. This simplification process is called currying.

* Variants
  * Ocaml's type system for creating generics and polymorphic values.

* Functors
  * An umbrella term that refers to "something" that produces a "result" out of "something". Another word for a function. The concept is so abstract that there are many types of functors. They are functions that behave in a particular way. It can be implemented differently based on the language. It comes from category theory where a functor is a mapping between categories. (very abstract indeed)
    * Module Functors (dynamic modules)
      * Functions that operate on modules. Often used to provide the factory pattern or give mutability to "instantiate" modules.
  
    * Applicative Functors
      * Functions that operate on functors. (holy cat) The end result when two invocations of the functor is done has modules/classes with non-equal abstract types.
  
    * Generative Functors
       * Functions that operate on functors. (holy cat) The end result when two invocations of the functor is done has modules/classes with equal abstract types.
    * Monoid Functors
       * Functions where the output is independent of the input.
    
    Functors can be used to provide **dependency injection**, **inheritance**, **virtual/abstract** objects, polymorphism, subtyping, allowing the creation of factories/ and various other patterns.

* Monads - A form/type of an Applicative Functor

* Lambda Calculus
  * Anonymous function spawning notation.

* Polymorphism
  * The act of having and passing data that holds multiple "forms". A stream object for example might be a base entity for a filestream, networkstream, pipestream or whatever.

* Generics
  * Having data structures that can be reused with other types. Particularly lists. Lists of integers or bytes or strings as an example.

* Meta Programming
  * Programs written that generate other programs/code.

* Dependency Injection
  * A concept used to manage portability and hotswap, as common usecases. One implementation of dependency injection is the IoC container for dependency inversion.

* Module Types
  * Ocaml's "interfaces" to modules.

* Zippers
  * Pointers to certain nodes/data structures, such as trees and their branches.

### Functional Paradigm Aims

* Functional Application
  * Functional programming is all about having pure functions and calling those pure functions to transform your data. Everything is an expression and your IO should be separated and organized in a high level fashion.
  
* Functional Ability
  * Concepts like functors, monads, monoids and whatnot, extend the ability of what you can do in the language with functions.

* Functional Purity
  * Functions without side effects that are agnostic of system state. As many as you can. Why? Said functions are easy to test, well design and don't depend on external factors. (in theory)

* IO & Side Effect Separation
  * A tremendous amount of errors, bugs and malpractice happens as a result of poor state management. Having a more organized flow where IO is separate from pure code provides clarity to where errors may occur as well as visual guidance to where program logic/computation is located.

* Reduce state and constrain/isolate it
  * Removing for, while loops is one way to reduce state and instead do things recursively.

* Low Function Arity Through Currying


* Simple & Flexible Data Transformation
* Low Coupling, High Cohesion
* Type Correctness
* Immutability unless otherwise altered
* Recursivity
* Declaratively define problems
* Write less, Do more
* Lower bug rate

### Facts

* The LHS of `type` definitions is primarily concerned with generics. E.g `type 'a list` is the equivalent of `List<'a>`.
* The RHS of `type` definitions is primarily concerned with **modelling** a certain type of **format** the data can take. E.g Options
* The RHS is the evaluation of an expression, which possibly means that even for `types`, the RHS still evaluates to an expression where the returned value is a type.

<br>

* Expression evaluation - the expression MUST terminate in returning a value. Be it a number, or a type. or a unit.

<br>

* Recursivity state management and advanced recursion + tail recursion.

<br>
<br>
  
</details>

<br>

<details>
   <summary>External Dependencies</summary>

---

### Common Libraries

OPAM is the official Ocaml package manager.

`opam install <pkg-name>`

| Library  | Purpose | Comments |
| -------- | ------- | ----- |
| Lwt  | Events & Promises | todo |
| Mirage  | OCaml Platform| todo |
| LablTk | GUI | todo |
| vec | Data Structures - Dynamic Arrays | https://github.com/aionescu/vec |
| Cryptokit | Security & Cryptography | todo |
| Graphics Module | Charts & Graphics | todo |
| LambdaSoup | HTML/XML Parser | todo |
| Yojson | JSON Parser | todo |
| Str Module | Regex | todo |
| Ocaml-csv | CSV Parser | todo |
| | Interop | todo |
| DynF / FFI | Interop | todo |
| .NET | Interop | todo |
| QT | Interop | todo |
| pyml | Bindings for Python | todo |
| Ocaml-opencv | Computer Vision | todo |
| | Testing | todo |
| Logs | Logging | todo |
|  | AOP | todo |
|some_matrix/tensor lib|Machine Learning|todo|
| Ocaml-electron | Browser as a Service | todo |
| Qanat | ORM | todo |
| PPX | Meta Programming | todo |
| Caqti | Databases & SQL | todo |

<br>
<br>

</details>

<details>
   <summary>A Better Standard API Reference</summary>

---

## The Standard API

Click each module to expand and see their exposed functions and types.

Work in progress. Add Jane Street extension API here as well.

(* Importable Modules *)

<details>
    <summary>Sys</summary>
    
    <details>
        <summary>Module</summary>
            Functions.
    </details>

</details>

<details>
    <summary>Arg</summary>
    
    <details>
        <summary>Module</summary>
            Functions.
    </details>

</details>

<details>
    <summary>Stdlib</summary>
    
    <details>
        <summary>Module</summary>
            Functions.
    </details>

</details>

(* Console, File IO, Etc *)

<details>
    <summary>Printf</summary>
    
    <details>
        <summary>Module</summary>
            Functions.
    </details>

</details>

<details>
    <summary>Scanf</summary>
    
    <details>
        <summary>Module</summary>
            Functions.
    </details>

</details>

<details>
    <summary>Format</summary>
    
    <details>
        <summary>Module</summary>
            Functions.
    </details>

</details>

<details>
    <summary>Printexc</summary>
    
    <details>
        <summary>Module</summary>
            Functions.
    </details>

</details>

<details>
    <summary>In_Channel</summary>
    
    <details>
        <summary>Module</summary>
            Functions.
    </details>

</details>


<details>
    <summary>Out_Channel</summary>
    
    <details>
        <summary>Module</summary>
            Functions.
    </details>

</details>


<details>
    <summary>Filename</summary>
    
    <details>
        <summary>Module</summary>
            Functions.
    </details>

</details>

```ocaml

(* Console, File IO, Etc *)
Marshal
Callback
Lazy
Lexing

Gc
Oo


(* Date, Time, Math *)
Date
Time
Math

(* Related to Types *)
Char
Bool
String
Bytes
Int
Float
Complex

Unit
Option

(* Data Structure Modules *)
Array
Buffer
Stream
List
Queue
Seq
Hashtbl
Map
Set
Stack

(* Algorithms. Hashing, RNG, Sort, Etc. *)
Random
Digest
Parsing

(* Concurrency, Parallelism, Synchronization *)
Atomic
Thread
Mutex
Semaphore

```

</details>

<br>
<br>
<br>

## Abstract

Click the sections below to expand.

<br>
<br>

<details>
  <summary> Motivation </summary>

---

Optional reading.

The transition for an imperative programmer to functional/declarative programming is often the most frustrating and challenging task an individual has to face when introduced to the paradigm. I should know, since I'm actually in the process itself.

This is my "adventure", diving in the functional programming paradigm with the OCaml language.

I will share with you what, as an imperative programmer, has been difficult for me to tackle or understand, and solutions to how one can make that transition easier. This will also act as a centralized area containing as much useful information about OCaml and it's syntax as I can get.

<br>
<br>

</details>

<details>
  <summary> What is The Damn Goal..? </summary>

---

Optional reading.

Here is what I personally think is the biggest problem imperative programmers face when turning to the functional paradigm.
**The lack of a goal**. I don't mean something as cheesy as setting up for a journey on a career or deciding what you want to become.

No, a goal as in, "What is my aim to do, in order to get my program written, and for it to work".

To which, a poor imperative programmer will obviously turn to thinking about the syntax step by step and following logic as originally taught. It is how we/they naturally approach problems and it isn't a wrong approach.

The problem isn't that what they're doing is wrong. The problem is that the information being fed to us by the documentation and by material which "claims" to teach functional programming or the language at hand, **is not answering our questions.**

A seasoned imperative programmer wants to know:

* How do I declare a function with arguments and return values.
* How do I create objects and structures.
* What is my API and where can I find references for more functions and objects/structures.
* What does the layout of my project and my code look like?
* How do I handle x, y, z. Where x may be error handling, y logging and z calls or interop.
* What's the best convention and guidelines for writing this kind of code.

Out of these, arguably, the first and third questions are by far, the most important, for an aim in getting started.

<br>
<br>

---

<br>
<br>

What does the functional programming material provided to most imperative programmers give to them?



First off, it gives functions. Fair enough. Obviously useful. But functions with recursivity.

Then they are given records and types, which, again, fair enough, useful. But with other conundrums like typeclasses and module types. Not to mention they spend an awful amount of time discussing functional arity and currying.

They are then thrown into the type system and spend 70 pages reading about building a tree structure with abstract types or talks about how great the language is because it is supports lazy behaviour, that it's fabulous and elegant and whatever glorious deeds it can do using first class citizen entities.

Then it proceeds to show you how it does it by providing pattern matching and guards (with even more recursivity). When you are done, it introduces a concept called Monads, Higher Order Functions and Functors. Holy cat.

Do you see the problem?

<br>
<br>

---

<br>
<br>

None of the above tell the programmer:

1. What he should aim for.
2. Why he should aim for (whatever the goal is)
3. Analogies to which they can map their imperative knowledge to.

<br>
<br>

---

<br>
<br>

Enough ranting. I'll cover exactly what an imperative programmer needs to do to make that switch.

A functional programmer is tasked with four major concerns.

1. State management.
2. Functional purity & Transformation.
3. Separation of IO & Concern
4. Strict expression evaluation & Immutability


todo todo
explain the points.

<br>
<br>

</details>
