---
created: 2026-11-19
tags:
  - note
  - journal
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-11-19
week: "7"
---

# 2026-11-19 - Object Methods, Static Attributes and Resizable Arrays

## Main Idea

We reach objects through [[Method|methods]]. The idea of objects is creating a new data type: with the class `Cas` we made a new type with a structure that allows operations, so the user of the class no longer thinks about hours and minutes, but about time as a whole.

`static` means that something is bound to the [[Class|class]], not to an [[Object|object]]. Static methods get the object as a parameter, non-static methods get it through `this`. There are also static attributes, shared by all objects of the class.

Methods that change attribute values (setters) are avoided: it is easier to make a new object and leave the old one alone ([[Immutable Object|immutable objects]], *nespremenljivi objekti*).

Arrays have a fixed size. A [[Dynamic Array|resizable array]] (*raztegljiva tabela*, class `VektorInt`) starts with some capacity and, when it is full, creates a new array twice as large.

## Notes

### Constructor and `this`

Methods are what lets us get to the objects. The first one is the [[Constructor|constructor]] (*konstruktor*): it does not create anything, it only sets the initial values of what has already been created (by `new`).

Through `this` the constructor accesses the object. The result of `new` is a [[Pointer|pointer]] (*kazalec*), not the object.

### Static and non-static methods

`static` means bound to the class and not to an object.

- static method `pristejStatic(Cas cas, int h, int min)`: the object is passed as an ordinary parameter, called as `Cas.pristejStatic(malica, 1, 50);`
- non-static method `pristej(int h, int min)`: `this` behaves like one more parameter, called as `kosilo.pristej(2, 30);`

Both compute the new time in minutes since midnight and reduce it modulo 1440 (minutes in a day) with `(noviCas % 1440 + 1440) % 1440`, because in Java `-10 % 3 = -1` and not `2`.

### Getters and setters

- getter (*vrni*): `vrniUro()`, `vrniMinuto()` — no parameters, return the attribute.
- setter (*nastavi*): `nastaviUro(int h)` — careful, because we work with pointers: if two variables point to the same object, a setter changes it for both. In class the setter is left commented out.

Instead of a setter we create a new object in the method (`plus` returns a new `Cas`).

### Immutable types

Methods that change attribute values are avoided; it is easier to make a new object and leave the old one alone (we avoid setters).

Immutable types (*nespremenljivi tipi*):

1. `String`

### Printing and `toString`

`izpisi()` prints the time, `toString()` returns it as a string. `toString` uses `String.format`, which works like `System.out.printf`, but returns the string instead of printing it.

### Comparing objects

We can also compare times. `==` on pointers compares addresses:

```java
this == drugi // both contain the same memory address (the same object)
this != drugi // one is at one address and the other at another
```

`jeEnakoKot` compares by content (`ura` and `minuta`). Here a static method would be more natural (it takes two times), but the practice is to use non-static methods. `return this == drugi` would return `true` only if both pointed to the same object.

### A new type

We made a new type (with a structure, allowing operations). Once we have the type `Cas`, it does not matter how time is represented internally (it could be just the number of minutes from midnight on). Example: a class for fractions (*ulomki*) — we would no longer think about numerators and denominators.

The [[Garbage Collector|garbage collector]] (*smetar*) deletes memory that nobody points to.

### Static attributes

There are also static attributes (bound to the whole class, shared by all objects).

- example of a static attribute for a human: species (*vrsta*)
- examples for `Cas`: the bounds (0, 24 h), the American way of writing time (AM, PM) — `zapis12`

A static attribute is accessed without `this` (`zapis12` or `Cas.zapis12`, not `this.zapis12`).

### Resizable arrays

Arrays have a fixed size (nothing stretches, a new, larger array is made instead).

Variant of a "resizable array" (*raztegljiva tabela*): whenever needed, make a new array and add the old data. That would be very inefficient.

