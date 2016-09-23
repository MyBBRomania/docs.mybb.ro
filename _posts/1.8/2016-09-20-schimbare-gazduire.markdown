---
layout: page
title:  "Schimbare Găzduire Web"
categories: faq
permalink: 1.8/faq/schimbare-gazduire
---

Procesul de migrare către o nouă găzduire web constă în trei secțiuni: realizarea unui backup, înărcarea datelor pe serverul noii găzduiri și transferul domeniului.*

# Backup Date
1. Logați-vă în Panoul de Control al Administratorului (AdminCP) și dezactivați toate modificările (pluginurile). Pentru a face asta, navigați la `Configuration` și setați `Disable All Plugins` pe `Yes`.
2. Închideți-vă forumul navigând la `Configuration`, `Board Online / Offline` și setând forumul pe închis. Acest lucru va asigura ca datele exportate la pasul următor să fie la curent și că nicio activitate nu va fi pierdută în timpul migrării.
3. Exportați baza de date prin navigarea către secțiunea `Tools & Maintenance`, `Backup Database`, `New Backup`. Selectați toate tabelele folsind opțiunea `Select All`, bifați `GZIP Compressed`, `Download`, `Structure and Data` și `Analyze and Optimize Selected Tables`. Salvați fișierul rezultat pe calculatorul vostru. Vedeți imaginea de mai jos pentru referință.
[![Export Backup]({{site.baseurl}}/assets/images/1.8/faq/backupdb-export.png)]({{site.baseurl}}/assets/images/1.8/faq/backupdb-export.png)
4. Folosind un client FTP, precum [Filezilla][filezilla], descărcați **TOATE** fișierele forumului pe calculatorul vostru.

[filezilla]: https://filezilla-project.org/download.php?show_all=1

# Încărcarea Datelor pe Noul Server
1. Creați o nouă bază de date și un utilizator pentru aceasta la noul serviciu de găzduire web. Schimbați configurația bazei de date în fișierul `./inc/config.php`, astfel încât să se potrivească noilor valori.
2. Folosind o unealtă precum phpMyAdmin, accesați baza de date creată mai sus și importați datele salvate în cadrul pasului 3 de la secțiunea *Backup Date* de mai sus.
3. Folosind un client FTP, încărcați **TOATE** fișierele forumului pe noul server.

# Transfer Domeniu
În majoritatea cazurilor, noua găzduire vă va ajuta să vă transferați domeniul pentru a indica către sistemele lor. Dacă nu, vă rugăm să-i contactați pentru asistență în privința schimbării setărilor pentru domeniul vostru, din moment ce setările diferă de la găzduire la găzduire. De asemenea, este de reținut faptul că propagarea DNS (timpul necesar pentru calculatoare să afle că domeniul vostru indică spre un loc nou) poate dura câteva ore, deci dacă nu se actualizează imediat, nu ar trebui să existe nicio grijă.

# Completarea Transferului
1. Domeniul vostru ar trebui să indice către noua găzduire, iar forumul vostru ar trebui să funcționeze precum a funcționat la vechea găzduire. Dacă apar probleme, [creați un subiect pe forumul MyBB România][subiect-suport] sau contactați noua găzduire web pentru asistență.
2. Redeschideți-vă forumul prin urmarea pașilor 1,2 din secțiunea *Backup Date* de mai sus, însă alegând opțiunea de deschidere.

[subiect-suport]: http://mybb.ro/
