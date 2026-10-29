---
created: 2026-10-29
tags:
  - note
  - journal
type: "[[Lectures]]"
course:
date:
week:
---

# 2026-10-29 Programming 4

## Main Idea




## Notes

zanimivost: operator (=) nastopajo v stavkih

```java
int a = 7;
a = 10;
a += 20;

lahko nastopajo tudi kot del izraza

int b = 0;
b = (a = 3) + 9 // ker lahko enacaj nastopa kot del izraza
a = 3
b = 12

a = b = 10;
a = (b = 10); // desna asociativnost
```

ucinek izraza je da a dobi vrednost 3
vrednost tega izraza je nova vrednost leve strani

v knjigi bitni operatorji (zelo koristni - preberi sam)

nekateri operatorji so mocnejsi od drugih - prioriteta
_*_ > _+_

```java
(2 << 3) - 1
ali
2 << (3 - 1)

```

asociativnost

```java
a op b op c
(a op b) op c // levo asociativno
a op (b op c) // desno asociativno (prireditveni)
```


# Metode

kos kode vzamemo in mu damo ime, potem poklicemo ime in se koda izvede.
S tem izdelamo metod(funkcijo)

metoda je kos kode ki ima svoje ime in jo lahko veckrat reusamo.

```java
public static void main // glavna metoda
```
je tudi metoda


argumenti grejo v parametre

ime parametra je lahko ime argumenta(ker so loceni spremenljivki)

```java
public static void metoda(T1 p1, T2 p2, ..., Tn pn) { // type in parameter
	...
}

public static void ...(...) {
	metoda (a1 , a2, ..., an); // argument
}
```

tipi morajo biti priredljivi

```java
public static void narisi(int n) {
	...
}
int a = 3

narisi(a) // 3 se skopira v n

long b = 7

narisi(b) // to bi bila napaka, ker long ne mores skopirati v int
```


# return

klicatelj dobi rezultat iz racuna.
metode lahko vracajo vrednosti

```java
return 14 // pejdi ven iz metode (zakljuci izvajanje metoda), klic metode se zamenja z vrnjeno vrednostjo.
```

more biti nujno type cesa hocemo da se returna (more biti isto kot variable kateremu hocemo vrednost dati)

ce imamo void lahko gremo ven z :

```java
return; //to bi delalo

break; // to dela samo v loopu 
```

# recursion

metode lahko klicejo samo sebe - rekurzivni klic

nekatere probleme z rekurzijo lazje resimo

primer: fibonacijevo zaporedje

```
0 1 2 3 5 8 13 21 ...
```

rekurencna enacba se lahko v programu prevede v rekurzijo

```
Fn = 0 ; n = 0
	 1 ; n = 1
	 Fn-2 + Fn-1 drugace
```

## Code

primer : program, ki izpise vzorec

```java
public class Plus {
    public static void main(String[] args) {

        for (int i = 1; i <= 4; i ++) {
            for (int j = 1; j <= 4; j++) {
                System.out.print(" ");
            }
            System.out.println("+");
        }
        for (int i = 1; i <= 9; i++) {
            System.out.print("+");
        }
        System.out.println();
        for (int i = 1; i <= 4; i ++) {
            for (int j = 1; j <= 4; j++) {
                System.out.print(" ");
            }
            System.out.println("+");
        }
    }
}
```
ta koda je repetitive , zato bolj z uporabo metode (2 x se ponovi )

```java
public class Plus {
    public static void main(String[] args) {

        navpicniKrak();
        for (int i = 1; i <= 9; i++) {
            System.out.print("+");
        }
        System.out.println();

        navpicniKrak(); 
    }
    public static void navpicniKrak() {
        for (int i = 1; i <= 4; i ++) {
            for (int j = 1; j <= 4; j++) {
                System.out.print(" ");
            }
            System.out.println("+");
        }

    }
}
```
to je z uporabo metode

```java
import java.util.Scanner;

public class Plus {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        navpicniKrak(n);
        for (int i = 1; i <= 2 * n + 1; i++) {
            System.out.print("+");
        }
        System.out.println();

        navpicniKrak(n); 
    }
    public static void navpicniKrak(int visina) {
        for (int i = 1; i <= visina; i ++) {
            for (int j = 1; j <= visina; j++) {
                System.out.print(" ");
            }
            System.out.println("+");
        }

    }
}
```

```java
public static void main {
	int a = 42;
	metoda(a);
	System.out.println(a);
}

public static void metoda(int a) {
	a++;
	System.out.println(a);
}
```

to izpise 43 42

bolj kompaktna koda

```java
import java.util.Scanner;

public class Plus1 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        navpicniKrak(n);
        
        sredinskiDel(n);

        navpicniKrak(n); 
    }
    public static void navpicniKrak(int visina) {
        for (int i = 1; i <= visina; i ++) {
            znaki(visina, ' ', false);
            System.out.println("+");
        }

    }
    public static void sredinskiDel(int n) {
        znaki (2 * n + 1, '+', true);

    }
    public static void znaki(int n, char znak, boolean prelom) {
        for (int i = 1; i<= n; i++) {
            System.out.print(znak);
        }
        if (prelom) {
            System.out.println();
        }
    }
}
```

primer return

```java
public class Obseg {
    public static void main(String[] args) {
        // obseg(3, 4);

        int o = obseg(3, 4);
        System.out.println(o);
    }

    // public static void obseg(int a, int b) {
    //     System.out.println(2 * (a + b)); // tega obsega ne moremo uporabiti
    // }
    public static int obseg(int a, int b) {
        return 2 * (a + b);
    }
}
```

prastevila z metodami

preverjanje ce je kandidat prastevilo je podproblem, zato mu naredimo svojo metodo

```java
import java.util.Scanner;

public class Prastevila5{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        System.out.println(2);
        

        for (int kandidat = 3; kandidat <= n; kandidat+= 2){

            if (jePrastevilo(kandidat)) {
                System.out.println(kandidat);
            }
        }
    }

    public static boolean jePrastevilo(int stevilo){
        
        int koren = (int) Math.round(Math.sqrt(stevilo)); // round vrne long

        for (int d = 3; d < koren; d+= 2){
            if (stevilo % d == 0){
                return false;
            }
            // napaka da bi dali
            // else {
            //     return true; 
            // }
        }

        // if (prastevilo){
        //     return true;
        // } else {
        //     return false;
        // }
        return true;
    }

} 


```

Prijateljska stevila
```
220: 1 2 4 5 10 11 20 22 54 55 110 = 284

284: 1 2 3 7 11 142 = 220
```

vsota deljiteljev iz kombinatorike :

```java
import java.util.Scanner;


public class PrijateljskaStevila {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int stevilo = sc.nextInt();

        // System.out.println(imaPrijatelja(stevilo));

        if (imaPrijatelja(stevilo)) {
            // System.out.println(kandidat); ne gre
            System.out.println(vsotaDeljitevljev(stevilo));
        } else {
            System.out.println("Nima");
        }

    }

    public static boolean imaPrijatelja(int stevilo) {
        int kandidat = vsotaDeljitevljev(stevilo);

        return kandidat != stevilo && vsotaDeljitevljev(kandidat) == stevilo;
    }

    public static int vsotaDeljitevljev(int n) {
        int vsota = 0;
        for (int d = 1; d < n; d++) {
            if (n % d == 0) {
                vsota += d;
            }
        }
        return vsota;
    }
}
```
'''

'''

### Example



## Questions

- [ ] 

## Connections


## Sources
