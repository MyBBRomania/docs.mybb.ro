---
layout: page
title:  "Lipsă Temă"
categories: faq
permalink: 1.8/faq/lipsa-tema
---

# Forumul nu are temă / design

Dacă site-ul vostru arată astfel, s-ar putea ca adresa URL să nu fie introdusă corect:

[![Forum fără temă]({{site.baseurl}}/assets/images/1.8/faq/broken.jpg)]({{site.baseurl}}/assets/images/1.8/faq/broken.jpg)

Pentru a rezolva aceasă problemă, deschideți fișierul `inc/settings.php` și găsiți linia `$settings['bburl']`.

Schimbați valoarea cu URL-ul corespunzător, de exemplu din `$settings['bburl'] = "http://notmysite.com";` în `$settings['bburl'] = "http://mysite.com";`.

În continuare, accesați `Admin CP > Configuration > Site Details` și actualizați și setarea `Board URL`.

# AdminCP nu are temă / design

Dacă doar Panoul de Control al Administratorului arată astfel și ați schimbat numele dosarului în care se află (din */admin* în ceva diferit, precum */panel*), atunci ar trebui să faceți schimbarea și în fișierul `inc/config.php`,

Pentru a rezolva, deschideți fișierul `inc/config.php`, găsiți linia `$config['admin_dir']` și schimbați valoarea cu numele nou al dosarului.
