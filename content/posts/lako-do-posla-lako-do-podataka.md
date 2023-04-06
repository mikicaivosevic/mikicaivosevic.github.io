---
title: "Lako do posla — Lako do podataka"
date: 2023-04-06T18:43:02+02:00
description: "Lako do posla / Lako do podataka 🚀 Pre nekoliko dana se pročulo da je baza podataka sa sajta lakodoposla[dot]com osvanula na internetu. Sadržaj baze uključuje osetljive podatke oko 500,000 aktivnih i neaktivnih korisnika, a gde se nalazi podaci kao što su: ime, prezime, email, lozinke, …"
draft: false
---

Lako do posla / Lako do podataka 🚀 Pre nekoliko dana se pročulo da je baza podataka sa sajta lakodoposla[dot]com osvanula na internetu. Sadržaj baze uključuje osetljive podatke oko 500,000 aktivnih i neaktivnih korisnika, a gde se nalazi podaci kao što su: ime, prezime, email, lozinke, …

Od lozinki, čak 15,000 je otkriveno u plaintext formatu, bukvalno na izvol’te 🤦 To sad dovodi sve te korisnike do rizika da ukoliko koriste istu lozinku još negde, da neko pristupi njihovim nalozima i na drugim servisima, tako da je predlog da što pre zamene, odnosno izbace iz upotrebe tu lozinku.

Sve ovo se našlo lako dostupno na internetu. Poslednji unos u bazu je datiran 28. jula ove godine, a 10. avgusta se pisalo o LFI propustu na jednom 🇮🇷 forumu.

Ovaj data breach je pokazao da lakodoposla nema nikakvu politiku povodom jačine lozinke — sve dolazi u obzir, pa su tako neki korisnici (među kojima se nalaze i poznate domaće firme i državne institucije) koristili lozinke u stilu “ime firme123”, “123456” i slično.

Sad prelazimo na sledeću etapu gde su prešli igricu, polisa privatnosti. Tamo navode da se obavezuje da će čuvati podatke korisnika, ali takođe se navodi da ukoliko se desi krađa podataka, da se sajt ne može smatrati odgovornim.

Neke od loših praksi koje sam primetio:

🚨 Ne radi se hash lozinki svuda, odnosno neke lozinke su čuvaju u tekstualnom formatu, a to je baš loša praksa, da ne kažem kriminalna.

🚨 Ne postoji validacija za lozinke, odnosno dozvoljavaju se lozinke kao što je 123456 i sl.

🚨 Ne forsira se HTTPS konekcija

🚨 Pristup MySQL bazi podataka je bio otvoren za pristup sa bilo koje IP adrese.

🚨 Nisu radili redovno ažuriranje web aplikacije i infrastrukture.

🚨 Nisu sprovodili redovna sigurnosna testiranja.

🚩 Sve ovo su kriminalni propusti za firmu koja barata ovolikim brojem osetljivih podataka.

I sad ide najzanimljiviji deo, kako su došli do baze podataka ?

1️⃣ Našli su LFI (Local File Inclusion) propust na web aplikaciji koji je dopustio napadačima da čitaju lokalne fajlove na serveru.

2️⃣ Došli su do konfiguracionog fajla koji sadrži podatke za pristup MySQL bazi, a koji koristi web aplikacija za komunikaciju sa bazom podataka (.env ili tako nešto).

3️⃣ Kad su došli do kredencijala za MySQL, iskoristili su to što je dozvoljeno da se uloguje sa bilo koje IP adrese direktno na MySQL bazu.

4️⃣ Kad su to uradili, dobili su pristup direktno bazi i podacima, pa su mogli da urade dump, to jest da preuzmu celu bazu.

Kako sam došao do ovog zaključka ? Na jednom forumu sam našao da se neko pohvalio sa tim da je našao LFI na sajtu lakodoposla, a nakon toga sam pretpostavio da je neko preuzeo kredencijale za bazu, pa sam kroz Shodan proverio history za njihovu IP adresu i primetio da je do 6.8. MySQL bio otvoren za pristup sa bilo koje IP adrese, a nakon toga je odrađeno whitelist-ovanje, odnosno da bazi može da se pristupi samo sa određenih IP adresa.
