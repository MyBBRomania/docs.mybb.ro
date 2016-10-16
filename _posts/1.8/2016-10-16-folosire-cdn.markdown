---
layout: page
title:  "Folosirea unui CDN cu MyBB"
categories: faq
permalink: 1.8/faq/folosire-cdn
---

MyBB 1.8 aduce pentru prima dată compatibilitatea cu un CDN. Această facilitate vă permite să încărcați fișiere statice precum JavaScript, CSS și imagini de la un CDN la alegere. Acest tutorial vă va ghida prin pașii de instalare de bază.

Notă: Doar CDN-urile de tip "pull" sunt suportate în momentul scrierii acestui ghid.

# Setarea domeniilor/subdomeniilor

La setarea unui CDN, va trebui să alegeți subdomeniul care va fi folosit. Pentru acest tutorial, vom folosi *"s.mybbstuff.com"*. Toate fișierele pentru subdomeniu se află în `/home/euan/webapps/s_mybbstuff_com/`.

Odată ce ați creat acest subdomeniu, ar trebui să copiați fișierele statice curente pe el. Mai jos se află o listă cu dosarele/fișierele pe care va trebui să le copiați în cadrul unei instalații implicite MyBB:

- cache/themes/*
- images/*
- uploads/*
- jscripts/*

# Configurarea CDN-ului

Odată ce aceste fișiere au fost copiate, ar trebui să puteți accesa fișierele de stil din domeniul specificat. Acum urmează configurarea CDN-ului. Ar trebui să alegeți un furnizor pe care îl preferați și în care aveți încredere; pentru acest tutorial, vom folosi "cdn.net".

Odată ce ați creat un cont cu furnizorul ales, trebuie setată o zonă sau un pachet. Al nostru a fost configurat astfel:

[![Setări CDN]({{site.baseurl}}/assets/images/1.8/faq/cdn-config.png)]({{site.baseurl}}/assets/images/1.8/faq/cdn-config.png)

Tipul de resursă ar trebui să fie "pull", iar originea ar trebui să fie subdomeniul configurat mai deveme (s.mybbstuff.com în acest caz). Puteți folosi orice CDN hostname doriți - majoritatea furnizorilor vă vor da un subdomeniu al lor dacă nu doriți să configurați registrele CNAME DNS și așa mai departe.

# Setarea forumului MyBB să folosească CDN-ul

Acum că CDN-ul este configurat, este timpul să schimbăm setările MyBB pentru a se folosi de acesta. Logați-vă în Panoul de Control al Administratorului și accesați `Configuration > Settings > Server and Optimization Options`. Veți vedea setările CDN aproape de partea din jos a paginii. Puteți schimba setările pentru a se potrivi nevoilor voastre. În cazul nostru, setările arătau astfel:

- **Use a CDN?:** Yes
- **URL to use for static files:** Acesta este hostname-ul CDN configurat la pasul doi. În cazul nostru, *http://cdn.mybbstuff.com*
- **Path to store static files:** Aceasta este calea către subdomeniul setat mai devreme pentru fișierele statice care trebuie stocate. Toate fișierele care urmează să fie încărcate și cele de stil vor fi salvate aici de acum înainte. În cazul nostru, calea este *“/home/euan/webapps/s_mybbstuff_com”*

Odată configurat, salvați setările și reîncărcați pagina principală a foumului. Toate imaginile, fișierele de stil și cele JavaScript sunt acum încărcate de la un CDN.
