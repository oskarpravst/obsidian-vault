---
created: 2026-11-26
tags:
  - note
  - journal
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-11-26
week: "8"
---

# 2026-11-26 - Overloading, Constructors and Inheritance

## Main Idea

We finished the [[Dynamic Array|resizable array]] `VektorInt` (removing an element, `toString` with [[StringBuilder]]) and used its `String` version for a counting-out game (*izštevanka*).

Several methods may share a name if their signatures differ ([[Method Overloading|overloading]]); the same holds for constructors, and one [[Constructor|constructor]] can call another with `this(...)`.

The main topic was [[Inheritance|inheritance]] (*dedovanje*): a relation between classes where a subclass has everything its superclass has, plus something more (a part-time student is a student who also pays tuition). Every constructor starts with `this(...)` or `super(...)`. A subclass can redefine a method ([[Method Overriding|overriding]], *redefinicija metode*, `@Override`). The compiler only knows the type of the pointer, the runtime knows the type of the object, and **the method that is called is chosen by the type of the object**. So one `Student[]` array can hold both students and part-time students.

## Notes

### Removing an element and `toString`

`odstrani(indeks)` shifts every element after `indeks` one place to the left and decreases `stElementov`.

`toString` returns the contents as `[e0, e1, ..., en-1]`. It is easier to add the comma *before* an element than after it: we check whether it is the first element and, if so, put no comma in front of it.

Can I append to a string or change it? No, [[String|strings]] are immutable (*nizi so nespremenljivi*):

```java
String a = "tralala";
a += "hopsasa"; // ustvari se nov String kot vsota obeh nizov
```

So building a string with `+=` in a loop creates a new string in every step. Java offers a solution for this inefficiency: `StringBuilder`, a string that can be changed. With `StringBuilder` the method is faster. **When building strings in a loop, use `StringBuilder`, not `String`.**

`VektorString` is the same class as `VektorInt`, only with `String[] elementi` (the slides mention [[Inheritance|inheritance]] and generics as more general solutions).

### Counting-out game (`Izstevanka`)

The input gives the number of children `n`, the number of words in the rhyme `k` and the children's names. The children stand in a line; in each of the `n - 1` rounds the `k`-th child drops out (when counting reaches the end of the line, it continues from the start). The program prints the names of the children in the order they drop out. The names are kept in a `VektorString`; the index of the child that drops out is `(stBesed - 1) % stOtrok`.

### Methods with the same name

This is allowed, provided they differ in their signature (*podpis*): the name and the parameter types. The return type is not part of the signature.

### Several constructors

Again they must differ in the order of parameter types:

```java
public VektorInt() {
    this.elementi = new int[ZACETNA_KAPACITETA];
    this.stElementov = 0;
}

public VektorInt(int kapaciteta) {
    this.elementi = new int[kapaciteta];
    this.stElementov = 0;
}
```

Inside one constructor we call another (possible in Java, with a restriction: **it has to be the first statement in the constructor!**):

```java
public VektorInt() {
    // this.elementi = new int[ZACETNA_KAPACITETA];
    // this.stElementov = 0;
    this(ZACETNA_KAPACITETA); // klic konstruktorja 
}

public VektorInt(int kapaciteta) {
    this.elementi = new int[kapaciteta];
    this.stElementov = 0;
}
```

### Default constructor

If I don't define any constructor in a class, the compiler adds an empty constructor without parameters itself (the default constructor, *privzeti konstruktor*; it does nothing), its body contains `super()`.

```java
public class PrimerA {
	private int x;
	
	// prevajalnik doda: (prevzeti konstruktor)
	public PrimerA() {
	}
}
```

The default constructor exists only if we define no constructor of our own. The class `PrimerB` itself compiles, but it has no constructor without parameters, so `new PrimerB()` does not compile:

```java
public class PrimerB {
	private int x;

	public PrimerB(int x) {
	this.x = x;
	}
}
```

```java
PrimerB b = new PrimerB(); // napaka pri prevajanju
```

### Inheritance

A relation between classes: one class inherits another. We have a special case (student → part-time student, *izredni študent*): all properties are shared, but it has something extra.

```java
class A {
	...
}

class B extends A {
	...
}
```

`B` is a subclass of `A` (`B` is a subtype of type `A`), `A` is a superclass (`A` is a supertype of `B`). Transitivity holds.

If a dog is a mammal, the dog has everything a mammal has, and something more. The subclass inherits all attributes (also the private ones) and all methods (except the private ones).

### Class `Student` and the constructor of `IzredniStudent`

First attempt (class `Student` is under Code below). This does not compile, for two reasons:

