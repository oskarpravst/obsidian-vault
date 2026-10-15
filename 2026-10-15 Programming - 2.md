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

## Questions

- [ ] 

## Connections


## Sources
