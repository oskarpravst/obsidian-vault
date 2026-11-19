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

## Code


```java
public static void pristej(Cas cas, int h, int min) {
        int noviCas = 60 * (cas.ura + h) + cas.minuta + min;
        noviCas = (noviCas % 1440 + 1440) % 1440; // ker -10 % 3 = -1 in ne 2
        cas.ura = noviCas / 60;
        cas.minuta = noviCas % 60;
    }
```


'''

'''

### Example



## Questions

- [ ] 

## Connections


## Sources
