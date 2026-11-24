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

## Repository layout

Each topic lives in its own numbered folder, in the order it was learned:

```
c-temelleri/
├── 01-hello/        first program: structure, printf, exit code
│   └── hello.c
├── .gitignore       compiled binaries are not tracked
└── README.md
```

## Build and run

```sh
cd 01-hello
gcc -Wall -Wextra -Werror -std=c11 hello.c -o hello
./hello
echo $?   # exit code, 0 = success
```

`-Wall -Wextra` turn on the compiler's warnings, `-Werror` refuses to build while any warning remains, and `-std=c11` pins the language standard.

## Programs

| # | Folder | Topic | Measurements |
|---|---|---|---|
| 01 | [01-hello](01-hello/) | Program structure, `#include`, `main`, `printf`, exit code | Source 82 B, binary 15,952 B, exit code 0 |

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
- [ ] Makefile and CI (GitHub Actions)

## Conventions

- Commit messages follow [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `docs:`, `refactor:`).
- Code, comments and output strings are written in English from `02-variables` on.
- Compiled binaries are not tracked; see [.gitignore](.gitignore).
