# OCaml - The Manual

> Pragmatic information about Functional Programming and OCaml.

<br>
<br>

## > For Intermediate Programmers

#### Spawning a project & building

* Ecosystem & Environment
  * dune
  * opam
  * LSP
  * ocamlc

`sudo apt-get install ocaml utop opam`

`dune init project`
`dune build`
`dune exec project`

<br>
<br>

#### Console Arguments & Printing

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

#### File IO

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

#### Directory & File Operations

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

#### Data Type Conversion

```ocaml
(* Typecasting. *)

let () =
    let some_string = "240" in
        let some_int = string_of_int some_string in
            let some_float = float_of_int some_int in
                let some_integer_logic = int_of_bool true in
                    exit 0;;
```

#### String Handling

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

#### Threading & Process Handling

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

#### Sockets

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

#### GUI

```ocaml
open Sys;
open Unix;

(*Synchronous*)
let () =
    
```

#### Web Requests

```ocaml
open Sys;
open Unix;

(*Synchronous*)
let () =
    
```

#### Web Framework

```ocaml
open Sys;
open Unix;

(*Synchronous*)
let () =
    
```
#### Logging

#### Regex

#### Parsing HTML/JSON/XML

#### Error Handling & Exceptions

#### Database Access / ORM

#### Keywords in OCaml

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

#### Symbols in OCaml

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

#### The Standard API

#### Common Libraries

* Lwt
* Mirage
* Labltk
* cryptokit

<br>
<br>

## > For Beginner Programmers

#### Types & Records

```ocaml
type box = int;;

type box = {
    some_var : String;
    another_var : Int;
    yet_another_var : Float
};;
```

#### Modules

```ocaml
module Box = 
struct
    type t = {

    }

    let f = expr
    let g = expr
end;;
```

#### Functions

```ocaml
let my_function arg1 arg2 = 
    arg1 + arg2;;

let this_func a : float b : string : unit = 
    another expr;

let my_func (x : int) (y : string) : bool =
    some expr;;
```

#### Variants & Polymorphism

```ocaml
type my_type = int | float | string | dog | cat of steel;;

type 'type_of container = flat | cat of steel;;
```

#### Variables, If Statements, Control Flow

#### OOP Handling

```ocaml
class my_class constr =
object (self)
    val _member = ...
    val _members = ...

    method some_method = ...
    method another_method = ...
end;;
```

#### Interfaces (Module Types)

#### Generics

#### Functors

## > For Expert Programmers

#### FFI

#### DLLs
