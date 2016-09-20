---
layout: page
title:  "Erori Comune"
categories: faq
permalink: 1.8/faq/erori-comune
---

# Introducere
În timpul utilizării formului vostru, s-ar putea să întâmpinați o Eroare Internă MyBB, o eroare SQL, o eroare de permisiune etc. Aceste erori vă pot limita modul în care vă folosiți forumul, de aceea, pe această pagină, veți vedea câteva din cele mai comune erori întâlnite, alături de modul de rezolvare.

# Erori Interne MyBB

## MyBB Error (41)
**Tipul Erorii:** Eroare MyBB (41)

**Mesajul Erorii:** *Your board has not yet been installed and configured. Please do so before attempting to browse it.*

**Informații:** Forumul vostru nu a fost încă instalat și configurat. Această eroare apare atunci când fișierul `inc/config.php` nu este configurat corect. Dacă nu ați instalat încă forumul, trebuie să accesați `install/index.php` în browser și să urmați procesul de instalare. Dacă ați instalat deja forumul și aveți date în baza de date, trebuie să deschideți fișierul `inc/config.php` și să introduceți manual informațiile despre baza de date folosită.

## MyBB Error (42)
**Tipul Erorii:** Eroare MyBB (42)

**Mesajul Erorii:** *Your board has not yet been upgraded. Please do so before attempting to browse it.*

**Informații:** Forumul vostru nu a fost încă actualizat (upgradat). Această eroare apare atunci când încercați să treceți la o versiune majoră (ex: de la 1.6.x la 1.8.x), dar nu rulați scriptul de upgrade după încărcarea noilor fișiere. Pentru a rezolva această problemă, accesați `install/upgrade.php` din browser, alegeți vechea versiune din listă și urmați instrucțiunile date de script.

## MyBB Error (43)
**Tipul Erorii:** Eroare MyBB (43)

**Mesajul Erorii:** *The install directory (install/) still exists on your server and is not locked. To access MyBB please either remove this directory or create an empty file in it called lock.*

**Informații:** Dosarul de instalare (`install/`) încâ există pe server și nu este blocat. Pentru a vă putea accesa forumul, trebuie fie să ștergeți acest dosar, fie să creați un fișier numit `lock` în dosarul respectiv, pentru a-l bloca. MyBB necesită ștergerea sau blocarea acestui dosar, astfel încât nimeni să nu poată rula scriptul de instalare sau de upgrade și să vă corupa sau șteargă baza de date.

## MyBB Error (44)
**Tipul Erorii:** Eroare MyBB (44)

**Mesajul Erorii:** *MyBB was unable to load the SQL extension. Please contact the MyBB Group for support. MyBB Website*

**Informații:** Acesată eroare apare atunci când tipul bazei de date a fost setat incorect în `inc/config.php`. Pentru a rezolva problema, deschideți fișierul `inc/config.php` și verificați linia `$config['database']['type']`. O problemă comună este scrierea tipului `mysql` în loc de `mysqli` sau invers. Dacă nu știți ce trebuie introdus aici, contactați firma de găzduire.

# Erori SQL

## Eroarea MySQL 0 -
**Baza de date:** *MySQL*

**Eroare SQL:** *0 -*

**Interogare:** *[READ] Unable to select database*

**Informații:** Eroarea are loc atunci când este utilizat MySQL, iar numele bazei de date sau numele utilizatorului este incorect în `inc/config.php`. Pentru rezolvare, deschideți `inc/config.php` și verificați valorile pentru `$config['database']['database']` și `$config['database']['username']`. Dacă nu știți ce valori ar trebui să fie introduse aici, contactați furnizorul de găzduire.

## Eroarea MySQL 2005
**Baza de date:** *MySQL*

**Eroare SQL:** *2005 - Unknown MySQL server host ‘HOSTNAME’ (11004)*

**Interogare:** *[READ] Unable to connect to MySQL server*

**Informații:** Eroarea are loc atunci când este utilizat MySQL, iar numele de găzduire (hostname) este incorect în `inc/config.php`. Pentru rezolvare, deschideți `inc/config.php` și verificați valoarea pentru `$config['database']['hostname']`. Dacă nu știți ce valoare ar trebui să fie introdusă aici, contactați furnizorul de găzduire.

## Eroarea MySQL 1045
**Baza de date:** *MySQL*

**Eroare SQL:** *1045 - Access denied for user ‘USERNAME’@’HOSTNAME’ (using password: YES)*

**Interogare:** *[READ] Unable to connect to MySQL server*

