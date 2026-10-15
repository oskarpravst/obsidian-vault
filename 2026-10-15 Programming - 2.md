---
created: 2026-10-15
tags:
  - note
  - journal
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-10-15
week: "2"
---

# 2026-10-15 1115

## Main Idea


## Notes

stavki se izvajajo strogo zaporedno v programu.

pogojni stavek(if statement) se izvede samo ce je nek pogoj izpolnjen.
```java
if (pogoj) {
	stavki...
}

// samo en stavek lahko brez {}
if (pogoj)
	stavek
```


example:
```java
if (pogoj){ // ce res se bo to notri izvrsilo
	stavki
}

// ce ni res pa gremo direktno sem

```

```java
if (pogoj){
	stavki1 // ce izpolnjen sem in potem ven(ne v else)
} else{
	stavki2 // ce izpolnjen se bo if spregledal
}

// to je vse samo 1 pogojni stavek
```

v stavkih imamo podstavke. zato lahko {} velikokrat zbrisemo

```java
if (prvo > drugo){
            System.out.println("Prvo je vecje");
        } else if (prvo < drugo){
            System.out.println("Drugo je vecje");
        } else{
            System.out.println("Stevili sta enaki");
        }
```
else if je verizenje pogojev

```java
if 
else if
else if
else if
...
else
```

v teh verigah se izvede vedno samo en del(blok)

vedno inicializiramo spremenljivke preden jih uporabimo


# Logicni izrazi in tip boolean

pogoj v if stavku je logicni izraz(3 < 4, to je izraz z svojo vrednostjo ali resnica ali neresnica)
boolean (george bool) boolova algebra izhaja

ce truge se izvede if del, ce false se izvede else del.

```java
boolean b = 4 > 5
b = false

c = !b
c = true

```

enako kot :
```java
leva == desna 

3 == 3 // true

3 = 3 // napaka

3 == 3.0 // true, ker se pri operacijah kjer mesamo int in double, int pretvori v double

```

logicni operatorji:

```java
p && q // and

p || q // or

!p // no
```


kratkosticno izvajanje(shortcut evaluation)
```java
p && q // ce je p false program sploh ne pregleda q

p || q // ce je p true program sploh ne pregleda q
```


prevajalnik vidi samo tipe:

```java
import java.util.Scanner;

public class Vecje {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        boolean a = (3 < 4) || (1 / 0 == 1);
        boolean a = (3 < 4) || (b == c); // nedefinirane spremenljivke zato se nebi prevedlo
        System.out.println(a);

    }
}
```

in ima prednost pred ali


## Key Concepts


## Code

'''

'''

### Example

izpisimo kateri izmed dveh prebranih stevil je vecje:
```java
import java.util.Scanner;

public class Vecje {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        System.out.print("Vnesi prvo stevilo: ");
        int prvo = sc.nextInt();
        System.out.print("Vnesi drugo stevilo: ");

        int drugo = sc.nextInt();

        if (prvo > drugo){
            System.out.println("Prvo je vecje");
        } else{
            System.out.println("Drugo je vecje");
        }
        }
    }

```
ce prvo = 5 in drugo = 5: bo izpisal da je drugo vecje, ker if ni bil izpolnjen

posodobljena verzija:
```java
import java.util.Scanner;

public class Vecje2 {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        System.out.print("Vnesi prvo stevilo: ");
        int prvo = sc.nextInt();
        System.out.print("Vnesi drugo stevilo: ");

        int drugo = sc.nextInt();

        if (prvo > drugo){
            System.out.println("Prvo je vecje");
        } else{
            // ce pridemo do tod, vemo da velja da je prvo <= drugo
            // se vedno pa je lahko prvo < drugo ali prvo == drugo
            if (prvo < drugo){
                System.out.println("Drugo je vecje");
            } else{
                System.out.println("Stevili sta enaki");
            }
        }
        }
    }

```

ocena:
```java
import java.util.Scanner;

public class Ocena {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int tocke = sc.nextInt();
        int ocena = 0;

        if (tocke >= 90){
            ocena = 10;
        } else if (tocke >= 80){ // && tocke < 90 ker je to ze v prejsnem pogoju
            ocena = 9;
        } else if (tocke >= 70){
            ocena = 8;
        }  else if (tocke >= 70){
            ocena = 7;
        } else if (tocke >= 60){
            ocena = 6;
        } else if (tocke >= 50){
            ocena = 5;   
        }
        System.out.println(ocena); 
    }
}
```

sistem pipe:
```
echo 75 | java Ocena 
```

prednost: quicker

ce vpisujem prevelike(101) ali premale(-5) procente ne dela:
```java
import java.util.Scanner;

public class Ocena {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int tocke = sc.nextInt();

        if(tocke > 100 || tocke < 0){
            System.out.println("napaka")
        } else{
            int ocena = 0;

            if (tocke >= 90){
                ocena = 10;
            } else if (tocke >= 80){ // && tocke < 90 ker je to ze v prejsnem pogoju
                ocena = 9;
            } else if (tocke >= 70){
                ocena = 8;
            }  else if (tocke >= 70){
                ocena = 7;
            } else if (tocke >= 60){
                ocena = 6;
            } else if (tocke >= 50){
                ocena = 5;   
            }
            System.out.println(ocena); 

        }
    }
}

```


program, ki napise, ali je prebrano leto prestopno


## Questions

- [ ] 

## Connections


## Sources
