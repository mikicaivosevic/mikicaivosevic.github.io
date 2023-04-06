---
title: "Donesi / Foodpanda / Glovo - ista priča nakon nekoliko godina i dve akvizicije"
date: 2023-04-06T18:55:58+02:00
description: "Prošlo je 6 godina od prijavljivanja određenih propusta na Donesi. Neki su rešeni odmah, a neki su ostali tu i nakon nekoliko godina i nekoliko akvizicija."
draft: false
---
Prošlo je 6 godina od prijavljivanja određenih propusta na Donesi. Neki propusti su rešeni odmah, a neki su ostali tu i nakon nekoliko godina. Jedan od zanimljivijih propusta koji je rešen brzo je bio to što sam mogao da uradim narudžbinu i restoran čim prihvati narudžbinu bi automatski omogućio da preuzmem njihovu sesiju, odnosno da se ulogujem kao taj restoran #nisamgladan

Ono što je meni zanimljivo je to da su se desile dve akvizicije u međuvremenu, prva od strane Foodpanda, pa je skoro i Glovo preuzeo Donesi, a ono što je interesantno je to da neki propusti još uvek postoje na servisu i nakon nekoliko godina. Propusti su toliko očigledni da su mogli biti identifikovani da je neko pustio neki web vulnerability scanner, a to pokazuje na neki način da nije bila obraćena paznja prilikom akvizicije na deo oko sigurnosti.

Deo starog koda je ostao i na donesi.com domenu, bez obzira sto je prebačeno dosta toga na novi backend, a isto tako stara verzija koja ima propuste je ostala javno dostupna na legacy.donesi.com subdomenu. Dobra stvar je što je u medjuvremenu ubačen Cloudflare i aktiviran WAF za glavni domen, pa neke stvari ne mogu baš tako lako da se eksploatišu na novom domenu bez obzira što su ranjive, ali na subdomenu gde je legacy aplikacija koja je jos uvek povezana na bazu gde su stari korisnici, tu nije uključen Cloudflare WAF 🤦.

Još jedna zanimljivost je to da sam resetovao password putem forme na legacy aplikaciji i da mi je plain text password stigao na email. Nadam se da nova aplikacija ne čuva u plaintext formatu lozinke od korisnika.