So we make an array with an initial capacity (say 3); when it fills up, the new array is 2× larger than the previous one. On average we are efficient. It always has to grow by some factor; we will use factor 2.

## Code

### Class `Cas` (`cas/Cas.java`)

```java
public class Cas {
    private int ura;
    private int minuta;

    private static boolean zapis12 = false;

    public Cas(int h , int min){ // ne inicializiramo v konstruktu
        this.ura = h;
        this.minuta = min;
    } // konstruktor

    public static void nastaviZapis12(boolean da) {
        zapis12 = da; // ne this.zapis12, lahko pa Cas.zapis12
    }

    // staticna metoda
    public static void pristejStatic(Cas cas, int h, int min) {
        int noviCas = 60 * (cas.ura + h) + cas.minuta + min;
        noviCas = (noviCas % 1440 + 1440) % 1440;
        cas.ura = noviCas / 60;
        cas.minuta = noviCas % 60;
    }
    
    // ne-staticna metoda
    public void pristej(int h, int min) { // this se obnasa kot se en parameter
        int noviCas = 60 * (this.ura + h) + this.minuta + min;
        noviCas = (noviCas % 1440 + 1440) % 1440;

        this.ura = noviCas / 60;
        this.minuta = noviCas % 60;
    }

    public int vrniUro() { // ni nobenega parametra
        return this.ura;
    }

    public int vrniMinuto() {
        return this.minuta;
    }

    // public void nastaviUro(int h) {
    //     this.ura = h;
    // }

    public Cas plus(int h, int min) {
        int noviCas = 60 * (this.ura + h) + this.minuta + min;
        noviCas = (noviCas % 1440 + 1440) % 1440;

        int novaUra = noviCas / 60;
        int novaMinuta = noviCas % 60;

        return new Cas(novaUra, novaMinuta);
    }

    public void izpisi() {
        System.out.printf("%d:%02d", this.ura, this.minuta);
    }

    public String toString() {
        if (zapis12) {
            String pripona = (this.ura < 12) ? "AM" : "PM";
            int h = (this.ura + 11) % 12 + 1;
            return String.format("%d:%02d %s", h, this.minuta, pripona);
        }
        return String.format("%d:%02d", this.ura, this.minuta);
    }

    public boolean jeEnakoKot(Cas drugi) { // tukaj bolj naravno staticna metoda, ampak je praksa da se uporablja nestaticne metode
        return this.ura == drugi.ura && this.minuta == drugi.minuta; // tukaj se primerjata po vsebini
        // return this == drugi bi vrnila true samo ce bi kazala na isti objekt
    }

    public int razlikaVMin(Cas drugi) {
        return 60 * (this.ura - drugi.ura) +
                    (this.minuta - drugi.minuta);
    }

    public boolean jeManjsiOd(Cas drugi) {
        return (this.ura < drugi.ura) ||
        this.ura == drugi.ura && this.minuta < drugi.minuta;

        // ali return this.razlikaVMin(drugi) < 0;
    }

    public boolean jeManjsiAliEnak(Cas drugi) {
        return this.jeManjsiOd(drugi) || this.jeEnakoKot(drugi);
    }
}
```

### Test (`cas/TestCas.java`)

```java
public class TestCas {
    public static void main(String[] args) {
        // Cas malica = new Cas();
        // malica.ura = 10;
        // malica.minuta = 0;

        // Cas kosilo = new Cas();
        // kosilo.ura = 13;        
        // kosilo.minuta = 0;     

        Cas malica = new Cas(10, 0); // new ustvari objekt, malica kaze na ta objekt
        Cas kosilo = new Cas(13, 0);

        // Cas.pristejStatic(malica, 1, 50);
        // kosilo.pristej(2, 30);

        System.out.println(kosilo.vrniUro());
        System.out.println(kosilo.vrniMinuto());

        Cas vecerja = kosilo.plus(5, 0);

        System.out.println(malica.toString());
        System.out.println(kosilo.toString());
        System.out.println(vecerja.toString());

        Cas x = new Cas(11, 20);
        Cas y = new Cas(12, 0);
        Cas z = new Cas(22, 30);

        System.out.println(x);
        System.out.println(y);
        System.out.println(z);
        Cas.nastaviZapis12(true);
        System.out.println(x);
        System.out.println(y);
        System.out.println(z);


    }
}   
```

