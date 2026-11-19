---
created: 2026-11-19
tags:
  - note
  - journal
type: "[[Lectures]]"
course:
date:
week:
---

# 2026-11-19 Programming 7

## Main Idea


## Notes

metode, da lahko do objektov pridemo
1. konstruktor(ne ustvari nicesar, ampak nastavi zacetne vrednosti tistega kar je ze ustvarjeno)

preko this lahko konstruktor dostopa objekte.
rezultat je kazalec(ne objekt)

ideja objektov = ustvarjanje novega podatkovnega tipa


staticen pomeni, da je vezan na razred in ne na objekt

metodam, ki spreminjajo vrednosti atributov se izogibamo. lazje da naredimo nov objekt in starega pustimo pri miru. (setterjem se izogibamo)

nespremenljivi tipi:
1. String

## Code

staticna:
```java
public static void pristej(Cas cas, int h, int min) {
        int noviCas = 60 * (cas.ura + h) + cas.minuta + min;
        noviCas = (noviCas % 1440 + 1440) % 1440; // ker -10 % 3 = -1 in ne 2
        cas.ura = noviCas / 60;
        cas.minuta = noviCas % 60;
    }
    
klice se  Cas.pristejStatic(malica, 1, 50);

```

ne-staticna metoda:
```java
public void pristej(int h, int min) {
        int noviCas = 60 * (this.ura + h) + this.minuta + min;
        noviCas = (noviCas % 1440 + 1440) % 1440;

        this.ura = noviCas / 60;
        this.minuta = noviCas % 60;
    }
klice se kosilo.pristej(2, 30);
```

getter(vrni uro, vrni minuto)

```java
public int vrniUro() { // ni nobenega parametra
        return this.ura;
    }

    public int vrniMinuto() {
        return this.minuta;
    }
```

setter (nastavi) - pazi, ker delamo s pointerji.

```java
// public void nastaviUro(int h) {
    //     this.ura = h;
    // }
```

namesto setterja ustvarimo v metodi nov objekt
```java

```

```java
public Cas plus(int h, int min) {
        int noviCas = 60 * (this.ura + h) + this.minuta + min;
        noviCas = (noviCas % 1440 + 1440) % 1440;

        NovaUra = noviCas / 60;
        NovaMinuta = noviCas % 60;

        return new Cas(NovaUra, NovaMinuta);
    }

klicemo Cas vecerja = kosilo.plus(5, 0);

```
'''

'''

### Example



## Questions

- [ ] 

## Connections


## Sources