**Informații:** Eroarea are loc atunci când este utilizat MySQL, iar parola bazei de date este incorectă în `inc/config.php`. Pentru rezolvare, deschideți `inc/config.php` și verificați valoarea pentru `$config['database']['password']`. Dacă nu știți ce valoare ar trebui să fie introdusă aici, contactați furnizorul de găzduire.

## Eroarea MySQL 1146
**Baza de date:** *MySQL*

**Eroare SQL:** *1146 - Table ‘forum_mybb14x.test_datacache’ doesn’t exist*

**Interogare:** *SELECT title,cache FROM test_datacache*

**Informații:** Eroarea are loc atunci când este utilizat MySQL, iar prefixul tabelelor din baza de date este incorect în `inc/config.php`. Pentru rezolvare, deschideți `inc/config.php` și verificați valoarea pentru `$config['database']['table_prefix']`. Dacă nu știți ce valoare ar trebui să fie introdusă aici, contactați furnizorul de găzduire.

## Eroarea MySQL 2013
**Baza de date:** *MySQL*

**Eroare SQL:** *2013 - Lost connection to MySQL server during query*

**Interogare:** *SELECT title,cache FROM mybb_datacache*

**Informații:** Eroarea apare din cauza unei probleme cu conexiunea către baza de date. Furnizorul de găzduire va trebui să rezolve această problemă.

## Eroarea MySQL 2002
**Baza de date:** *MySQL*

**Eroare SQL:** *2002 - Can’t connect to local MySQL server through socket ‘/var/lib/mysql/mysql.sock’*

**Interogare:** *[READ] Unable to connect to MySQL server*

**Informații:** Eroarea apare atunci când serverul MySQL nu funcționează, iar MyBB nu se poate conecta la el. Va trebui să contactați furnizorul de găzduire cu mesajul acestei erori.

## Eroarea MySQL 1054
**Baza de date:** *MySQL*

**Eroare SQL:** *21054 - Unknown column ‘loginattempts’ in ‘field list’*

**Interogare:** `SELECT loginattempts FROM mybb_users WHERE LOWER(username)='username' LIMIT 1`

**Informații:** **Notă:** această rezolvare nu se aplică pentru toate erorile datorate unor *coloane necunoscute*, ci este concepută sepcial pentru interogarea de mai sus (cu un nume de utilizator / prefix de tabel etc. diferit). Vă rugăm să nu sugerați această rezolvare atunci pentru cazul în care cineva are o eroare diferită.

Eroarea are loc atunci când este utilizat MySQL și încercați să faceți upgrade de la 1.4.3 la 1.4.4, după ce ați încărcat toate fișierele noi, însă nu rulați scriptul de upgrade. În 1.4.4, a fost adăugată o nouă coloană, `loginattempts`, în tabelul cu utilizatori. Eroarea apare atunci când fișierul `member.php` al versiunii 1.4.4 încearcă să găsească coloane `loginattempts` în baza de date a versiunii 1.4.3, unde nu există. Pentru a rezolva această eroare, accesați din browser `install/upgrade.php` și alegeți 1.4.2/1.4.3 din listă.

# Alte Erori

## Mesajul Erorii: *The installer is currently locked*
*The installer is currently locked, please remove `lock` from the install directory to continue*

**Informații:** Eroarea are loc atunci când încercați să rulați scriptul de instalare sau de upgrade, dar dosarul `install/` este blocat. Trebuie doar să ștergețifișierul `lock` din dosarul `install/` pentru a continua.

## Mesajul Erorii: *Forbidden*
*You don’t have permission to access `admin/index.php` on this server.*

**Informații:** Eroarea are loc în cele mai multe cazuri din cauza unei probleme cu *mod_security*. *mod_security* este o extensie Apache folosită pentru securitate. În MyBB 1.4, *mod_security* tratează modul în care adresele URL sunt introduse în ACP ca o problemă de securitate, deci vă va bloca accesul.

Ar trebui să contactați furnizorul de găzduire și să-i cereți să vă aprobe domeniul sau contul de găzduire pentru *mod_security*.

## Catchable Fatal Error (4096)
Eroarea are loc atunci când realizați un upgrade al forumului de la versiunea 1.6.4 sau una mai veche către versiunea 1.6.5 sau una mai nouă, sau când instalați o temă care nu a fost actualizată corespunzător. Șablonul *member_register* trebuie să fie actualizat.

1. Intrați în **Admin CP > Templates > (setul dumneavoastră de șabloane) > Member Templats > member_register**.
2. Găsiți:
`{$captcha}`
3. Înlocuiți cu:
`{$hiddencaptcha}`