`System.out.println(x)` calls `x.toString()` automatically. ```text
13
0
10:00
13:00
18:00
11:20
12:00
22:30
11:20 AM
12:00 PM
10:30 PM
```

`kosilo.plus(5, 0)` leaves `kosilo` at 13:00 and returns a new object for `vecerja`.

### Bus timetable (`cas/VozniRed.java`)

Reads the first departure, the last departure and the interval in minutes, and prints the timetable.

```java
import java.util.Scanner;

public class VozniRed {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int uraZac = sc.nextInt();
        int minutaZac = sc.nextInt();
        int uraKon = sc.nextInt();
        int minutaKon = sc.nextInt();
        int interval = sc.nextInt();

        Cas cas = new Cas(uraZac, minutaZac);
        Cas casKon = new Cas(uraKon, minutaKon);

        while (cas.jeManjsiAliEnak(casKon)) {
            System.out.println(cas.toString());
            cas = cas.plus(0, interval);
        }
    }
}
```

```text
$ echo 8 0 10 0 25 | java VozniRed
8:00
8:25
8:50
9:15
9:40
```

### Resizable array (`VektorInt.java`)

`final` marks a constant; it is `static` because it belongs to the whole class.

```java
public class VektorInt {
    
    private static final int ZACETNA_KAPACITETA = 10;// konstante moramo zaceti z final

    private int[] elementi;
    private int stElementov;

    public VektorInt() {
        this.elementi = new int[ZACETNA_KAPACITETA];
        this.stElementov = 0;
    }

    public int steviloElementov() {
        return this.stElementov;
    }

    public int vrni(int indeks) {
        return this.elementi[indeks];
    }

    public void nastavi(int indeks, int vrednost) {
        this.elementi[indeks] = vrednost;
    }

    public void dodaj(int vrednost) {
        this.poPotrebiPovecaj();
        this.elementi[this.stElementov] = vrednost;
        this.stElementov++;
    }

    private void poPotrebiPovecaj() {
        if(this.stElementov == this.elementi.length) {
            int[] stariElementi = this.elementi;
            this.elementi = new int[2 * stariElementi.length];
            for (int i = 0; i < stariElementi.length; i++) {
                this.elementi[i] = stariElementi[i];
            }
        }
    }

    public void vstavi(int indeks, int vrednost) {
        this.poPotrebiPovecaj();

        for (int i = this.stElementov - 1; i >= indeks; i--) {
            this.elementi[i + 1] = this.elementi[i];
        }
        this.elementi[indeks] = vrednost;
        this.stElementov++;

    }
}
```

- `dodaj` adds at index `stElementov`, after `poPotrebiPovecaj` has made room.
- `poPotrebiPovecaj` (private helper): when the array is full, make a new array twice as long and copy the old elements over.
- `vstavi` shifts the elements from `indeks` onwards one place to the right, then writes the value.

## Questions

- [ ] 

## Connections

- Course: [[Programming 1]]
- Previous lecture: [[2026-11-12 - Reference Types, 2D Arrays and Classes - 6]] (classes, access modifiers, constructor, `Cas`)
- Related: [[Reference Type]], [[Static Method]], [[Getters and Setters]], [[String]], [[Amortized Analysis]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/06_razrediInObjekti_h.pdf|06_razrediInObjekti_h]] (static and non-static methods, getters and setters, immutability, `toString`, comparing, `VozniRed`, static attributes, `VektorInt`)
- Class code: `programming_1/class/7/` (`cas/Cas.java`, `cas/TestCas.java`, `cas/VozniRed.java`, `VektorInt.java`)
