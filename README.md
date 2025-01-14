# [cargo-workspace](https://github.com/jamilservicos/cargo-workspace)
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

## Don't forget to adjust your `Cargo.toml` !!

default:
~~~toml
# cargo-workspace/Cargo.toml

[workspace]
members = [
]

resolver = "2"

[profile.release]
codegen-units = 1
lto = true
strip = "symbols"
opt-level = 3

[profile.dev]
opt-level = 1               # Use slightly better optimizations.
overflow-checks = false     # Disable integer overflow checks.

[workspace.package]
authors = ["myname <my@email> (my.site)"]
description = "rust app"
documentation = ""
publish = false
license = "MIT"
readme = "README.md"
exclude = [
    ".gitignore", 
    ".rustfmt.toml", 
    ".github", 
    ".rusty-hook.toml",
    "tests/**",
    ".vscode/**",
    ".gitattributes",
]

[workspace.lib]
crate-type = ["rlib"]
test = false

[workspace.lints.rust]
unsafe_code ={ level = "deny", priority = -1 }

[workspace.lints.clippy]
all = { level = "deny", priority = -1 }
cargo = { level = "deny", priority = -1 }
pedantic = { level = "deny", priority = -1 }

#[workspace.dependencies]

#[workspace.build-dependencies]

#[workspace.dev-dependencies]
~~~

adjust your .gitignore, example:
~~~.gitignore
*
!.gitignore
!adder/
!adder/.gitignore
!add_one/
!add_one/.gitignore
~~~
