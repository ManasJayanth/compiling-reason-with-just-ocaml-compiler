# Compiling Reason files with just the compiler

Ever wondered how to compile a [Reason](https://reasonml.github.io/) with just the compiler - without Dune?

Here's a example showing how.

1. Setup the compiler in manner you please. This repo provides a
   simple [esy.json](./esy.json) to get up-and-running quickly. You'll
   need [esy](https://esy.sh) on your machine. You can install it with
   `npm i -g esy`
   
   
2. Compile the `.re` by,

	a. Using the `-impl` option to let the compiler know about Reason.
	b. Asking the compiler to preprocess the Reason file with Reason's
	`refmt`. `refmt` will turn Reason files to OCaml AST in binary
	format. The compiler loads these binary AST files and proceeds
	with the rest of the compiler pipeline, like it would with any
	OCaml code.
	
	Command:
	
	```sh
	esy ocamlopt -verbose -pp 'refmt --print binary' -impl hello.re -o hello-reason
    ```
	
	
