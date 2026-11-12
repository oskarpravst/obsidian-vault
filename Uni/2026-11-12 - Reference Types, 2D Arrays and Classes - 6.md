---
created: 2026-11-12
tags:
  - note
  - journal
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-11-12
week: "6"
---

# 2026-11-12 - Reference Types, 2D Arrays and Classes

## Main Idea

A variable of an array type does not hold the array itself, but a [[Pointer|pointer]] (*kazalec*) to it. Java has two kinds of data types: [[Primitive Type|primitive types]] (*primitivni tipi*) hold the value, [[Reference Type|reference types]] (*referenčni tipi*) hold an address. Copying a variable (also when passing it to a [[Method|method]]) always copies its value, so for a reference type only the address is copied.

Java has no real [[Two-dimensional Array|two-dimensional arrays]], only arrays of pointers to arrays. Rows exist, columns do not.

An [[Object|object]] is like an array whose elements can have different types; its type is described by a [[Class|class]] (*razred*). Attributes should be `private` and set through a [[Constructor|constructor]] (*konstruktor*).

## Notes

# Memoization

[[Memoization]] (*memoizacija*, not "memorization") — we store the results we have already computed.

# Reference types

```text
jshell> int[] a = {1, 2, 3};
a ==> int[3] { 1, 2, 3 }

jshell> int[] b = a;
b ==> int[3] { 1, 2, 3 }

jshell> b[0] = 42;
$3 ==> 42

jshell> a
a ==> int[3] { 42, 2, 3 }
```

A variable of an array type does not store the array, but a pointer to the array (we can think of it as a memory location).

```text
a -> [1, 2, 3]; // where [1, 2, 3] is located
```

```text
100 [1]
	[2]
	[3]
	
	
a  [100]

int[] b = a;

b also contains 100 - it points to the same array [1, 2, 3];
if we change an element, it changes in the array both of them point to
```

A pointer is like a slip of paper that points to a person. If we copy the slip, we have two slips, but the person is still the same one. If the person changes, both slips "change" (they point to the changed person).

Why don't we see these effects elsewhere? Because there are two kinds of data types:

1. [[Primitive Type|primitive types]] (there are 8 of them) hold the value,
2. [[Reference Type|reference types]] (`String`, `T[]`, `Scanner`) hold an address, so copying copies only the address.

When copying, the value of the variable is copied.

# Passing arrays to methods

```java
public static void main(...) {
	int a = 42; // a[42]
	int[] t = {1, 2, 3}; // t[->] [1, 2, 3]
	int[] u = {4, 5, 6}; // u[->] [4, 5, 6]
	int[] v = f(a, t, u); // v[->] [7, 8]
	
	
	
}

public static int[] f(int aa, int[] tt, int[] uu) {
	// aa[42]
	// tt[->] [1, 2, 3]
	// uu[->] [4, 5, 6]
	aa = 66; // aa[66]
	tt[1] = 10; // [1, 10, 3]
	uu = new int[]{7, 8}; // uu[->][7, 8], ne velja vec uu[->] [4, 5, 6]
	return uu;
	
}
```

- `aa = 66` changes only the copy, `a` in `main` stays 42.
- `tt[1] = 10` changes the array that both `t` and `tt` point to.
- `uu = new int[]{7, 8}` makes `uu` point to a new array; `uu` no longer points to `[4, 5, 6]`, and `u` is unchanged.

# Two-dimensional arrays

They do not exist in Java. What exists are arrays of pointers to arrays.

Rows exist, columns do not.

```java
T[][] t = new T[m][n];
```

When would we need two-dimensional arrays? (see Questions)

Advantage of these two-dimensional arrays: the rows do not all have to be the same length. The rows cannot be of different types.

```java
int[][] // an array of int elements
```

```java
T[] tabela = new T[dolzina];
```

For a reference type the elements of a new array have the value `null` (the null address — a pointer that points nowhere).

We can also have three-dimensional arrays (an array of 3 "pages").

# Classes and objects

An array is a sequence of elements of the same type. An [[Object|object]] is a sequence of elements of arbitrary types. Its variables usually have different meanings (but they have something in common). In objects the variables are called attributes (*atributi*), and we access them by their names. The type of an object is given in a [[Class|class]] (*razred*): a class is the construct with which we describe how the individual objects are composed.

Objects also belong to reference types.

```java
public class Ulomek {
	int stevec; // atributi
	int imenovalec;
}

Ulomek u = new Ulomek();
u.stevec = 3;
u.imenovalec = 5;
```

We define classes in separate files; the file name = the class name.

Examples of classes:

1. fraction (*ulomek*)
2. complex number
3. point in 3D
4. date
5. postal address
6. course (*predmet*)
7. student (the enrolment number is a `String`, because it can start with 0)

Class `Cas` (time):

```java
public class Cas {
	int ura;
	int minuta;
}
```

Attributes describe the state of the object. If I allow free access to the attributes, I can allow the object to get into an invalid state.

The idea is that attributes are accessed only through methods (so we want to forbid access to attributes from outside the class in which they are defined).

## Access modifiers (*dostopna določila*)

- `public` — visible from everywhere
- `protected` — from classes in the same package and from subclasses
- (none) — in the same package (*paket*, a set of classes in the same directory)
- `private` — only in the same class

All attributes should be `private`. If we declare an attribute differently, we need a good reason for it.

Accessing private attributes from another class is a compile error:

```bash
oskarpravst@Mac cas % javac Cas.java
oskarpravst@Mac cas % javac TestCas.java
TestCas.java:4: error: ura has private access in Cas
        malica.ura = 10;
              ^
TestCas.java:5: error: minuta has private access in Cas
        malica.minuta = 0;
              ^
TestCas.java:8: error: ura has private access in Cas
        kosilo.ura = 13;
              ^
TestCas.java:9: error: minuta has private access in Cas
        kosilo.minuta = 0;
              ^
4 errors
```

## Constructor

A [[Constructor|constructor]] initializes the attributes (it has no return type).

The operator `new` creates the object (attributes set to `ura = 0`, `minuta = 0`). Then the constructor is called (it gets 3 things: `h`, `min` and the pointer to the object).

```java
public Cas(int h , int min){
        this.ura = h; 
        this.minuta = min;
    } // konstruktor
```

The constructor gets a pointer to the object (this pointer is visible as `this`); `this` behaves like an additional parameter.

`new` returns the pointer to the object, which is then copied into the variable `malica`.

## Code

### Printing a 2D array (`IzpisTabele.java`)

```java
public class IzpisTabele {
    public static void main(String[] args) {
        int[][] t = {
            {3, 4, 1, 9},
            {7, 5, 10, 6},
            {12, 1, 0, 8}
        };

        for (int i = 0; i < t.length; i++) {
            for (int j = 0; j < t[i].length; j++) {
                System.out.print(t[i][j] + " ");
            }
            System.out.println();
        }
        
        // ali

        for (int[] vrstica: t) {
            for (int element: vrstica) {
                System.out.print(element + " ");
            }
            System.out.println();
        }
    }
}
```

Both loops (indices, and the [[Enhanced For Loop|for-each loop]]) print the same:

```text
3 4 1 9 
7 5 10 6 
12 1 0 8 
```

### Array of columns (`Stolpci.java`)

Each row has a different length (row `i` has `i + 1` elements), so we first create only the array of pointers to rows (`new int[n][]`) and then each row separately.

```java
import java.util.Scanner;
import java.util.Arrays;

public class Stolpci {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt(); // stevilo vrstic

        int[][] stopnice = new int[n][];

        for (int i = 0; i < n; i++) {
            int[] vrstica = new int[i + 1];
            for (int j = 0; j <= i; j++) {
                vrstica[j] = j + 1;
            }
            stopnice[i] = vrstica;
        }

        for (int[] vrstica: stopnice) {
            System.out.println(Arrays.toString(vrstica));
        }
    }
}
```

```text
$ echo 4 | java Stolpci
[1]
[1, 2]
[1, 2, 3]
[1, 2, 3, 4]
```

### Index of the maximum by columns (`IndeksMaksimuma.java`)

Only when the array is a rectangle (all rows equally long) can we talk about columns.

```java
import java.util.Scanner;
import java.util.Arrays;

public class IndeksMaksimuma {
    public static void main(String[] args) {
        int[][] tabela = {
            {2, 3, -1, 4, 0},
            {7, -2, -4, 3, 8},
            {-6, 9, -3, 5, -7},
            {3, -1, -7, 6, 4}
        };

        int[] imax = iMaxPoStoplcih(tabela);
        System.out.println(Arrays.toString(imax));
    }

    public static int[] iMaxPoStoplcih(int[][] t) {
        int[] imax = new int[t[0].length];

        for (int j = 0; j < t[0].length; j++) {
            int iNaj = 0;
            for (int i = 1; i < t.length; i++) {
                if (t[i][j] > t[iNaj][j]) {
                    iNaj = i;
                }
            }
            imax[j] = iNaj;
        }

        return imax;
    }
}
```

```text
[1, 2, 0, 3, 1]
```

### Class `Ulomek` (`TestUlomek.java`, `Ulomek.java`)

`TestUlomek.java`:

```java
public class TestUlomek {
    public static void main(String[] args) {
        Ulomek a = new Ulomek();
        a.stevec = 3;
        a.imenovalec = 5;
        Ulomek b = new Ulomek();
        b.stevec = 7;
        b.imenovalec = 2;

        System.out.printf("a: %d/%d%n", a.stevec, a.imenovalec);
        System.out.printf("b: %d/%d%n", b.stevec, b.imenovalec);



    }
}
```

`a` and `b` hold only pointers.

`Ulomek.java` (a separate file in the same folder):

```java
public class Ulomek {

    int stevec;
    int imenovalec;
}
```

```text
a: 3/5
b: 7/2
```

## Questions

- [ ] When would we need two-dimensional arrays?

## Connections

- Course: [[Programming 1]]
- Previous lecture: [[2026-11-05 - Arrays, Searching and Sorting - 5]] (memoization, [[Array|arrays]])
- Related: [[Fibonacci Sequence]] (memoization example), [[Variable Scope]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/05_tabele_h.pdf|05_tabele_h]] (memoization, primitive and reference types, two-dimensional arrays), [[Sources/programming_1/prosojnice/06_razrediInObjekti_h.pdf|06_razrediInObjekti_h]] (classes, access modifiers, constructor)
- Class code: `programming_1/class/6/` (`IzpisTabele.java`, `Stolpci.java`, `IndeksMaksimuma.java`, `cas/Cas.java`, `cas/TestCas.java`, `program/Ulomek.java`, `program/TestUlomek.java`)