1. the attributes `ip`, `vpisna` and `stroskiBivanja` are private in `Student`, so they are not directly accessible;
2. the constructor does not start with `this(...)` or `super(...)`, so the compiler adds `super()`, but `Student` has no constructor without parameters. So even with public attributes it would not compile.

```java
public class IzredniStudent extends Student {

    private int solnina;

    public IzredniStudent(String ip, String vpisna, int stroskiBivanja, int solnina) {
        this.ip = ip;
        this.vpisna = vpisna;
        this.stroskiBivanja = stroskiBivanja;
        this.solnina = solnina;

    }
}
```

```java
konstruktor(...) {
	super(...) ali this(...);
}
```

With `super` we call the constructor of the superclass; every constructor has to start with it. (If it does not start with `this()` or `super()`, the compiler adds the call `super()` itself.)

So we could add an empty constructor to `Student`, or delete it again:

```java
public Student() {
        
}
```

Because we gave our own `super`, the compiler will not add its own:

```java
public class IzredniStudent extends Student {

    private int solnina;

    public IzredniStudent(String ip, String vpisna, int stroskiBivanja, int solnina) {

        super(ip, vpisna, stroskiBivanja);
        this.ip = ip;
        this.vpisna = vpisna;
        this.stroskiBivanja = stroskiBivanja;
        this.solnina = solnina;

    }
}
```

This still does not compile: `this.ip`, `this.vpisna` and `this.stroskiBivanja` are private in `Student`. But the superclass constructor already sets the three attributes, so only `solnina` is left:

```java
public class IzredniStudent extends Student {

    private int solnina;

    public IzredniStudent(String ip, String vpisna, int stroskiBivanja, int solnina) {

        super(ip, vpisna, stroskiBivanja);
        this.solnina = solnina;

    }
}
```

`ana` and `bojan` in `TestStudent` are pointers (*kazalca*).

### Overriding a method

Redefining a method (*redefiniranje metode*): before the method header we write `@Override` (so it knows that this is a redefined method). The method must have the same name as the original and the same order of parameter types; the access modifier must be the same or looser (protected → protected or public, but not private).

```java
@Override
public int stroski() {
    // return this.stroskiBivanja + this.solnina;
    return super.stroski() + this.solnina;
}
```

`super.stroski()` calls the superclass version of the method.

### Pointer type and object type

`B` is a subclass of `A`:

```java
A a = new A(...);
B b = new B(...);
A p = b; // okej
B q = a; // napaka pri prevajanju
```

```java
Student s = bojan; // gre - polek kazalca bojana imamo kazalec s, ki kaze na bojana
IzredniStudent is = ana; // ne gre
```

The type of a pointer can be a supertype of the object's type (a `Student` pointer can point to a `Student` or to an `IzredniStudent`).

- The type of the pointer is set by its declaration.
- How do we know the type of the object a pointer points to? Through `new`: the runtime (*izvajalnik*) creates the object `bojan` with the constructor and knows that it is an `IzredniStudent`. The runtime knows the types of objects.
- The compiler (*prevajalnik*) only looks at types when compiling: it sees only the type of the pointer (`Student`). This rule is why `IzredniStudent is = ana;` is rejected.

**The choice of method is determined by the type of the object, not of the pointer:**

```java
Student s = bojan;

System.out.println(s.stroski()); // 1100 (stroski iz IzredniStudent)
```

So if these were `Student` pointers in an array, I can put students and part-time students into the same array:

```java
t[0] = new Student("Cvetka Cevc", "1", 900);
t[1] = new IzredniStudent("Drago Debeljak", "2", 300, 500);
t[2] = new Student("Emil Erjavec", "3", 800);

for (int i = 0; i < t.length; i++) {
    System.out.printf("%s -> %d%n", t[i].vrniIP(), t[i].stroski());
}
```

For `Drago Debeljak` the loop calls `stroski` from `IzredniStudent` (300 + 500 = 800).

### Preview for next week

In class we started the shape hierarchy: `Lik` (*lik*, shape) as the common superclass, `Pravokotnik` and `Krog` extend `Lik`, `Kvadrat` extends `Pravokotnik` (a square is a special case of a rectangle). The classes are still empty.

## Code

### `Student` and `IzredniStudent`

`Student.java`:

```java
public class Student {
    
    private String ip;
    private String vpisna;
    private int stroskiBivanja;


    public Student(String ip, String vpisna, int stroskiBivanja) {
        this.ip = ip;
        this.vpisna = vpisna;
        this.stroskiBivanja = stroskiBivanja;
    }

    public String vrniIP() {
        return this.ip;
    }

    public int stroski() {
        return this.stroskiBivanja;
    }
}
```

