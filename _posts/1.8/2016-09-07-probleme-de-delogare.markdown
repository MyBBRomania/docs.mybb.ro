---
layout: page
title:  "Probleme de Delogare"
categories: faq
permalink: 1.8/faq/probleme-de-delogare
---

# Probleme de Delogare

S-ar putea ca ID-ul vostru de utilizator să nu fi putut fi verificat pentru a vă deloga. Asta înseamnă că link-ul vostru de delogare nu conține un SID care este necesar încă de la versiunea 1.2.8. Există două motive posibile pentru asta:

1. Forumul a fost actualizat la o nouă versiune de MyBB, dar niște date din șabloane nu au fost actualizate.
2. Folosiți un șablon conceput pentru o versiune de MyBB mai veche decât 1.2.8 și astfel lipsește componenta SID.

O rezolvare pentru ambele probleme poate fi găsită [aici][community-link], fiind niște instrucțiuni pentru actualizarea manuală a șabloanelor. Notă: Va trebui să faceți acest lucru pentru fiecare temă de pe forum care nu conține un link cu SID.

Dacă după ce ați făcut schimbarea de mai sus încă nu sunteți capabil să vă delogați, s-ar putea ca problema să provină de la setările pentru cookies. Fie setările pentru cookies au fost schimbate și nu mai corespund cu fișierele cookies salvate, iar când încercați să vă delogați, MyBB încearcă să șteargă fișiere care nu există, fie aveți niște fișiere cookies de la o sesiune anterioară (când setările pentru cookies erau diferite) și un set de cookies pentru aceast sesiune (cu noile setări). În acest caz, MyBB va șterge noile fișiere cookies, dar cele vechi vor rămâne, ceea ce vă vor face incapabili de a vă deloga.

Vă rugăm să citiți [Probleme de Logare][probleme-logare] sau [Cookies][cookies]. În ambele situații, cea mai bună soluție este să vă ștergeți fișierele cookies din browser.

[community-link]: https://community.mybb.com/showthread.php?tid=25210&pid=177101#pid177101
[probleme-logare]: {{site.baseurl}}/1.8/faq/probleme-de-logare
[cookies]: /
