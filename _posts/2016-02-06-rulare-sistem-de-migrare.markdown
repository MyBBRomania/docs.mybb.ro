---
layout: page
title:  "Rularea Sistemului de Migrare"
categories: migrare
permalink: migrare/rulare-sistem-de-migrare
---

**Ultima versiune a Sistemului de Migrare MyBB importează doar către MyBB 1.8.**

# Cerințe

**Trebuie să aveți o copie de MyBB 1.8 deja instalată pentru a rula Sistemul de Migrare.** Mai multe informații despre cum să instalați MyBB pot fi găsite [aici][mybb-install].

# Pregătire inițială

## Descărcarea pachetului de migrare
În primul rând, trebuie descărcat pachetul care conține Sistemul de Migrare de pe [site-ul MyBB][merge-system]. După ce ați descărcat fișierul zip, dezarhivați-l.

## Încărcarea fișierelor
Odată ce fișierele au fost extrase, încărcați dosarul "merge" pe server, unde se află copia curentă a forumului vostru. **Fișierele trebuie să rămână în dosarul "merge".**

Lucruri de reținut:

- Asigurați-vă că structura dosarului este menținută (de exemplu, fișierele din dosarul admin ar trebui să se afle într-un dosar numit admin, cele din directory ar trebui să fie încărcat într-un dosar numit archive, etc).
- Asigurați-vă că încărcați fișiere .php, .html, .css și orice alt fișier text în modul ASCII, iar fișierele .gif, .jpg, .png sau orice alt fișier binar în modul Binar (vezi docmentația programului FTP folosit).

## Testare
Faceți un backup al bazei de date înainte de a face orice altceva. Apoi, rulați sistemul de migrare o dată pentru a vă asigura că totul funcționează corespunzător. Dacă nu, restaurați backup-ul și raportați erorile pe forumul MyBB.

## Preconfigurare forum
Înainte de a rula sistemul de migrare, vă rugăm să închideți/blocați ambele forumuri pentru a preveni adăugarea sau ștergerea de conținut sau utilizatori noi în timpuil rulări sistemului. Încă odată, vă rugăm să realizați un backup al bazei de date înainte de rulare.

# Rularea Sistemului de Migrare
Dacă întâmpinați vreo problemă, consultați [Pagina de Depănare a Problemelor][troubleshoot-page].

După ce ați încărcat fișierele, introduceți adresa forumului vostru într-un browser, daăugând */merge/* la sfârșit. Astfel, dacă adresa forumul este <a href="http://forumulvostru.ro/forum/">http://forumulvostru.ro/forum/</a> veți introduce <a href="http://forumulvostru.ro/forum/merge/">http://forumulvostru.ro/forum/merge/</a>

## Welcome
Prima pagină pe care o veți vedea este pagina de întâmpinare. În această pagină, trebuie să alegeți platforma și versiunea forumului pe care îl veți converti în MyBB. După ce ați ales, apăsați pe butonul "Next".

## Module Selection (Inițial)
Această pagină vă permite să alegeți ce doriți să importați. După cum puteți vedea, multe module au "dependențe", care necesită rularea unor alte module înainte de rularea modulelor repective.

Primul modul care trebuie rulat pentru realizarea procesului de migrare este modului "Database Configuration", unde veți introduce datele pentru copia existentă a forumului.

## Database Configuration
În această pagină trebuie să introduceți datele legate de baza de date a forumului existent - nu a forumului MyBB spre care migrați.

### Database Engine
Acesta este engine-ul pe care rulează forumul.

### Database Host
Acesta este serverul unde se află baza de date. Dacă găzduirea nu a menționat altceva, ar trebui să fie localhost.

### Database Username
Acesta este numele de utilizator folosit pentru accesarea bazei de date a forumului de la care migrați.

### Database Password
Aceasta este parola corespunzătoare numelui de utilizator introdus.

### Database Name
Acesta este numele bazei de date în care este instalat forumul.

### Table Prefix
Acesta este prefixul pentru fiecare câmp din baza de date a forumului de la care migrați.

## Module Selection (După configurarea Bazei de Date)
După ce ați introdus datele legate de baza de date, alte module vor putea fi rulate. Modulele deja rulate sunt marcate drept completate, iar dacă alt modul depinde de un modul deja rulat, modului va fi eliminat din secția de "dependențe".

## Importing Data (Running an Import Module)
Când alegeți să rulați un modul, veți vedea o pagină care vă permite să alegeți câte elemente vor fi importate deodată și să continuați în mod automat la pagina următoare până când sistemul de migrare finalizează importarea datelor penru acel modul.

Dacă doriți să vă întoarceți la pagina de alegere a modulelor înainte de a rula un modul, trebuie doar să apăsați pe butonul "Back".

## Module Selection (După ce mai multe module au fost rulate)
Odată ce ați rulat mai multe module, veți vedea că din ce în ce mai multe module vor fi disponibile. Modulele de importare nu vor putea fi rulate din nou, datorită riscului de a importa aceleași date a doua oară, care v-ar putea lăsa cu informații duplicate.

## Cleanup
Acesta este pasul final. Acest pas șterge în mod automat toate datele temporare care au fost create în timpul procesului.

De asemenea, veți putea descărca un fișier text sau HTML cu statistici despre migrare.

## Pluginul loginconvert.php
S-ar putea să primiți un mesaj asemănător în timpul migrării: *"Warning: You should upload loginconvert.php to inc/plugins if you wish to convert passwords."*. Asta înseamnă că sistemul de migrare nu a fost capabil să mute pluginul automat. Nu este obligatoriu să-l încărcați în acel moment. Îl puteți încărca după migrare, dar va trebui să fie și activat. Dacă în încărcați în timp ce sistemul ruleză, va fi activat în mod automat.
Notă: Membri convertiți nu vor fi capabili să se logheze până când nu încărcați și activați pluginul.

## Statistici Anonime
Sistemul de Migrare MyBB (RC4 și versiunile mai recente) vă permite să trimiteți statistici anonime despre migrarea efectuată către Grupul MyBB. Aceste informații le permit grupului să îmbunătățească sistemul.

Ce informații sunt trimise?

### Module Rulate
Acestea sunt modulele rulate în timpul migrării (Users, Threads, Posts etc.)

### Informații Numerice
Numărul de utilizatori, subiecte, mesaje etc. care au fost convertite.

### Titlul Forumului
Acesta este titlul / numele forumului de la care migrați. Ajută la filtrarea duplicatelor.

### Adresa IP
Aceasta este Adresa IP a calculatorului.  Ajută la filtrarea duplicatelor.

Dacă nu doriți să trimiteți aceste informații, pur și simplui debifați opțiunea *"Send anonymous statistics about my merge to the MyBB Group"* de pe prima pagină. Nicio informație nu va fi trimisă Groupului MyBB dacă nu doriți acest lucru.

# După rulare

După ce ați folosit Sistemul de Migrare, ar trebui să rulați toate uneltele *"Recount and Rebuild"*, aflate în secțiunea *"Tools and Maintenance"* din AdminCP. După asta, ar trebui reconstruită și memoria cache. În final, este recomandat să verificați toate permisiunile (pentru forumuri și grupuri).


[mybb-install]: /instalare/instalare-mybb/
[merge-system]: http://www.mybb.com/download/merge-system/
[troubleshoot-page]: /migrare/depanare-probleme/

