---
created: 2026-10-14
tags:
  - note
  - journal
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-10-14
week: "1"
---

# 2026-10-14 - Exercises for Introduction to programming

## Main Idea

Lab exercises (*vaje*) for week 1: moving around the computer with the terminal, setting up the exercise folder, running a Java program with input from a file, and testing it automatically against expected outputs with `tj.exe`.

## Notes

### Basic terminal commands

We usually want to navigate our computer using the terminal.

| Command | Meaning |
|---|---|
| `pwd` | where we are located |
| `ls` | list the files in the current directory |
| `ls -l` | longer list (with details) |
| `mkdir name` | make a new directory |
| `cd .` | stay where we are — `.` is the current directory |
| `cd ..` | go to the parent directory (one level up) |
| `cd /` | go to the root directory |
| `cat file` | display the contents of a file |
| `echo 2 5` | print `2 5` — useful as input for a program |
| `TAB` | autocomplete (*zaključevanje*) |
| `Ctrl + Shift + T` | new terminal (*nova konzola*) |
| `AltGr + 1` | types `~` (the home directory) on a Slovenian keyboard |

### Setting up the exercises

Our exercises will be located in:

```text
op51549:/remote_home/op51549.STUDENT/vaje/prog1$
```

1. Unzip the exercises into that folder and copy the exercise sheet next to them:

   ```bash
   unzip p1_vaje01.zip -d /remote_home/op51549.STUDENT/vaje/prog1/
   cp vaje01.pdf /remote_home/op51549.STUDENT/vaje/prog1/p1_vaje01/
   ```

   General form: `unzip 'what' -d 'where'`, `cp 'what' 'where'`.

2. Make a new directory `results` (*rezultati*):

   ```bash
   mkdir results
   ```

3. Copy `tj.exe` into the current directory (`.`):

   ```bash
   cp vsota1/tj.exe .
   ```

`tj.exe` is written in C# (.NET). To run it on Linux or Mac we need **Mono**:

```bash
sudo apt install mono-complete
```

### `PATH` and `CLASSPATH`

- **`PATH`** — the list of directories where the operating system looks for programs. Windows first looks in the current directory and only then in `PATH`; Linux looks only in `PATH` (*to samo Windows*).

  ```bash
  echo $PATH
  ```

- **`CLASSPATH`** — Java was developed on Unix with the same mechanism, so Java looks for classes in `CLASSPATH` (that is why `.` — the current directory).
- Open VS Code in the current directory:

  ```bash
  code .
  ```

Documentation: `openjdk@27` docs.

### Running programs

Open a file in an editor in the background with `&`, so the terminal is not blocked (*da konzola ne bo ugrabljena*):

```bash
gedit HelloWorld.java &
```

**Pipe** (*mehanizem cevovoda*): whatever is the output of our program becomes the input of the next program in the pipe (`|`):

```bash
echo 5 9 | java Vsota1
```

**Redirection** — input from a file (`<`) and output into a file (`>`):

```bash
java Vsota1 < vsota1/test01.in                         # input test01 into Vsota1
java Vsota1 < vsota1/test01.in > results/test01.res    # ... and write the answer into results
```

### Testing

Compare our answer (`.res`) with the correct answer (`.out`):

```bash
diff vsota1/test01.out results/test01.res
```

If nothing is printed, the files are the same → the answer is correct. (`diff` also returns an exit status: `0` if the files are the same, `1` if they differ.)

That is why we use `tj.exe` — it automates this process of testing for all test cases:

```bash
mono tj.exe Vsota1.java vsota1/ results/
firefox results/prikaz.htm    # view the results
```

For faster testing use the option `-threads 10`.

### Tasks (*naloge*)

**Vsota 1** — read two integers from $[-10^9, 10^9]$ and print their sum.

```java
import java.util.Scanner;

public class Vsota1 {
    public static void main(String[] args) {
        Scanner ana = new Scanner(System.in);
        // left: type Scanner, right: a Scanner object; ana points to the object
        int a = ana.nextInt();
        int b = ana.nextInt();

        int vsota = a + b;
        System.out.println(vsota);
    }
}
```

```text
$ echo -32 7 | java Vsota1
-25
```

**Vsota 2** — the same, but print in the form `a + b = c`:

```java
System.out.println(a + " + " + b + " = " + vsota);
System.out.printf("%d + %d = %d%n", a, b, vsota); // just for fun (za foro)
```

```text
$ echo 32 -7 | java Vsota2
32 + -7 = 25
```

## Questions

- [ ] 

## Connections

- Course: [[Programming 1]]
- Lecture: [[2026-10-08 - Introduction to programming - 1]] — input with `Scanner`, compiling and running, testing with test cases
- Exercises: [[Sources/programming_1/vaje/prog1/p1_vaje01/vaje01.pdf|vaje01]]

## Sources

- My terminal notes from the lab: `programming_1/vaje/prog1/p1_vaje01/zapiski.txt`
- Code: `programming_1/vaje/prog1/p1_vaje01/Vsota1.java`, `Vsota2.java`