`IzredniStudent.java`:

```java
public class IzredniStudent extends Student {

    private int solnina;

    public IzredniStudent(String ip, String vpisna, int stroskiBivanja, int solnina) {

        super(ip, vpisna, stroskiBivanja);
        this.solnina = solnina;

    }

    @Override
    public int stroski() {
        // return this.stroskiBivanja + this.solnina;
        return super.stroski() + this.solnina;
    }

}
```

`TestStudent.java`:

```java
public class TestStudent {
    public static void main(String[] args) {
        Student ana = new Student("Ana Antolinc", "12345678", 500); // ana je kazalec na Student
        IzredniStudent bojan = new IzredniStudent("Bojan Bevc", "87654321", 400, 700);

        System.out.println(ana.vrniIP());
        System.out.println(bojan.vrniIP());

        System.out.println(ana.stroski());
        System.out.println(bojan.stroski());

        Student s = bojan;

        System.out.println(s.stroski());

        Student[] t = new Student[3];

        t[0] = new Student("Cvetka Cevc", "1", 900);
        t[1] = new IzredniStudent("Drago Debeljak", "2", 300, 500);
        t[2] = new Student("Emil Erjavec", "3", 800);

        for (int i = 0; i < t.length; i++) {
            System.out.printf("%s -> %d%n", t[i].vrniIP(), t[i].stroski());
        }
    }
}
```

```text
Ana Antolinc
Bojan Bevc
500
1100
1100
Cvetka Cevc -> 900
Drago Debeljak -> 800
Emil Erjavec -> 800
```

### `VektorInt`: new methods

The rest of the class is unchanged from [[2026-11-19 - Object Methods, Static Attributes and Resizable Arrays - 7]]; the constructors are in [[#Several constructors]].

```java
public void odstrani(int indeks) {
    for(int i = indeks; i < this.stElementov - 1; i++) {
        this.elementi[i] = this.elementi[i + 1];
    }
    this.stElementov--;
}

public String toString() {
    StringBuilder sb = new StringBuilder();
    sb.append("[");
    for(int i = 0; i < this.stElementov; i++) {
        if (i > 0) {
            sb.append(", ");
        }
        sb.append(this.elementi[i]);
    }
    sb.append("]");
    return sb.toString();
}
```

```java
public class TestVektorInt {
    public static void main(String[] args) {
        VektorInt v = new VektorInt();
        v.dodaj(10);
        v.dodaj(20);
        v.dodaj(30);
        v.vstavi(1, 15);
        v.odstrani(2);

        System.out.println(v.toString());
    }
}
```

```text
[10, 15, 30]
```

### `Izstevanka`

```java
import java.util.Scanner;

public class Izstevanka {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int stOtrok = sc.nextInt();
        int stBesed = sc.nextInt();

        VektorString otroci = new VektorString();

        for (int i = 0; i < stOtrok; i++) {
            otroci.dodaj(sc.next());
        }

        int stKrogov= stOtrok - 1;

        for (int krog = 1; krog <= stKrogov; krog++) {
            int ixIzpadlega = (stBesed - 1) % stOtrok;

            System.out.println(otroci.vrni(ixIzpadlega));

            otroci.odstrani(ixIzpadlega);
            stOtrok--;
        }
    }
}
```

```text
$ echo 5 9 Anton Barbara Cene Drago Evfilija | java Izstevanka
Drago
Anton
Evfilija
Barbara
```

## Questions

- [ ] 

## Connections

- Course: [[Programming 1]]
- Previous lecture: [[2026-11-19 - Object Methods, Static Attributes and Resizable Arrays - 7]] (`VektorInt`, `toString`, immutable objects)
- Related: [[Reference Type]], [[Immutable Object]], [[Pointer]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/06_razrediInObjekti_h.pdf|06_razrediInObjekti_h]] (slides 56–67: `toString`, `StringBuilder`, `VektorString`, `Izstevanka`, methods with the same name, several constructors, default constructor)
- Slides: [[Sources/programming_1/prosojnice/07_dedovanje_h.pdf|07_dedovanje_h]] (slides 1–26: inheritance, `Student`/`IzredniStudent`, `super`, overriding, pointer type vs. object type, arrays, shape hierarchy)
- Class code: `programming_1/class/8/` (`Student.java`, `IzredniStudent.java`, `TestStudent.java`, `VektorInt.java`, `TestVektorInt.java`, `VektorString.java`, `Izstevanka.java`, `liki/`)
