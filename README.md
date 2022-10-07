# OCaml - The Manual

> Pragmatic information about Functional Programming and OCaml.

<br>
<br>

## > For Intermediate Programmers

#### Spawning a project & building

dune
opam
lsp

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

#### GUI

#### Web Requests

#### Web Framework

#### Regex

#### Parsing HTML/JSON/XML

#### Error Handling & Exceptions

#### Database Access / ORM

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
type my_type = int;;

type my_type = {
    some_var : String;
    another_var : Int;
    yet_another_var : Float
};;
```

#### Modules

```ocaml
module my_module = 
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
