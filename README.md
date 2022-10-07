# OCaml - The Manual

> Pragmatic information about Functional Programming and OCaml.

---

## > For Seasoned Programmers

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

* Beginers


