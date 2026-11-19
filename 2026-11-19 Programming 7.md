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

s casom lahko tudi primerjamo

== pri kazalcih 

```java
this == drugi (oba vsebujeta isti pomnilniski naslov - ista vsebina)
this != drugi (en na enem naslovu in drugi na drugem)
```

naredili smo nov tip(z zgradbo, omogoca operacije)
ko imamo tip cas je vseeno kako je cas interno predstavljen(lahko bi bil samo s stevilom od polnoci naprej)
primer: razred o razredu ulomkov(nebi vec razmisljali o stevci in imenovalci)

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

metoda, ki izpise cas:

```java
public void izpisi() {
        System.out.printf("%d:%02d", this.ura, this.minuta);
    }
```

metoda ToString():
uporabimo String.format();

```java
public String toString() {
        return String.format("%d:%02d", this.ura, this.minuta);
    }
    
System.out.println(malica.toString());
System.out.println(kosilo.toString());
System.out.println(vecerja.toString());
```

primerjava 2 casov:

```java
public boolean jeEnako(Cas drugi) { // tukaj bolj naravno staticna metoda, ampak je praksa da se uporablja nestaticne metode
        return (this.Cas == drugi.cas); // tukaj se primerjata po vsebini
        // return this == drugi bi vrnila true samo ce bi kazala na isti objekt

    }

```


se druge metode:
```java
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
```

### Example



## Questions

- [ ] 

## Connections


## Sources
