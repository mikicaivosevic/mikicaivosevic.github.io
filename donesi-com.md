## Kako sam dobio nagradu od 1000 dinara od donesi.com 

Prvi XSS i open redirect sam prijavio 7.12.2014. godine. 

Detaljno sam opisao gde se nalaze propusti, tako da su odmah mogli da srede sve to sto su i uradili, a ja sam dobio 1000 dinara u vidu kupona kao nagradu :) 

Mislim da je velika greska da se salje 1000 dinara, bolje je poslati majice, stikere, itd... Kad neko posalje 1000 dinara, nekako se cini kao da je procenio da vas trud i rad vredi 1000 dinara. Verujem da je to uradjeno iz dobre namere, ali je uradjeno lose. 

XSS

```
 http://www.donesi.com/beograd/tag/"><h1>
 ```

Open redirect

```
 http://www.donesi.com/beograd/zone.php?user_id=78624&user_address_id=0&zoneID=1&afterZoneGo=http://goo.gl/67bkVz
 ```

Nakon te prijave i slanja tih 1000 dinara, pitao sam da li mogu da mi daju referencu na Linkedinu jer bi mi to puno znacilo za moj CV koji sam gradio, ali nakon toga nisam dobio nikakav odgovor. Posle nekog vremena sam opet pitao da mi samo odgovore da li moze ili ne, da razumem ako nisu u mogucnosti itd, ali samo da napisu.

Nakon tog emaila, pomislili su da ih ja ucenjujem, samo ne znam kako jer sam vec poslao detaljno opisane propuste, ali ko ce ga znati. :) Uglavnom ja sam njih zbunjivao sa tim sto sam im slao sve, pa zbog toga je izostao odgovor, ali cim sam otkrio nove propuste, odjednom se izgubila ta zbunjenost i nastavljena je komunikacija i na kraju je sve sredjeno, ja sam dobio svoju referencu, a oni su opet dobili detaljno opisano propuste.

#### Sad smo dosli vec do 04.01.2015.

Opet prijavljujem propust, ovog puta jos jedan open redirect. Ono sto je najtuznije je to da ovaj propust jos uvek postoji. Oni su uradili fix, ali na veoma los nacin. Umesto da provere da li string pocinje sa http://donesi.com, oni su proverili samo da li string sadrzi donesi.com i na taj nacin omogucili da se to vrlo lako bypass-uje, kao sto se vidi dole u primeru :)

PoC:

```
www.donesi.com/click.php?ref=MikicaI&loc=ser&url=http://jelovnik.hr/?donesi.com
```

Nakon ovoga, primetio sam da mozda mogu da ponudim svoje usluge, ali tu sam dosao do toga da nisu zainteresovani jer ih je otkupila Foodpanda grupacija :) Skroz legitimno, tad sam i cestitao na prodaju, izvanredan uspeh...


#### Sad prelazimo na drugi period 15.03.2015

Jos jedan XSS

```
http://www.donesi.com/ser/unsub.php?email=%22%3E%3Cscript%3Ealert%281%29%3C/script%3E&hash=ebc88163b318ad8ccd22365a30a31db8
```

Opet sam detaljno opisao propust, ljudi se zahvalili i to je to :) 


### I konacno dolazimo do najzanimljivijeg propusta 25.09.2017.

Naravno, opet je u pitanju XSS, ali ovog puta persistent i to na strani restorana. Ovo mi je omogucilo da mogu da izvedem to da uzmem sesiju od restorana kod kog vrsim narudzbinu. Morao sam da testiram da vidim da li mogu da uzmem sesiju i nazalost uzeo sam od Colline (najbolji burgeri koje sam jeo).

Kad sam to oktrio, odmah sam poslao email sa detaljima gde se nalazi propust, koja narudzbina je kreirana i u kojoj moze da se vidi sta sam uradio. Bukvalno u roku od par sati su odgovorilii i sredili veoma brzo.

Prvo sredjivanje nije bilo bas dobro jer su filtrirani parametri pre snimanja u DB, a to je znacilo da jos uvek postoji maliciozan kod vezan za narudzvinu, pa sam to prijavio i na kraju je to sredjeno.


### Razlog zbog kog sve ovo pisem

Po dogovoru ovo nisam trebao da napisem, ali posle nekog vremena sam shvatio da moram ovo da opisem.

Uglavnom vrlo zanimljivo iskustvo, dosta propusta prijavljeno i jedna velika greska za njih. Dbra stvar po njih je sto su za "dz" dobili sve detaljno opisano, sto nasa zajednica nece podeliti ovakve stvari i to sto me prati ukupno pet ljudi (mama, tata, sestra i jos dva moja lazna profila), a losa stvar je to sto sam u mogucnosti da pisem sve ovo.
