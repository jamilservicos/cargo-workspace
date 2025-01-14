# cargo-workspace
template for creating a workspace in rustrover


manual use:

~~~bash
$ git clone git@github.com:jamilservicos/cargo-workspace.git
$ cd cargo-workspace
$ cargo new adder
     Created binary (application) `adder` package
$ cargo new add_one --lib
     Created library `add_one` package
$ cargo build
   Compiling add_one v0.1.0 (file:///projects/add/add_one)
   Compiling adder v0.1.0 (file:///projects/add/adder)
    Finished dev [unoptimized + debuginfo] target(s) in 0.68s
$ cargo run -p adder
    Finished dev [unoptimized + debuginfo] target(s) in 0.0s
     Running `target/debug/adder`
Hello, world! 10 plus one is 11!
~~~

see more about the rust workspace at:  https://doc.rust-lang.org/book/ch14-03-cargo-workspaces.html

adjust your .gitignore, example:
~~~.gitignore
*
!.gitignore
!adder/
!adder/.gitignore
!add_one/
!add_one/.gitignore
~~~
