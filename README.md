# c-temelleri

Learning C from the ground up, with a focus on embedded systems.
Part of my **OMR-2028** roadmap: embedded systems and Edge AI.

Every program here is written by hand, compiled with GCC from the terminal, and measured (bytes, exit codes) before it is committed.

## Environment

| Tool | Version |
|---|---|
| OS | Ubuntu on WSL2 (x86_64) |
| Compiler | GCC 15.2.0 |
| Debugger | GDB 17.1 |
| Build | GNU Make 4.4.1 |

## Build and run

```sh
gcc hello.c -o hello
./hello
echo $?   # exit code, 0 = success
```

## Programs

| # | File | Topic | Measurements |
|---|---|---|---|
| 1 | [hello.c](hello.c) | Program structure, `#include`, `main`, `printf`, exit code | Source 82 B, binary 15,952 B, exit code 0 |

## Roadmap

- [x] First program: write, compile and run with GCC
- [ ] Variables and data types (`int`, `char`, `float`)
- [ ] `sizeof`: how many bytes each type uses
- [ ] Operators and precedence
- [ ] Control flow: `if`, `switch`, `for`, `while`, `do-while`
- [ ] Functions, scope, storage classes (`auto`, `static`, `extern`)
- [ ] Stack frames
- [ ] Arrays and strings
- [ ] The four stages of compilation (`-E`, `-S`, `-c`, linking)
- [ ] Number systems and bitwise operators

## Conventions

- Commit messages follow [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `docs:`).
- Compiled binaries are not tracked; see [.gitignore](.gitignore).
