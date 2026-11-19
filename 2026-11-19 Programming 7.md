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

Smetar memory na katerega noben ne kaze izbrise.

obstajajo tudi staticni atributi(vezani na celoten razred - skupni za vse objekte)
primer staticnega atributa za cleveka = vrsta
primer za cas = meja (0, 24ur), ameriski nacin zapisa(AM, PM)


tabele so fiksne velikosti(nic se ne razteza, ampak se naredi nova tabela z vecjo velikostjo)
variante "raztegljive tabele" - po potrebi naredimo novo tabelo, dodamo stare podatke
to bi bilo zelo neucinkovito

zato se naredi tabelo z zacetno kapaciteto(recimo 3), ko se zapolni je nova tabela 2x vecja od prejsnje. v povprecju smo ucinkoviti. vedno mora biti za nek faktor

uporabili bomo faktor 2.



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

vozni red avtobusa:
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

ameriski nacin
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
        zapis12 = vrednost; // ne this.zapis12, lahko pa Cas.zapis12
    }
    
    
public String toString() {
        if (zapis12) {
            String pripona = (this.ura < 12) ? "AM" ; "PM";
            int h = (this.ura + 11) % 12 + 1;
            return String.format("%d:%02d %s", this.ura, this.minuta, pripona);
        }
        return String.format("%d:%02d", this.ura, this.minuta);
    }
```
### Example



## Questions

- [ ] 

## Connections


## Sources
