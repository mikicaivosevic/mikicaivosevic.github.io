---
title: "IoT Hack: Od običnog štampača do poverljivih ugovora"
date: 2023-04-06T18:51:34+02:00
description: "Pre izvesnog vremena, učestvovali smo u testiranje interne mreže jedne firme. Omogućili su nam pristup mreži, ali bez ikakvih dodatnih privilegija — isti pristup internoj mreži koji imaju i njihovi zaposleni."
draft: false
---
Pre izvesnog vremena, učestvovali smo u testiranje interne mreže jedne firme. Omogućili su nam pristup mreži, ali bez ikakvih dodatnih privilegija — isti pristup internoj mreži koji imaju i njihovi zaposleni. 

Šta smo uradili ?

Mapirali smo čitavu infrastrukturu i došli do brojke od oko 1000 zakačenih uređaja.

Zatim smo grupisali sve uređaje i podelili ih na kategorije kao što su PC, server, štampač, VOIP telefoni i sl.

Čim smo videli da je na mrežu zakačen određen broj štampača 🖨, odlučili smo da ih testiramo, da vidimo da li koriste default kredencijale (🚩 kao što često koriste, jer se retko ko seti da ih promeni 🚩). Nažalost po njih, a super za nas, naša pretpostavka se ispostavila tačnom, tako da smo lako uspeli da pristupimo admin dashboard-u štampača.

Zanimljiva stvar koju smo odmah pronašli u konfiguraciji je ta da štampac čuva u sebi SMTP kredencijale za 🔑 Office 365 📨 nalog firme kako bi mogao automatski da pošalje narudžbinu za nove kertridže kada se potroše na mejl distributera.

Nakon analize shvatili smo da su ovi kredencijali enkriptovani, pa nismo mogli direktno da im pristupimo, ali sa kontrolom nad dashboard-om, nismo ni morali. Jednostavno smo promenili SMTP host i podesili da ne šalje kredencijale na Office 365, već na naš SMTP server, odakle smo mogli da ih uzmemo i koristimo za dalje logovanje na poslovni mejl nalog firme.

Pošto smo se kretali zaobilaznim putem, morali smo i da deaktiviramo proveru SSL sertifikata na štampaču, ali ni to nije bio problem uz admin privilegiju na uređaju. Nakon toga, Office 365 kredencijali (username i password 🔐) su stigli direktno do nas.

Odmah smo se ulogovali i shvatili da nalog sačuvan u štampaču za porudžbinu kertridža ima pristup poverljivim dokumentima u mejlu firme. To podrazumeva ugovore, interne odluke i druge osetljive podatke 💾 💳.

Za ovu potencijalni katastrofu, sve što je bilo potrebno je da kredencijali na štampaču ostanu u svom default obliku, t.j. da ne budu ojačani snažnom lozinkom.

Sa sve većim brojem uređaja koji koriste Wi-Fi konekciju, od računara i telefona do aparata za kafu i Roomba usisivača, površina sajber napada je značajno uvišestručena. Zato je danas neophodno održavati redovnu bezbednosnu higijenu svih poslovnih resursa na internetu. Ovo podrazumeva kontinuirani monitoring onlajn resursa, ali i obuku zaposlenih usled sve učestalijih phishing i ransomware napada.
