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


'''

'''

### Example



## Questions

- [ ] 

## Connections


## Sources
