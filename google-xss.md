## Kako sam dobio nagradu od 1000 dinara od donesi.com 

## XSS na google.com domeni i nagrad od 5000$ + Hall of fame

Kako mi je uopste palo na pamet da trazim propuste na google.com ? 

Ni ja sam jos uvek ne verujem koliko sam tad imao srece. Uglavnom vece pre nego sto sam otkrio propust sam se napio najgore u zivotu, dovoljno je da kazem da kad me je mama zvala na skype, da sam se probudio na plocicama, pao sam sa kreveta u toku noci.

Otisao nekako do kompa, poceo da pricam sa mamom, ali zato sto sam verovatno jos uvek bio pijan, ne znam ni sam, ali neki link me odveo na telegraf.rs i tamo sam video reklamu neku da google trazi programere, da ima otvorene pozicije. Kako sam i zasto otvorio telegraf.rs ne znam, a ni kako je oglas za posao u google dosao kod njih na sajt jos manje znam. 

Uglavnom istog trenutka kad sam otvorio google, mahinalno sam odlucio da proverim GET parametre, da unesem neke html tagove i booooommmmm, otreznio sam se istog trenutka. Da nisam bio pijan, sigurno ne bih bio toliko lud da to testiram, tako da je bilo veoma bitno da napisem to. :D

PoC:

```
https://www.google.com/about/jobs/search/?_escaped_fragment_=t%3Djo%26jid%3D2955001%3Cscript%3Ealert%281337%29%3C/script%3E"
```

Ono sto je najvaznije, nakon 10ak dana sam dobio email u kom su bile dve veoma bitne stavke:

 - "Congratulations! This vulnerability is eligible for a reward of $5000." 

 - "Finally, please let us know if you’d like your name added to our Hall of Fame[1] page. It should be of the form: name - site [site link]"


#### Pitanje

Ako sam preko telegraf.rs uspeo da dodjem do propusta na google-u, da li to znaci da treba da krenem da posecujem i informer.rs ? :/ #dilema