---
layout: page
title:  "Instalare MyBB"
categories: instalare
permalink: instalare/instalare-mybb
---


## Preparare

### Descărcarea Fișierelor MyBB

1. În primul rând, descărcați ultma versiune MyBB de pe [pagina de descărcări][mybb-desc].
2. După descărcare, dezarhivați fișierul.
	- Pentru Windows, puteți folosi fie [utilitatea][win-zip] care vine cu sistemul de operare, fie o aplicație precum [7-zip][7zip].
	- Pentru sistemele *nix puteți folosi comanda `unzip mybb-package-name.zip`

### Încărcarea Fișierelor

În arhiva descărcată anterior se află două directoare: **Documentation** și **Upload**. Directorul Documentation conține informații utile, însă nu e necesar să fie încărcat pe server.

În continuare, trebuie să încărcați conținutul directorului `Upload/` în directorul rădăcină (root) al site-ului vostru web (uneori denumit `www`, `public_html`, `htdocs` sau `httpdocs`) sau într-un subdirector al directorului rădăcină (precum /forum sau /comunitate).

Procesul de încărcare a fișierelor pe server va depinde de serviciul de găzduire ales, însă cea mai comună metodă este FTP. [FileZilla][filezilla] este un client FTP gratuit potrivit pentru situația de față.

### Permisiunile Fișierelor

Pentru funcționarea corectă a formului, este necesară modifcarea permisiunilor unor fișiere. După ce ați încărcat fișierele pe server, redenumiți fișierul *config.default.php* în *config.php* din directorul `inc/`

#### Sisteme *nix via CHMOD

**Dacă aveți acces SSH**, puteți aplica permisiunile necesare folosind următoarea comandă, executată din directorul MyBB rădăcină:

{% highlight sh %}
chmod 666 inc/config.php inc/settings.php
chmod 777 cache/ cache/themes/ uploads/ uploads/avatars/
{% endhighlight %}

Opțional, puteți aplica următoarele permisiuni:

{% highlight sh %}
chmod 666 inc/languages/english/*.php inc/languages/english/admin/*.php
chmod 777 cache/ cache/themes/ uploads/ uploads/avatars/ admin/backups/
{% endhighlight %}

**Dacă nu aveți acces SSH**, folosind FileZilla, permisiunile fișierelor și directoarelor pot fi schimbate apăsând click dreapta și alegând **File Attributes**.

#### Sisteme Windows

Pentru serverele care rulează pe Windows, trebuie să urmați [aceste instrucțiuni][win-perm]. În general, fișierele și directoarele listate mai sus necesită permisiuni **Full modify**.

## Instalare

Pentru a accesa sistemul de instalare, trebuie să navigați către directorul `install/` al site-ului vostru folosind un browser web. De exemplu, dacă domeniul vostru este exemplu.ro și ați încărcat fișierele MyBB în directorul rădăcină, introduceți adresa [http://exemplu.ro/install](http://exemplu.ro/install), iar dacă ați încărcat fișierele într-un subdirector `forum/`, folosiți adresa [http://exemplu.ro/forum/install](http://exemplu.ro/forum/install).

### Bine ați venit

Dacă ați încărcat fișierele corespunzător și ați accesat sistemul de instalare, ar trebui să vedeți o pagină asemănătoare:

[![Pagina de întâmpinare](/docs.mybb.ro/assets/images/install/welcome.jpg)](/docs.mybb.ro/docs.mybb.ro/assets/images/install/welcome.jpg)

Tot ceea ce trebuie să faceți este să apăsați pe butonul **Next**.

### Acord de licență

MyBB folosește licența GNU LGPL. Pentru a putea folosi această platformă, trebuie să citiți și să fiți de [acord cu licența][licenta]. Licența trebuie repectată pe toată perioada în care platforma este instalată. După ce ați citit acordul, apăsați butonul **Next** pentru a trece la următorul pas.

Dacă doriți să aflați mai multe informații despre licența GNU LGPL și ceea ce reprezintă, [consultați site-ul GNU][lgnu].

[![Licența GNU LGPL](/docs.mybb.ro/assets/images/install/license.jpg)](/docs.mybb.ro/docs.mybb.ro/assets/images/install/license.jpg)

### Verificarea Cerințelor

Această pagină verifică dacă serverul îndeplinește [cerințele][mybb-req] necesare pentru a rula MyBB.

[![Verificare Cerințe](/docs.mybb.ro/assets/images/install/requirements.jpg)](/docs.mybb.ro/assets/images/install/requirements.jpg)

### Configurare Bază de Date

Această pagină e dedicată configurarii bazei de date. Dacă aveți Javascript activat, doar câmpurile relevante sistemului ales vor fi afișate.

#### Database Engine

Acesta este sistemul pe care doriți să-l folosiți. Opțiunile care ar putea fi disponibile sunt MySQL, MySQL Improved, SQLite 3 sau PgSQL. Cel mai probabil, doar MySQL sau ceva asemănător va fi disponibil, deci asta ar trebui să fie opțiunea potrivită pentru voi. Dacă aveți opțiunea de a alege dintre MySQL și MySQL Improved, de obicei, varianta Improved este alegerea mai bună.

#### Database Host

Acesta este serverul în care se află baza de date. Dacă găzduirea nu menționează altceva, ar trebui să fie localhost. Această opțiune nu este necesară pentru SQLite.

#### Database Username

Acesta este numele de utilizator pe care l-ați creat sau îl folosiți pentru a accesa baza de date. Această opțiune nu este necesară pentru SQLite.

#### Database Password

Aceasta este parola pentru numele de utilizator introdus anterior. Această opțiune nu este necesară pentru SQLite.

#### Database Name

Acesta este numele bazei de date în care doriți să instalați MyBB. Această opțiune nu este necesară pentru SQLite.

#### Database Path

Aceasta este calea în care doriți să salvați fișierul SQLite. Această opțiune este necesară doar dacă ați ales **SQLite 3**.

#### Table Prefix

Acesta este prefixul pentru tabelele din baza de date. Dacă nu aveți o altă instalație MyBB în aceeași bază de date care folosește prefixul `mybb_`, puteți lăsa câmpul așa cum este.  Dacă aveți deja o instalație MyBB în baza de date, ar trebui să schimbați prefixul.

Odată ce ați introdus datele corecte, puteți apăsa pe butonul **Next**. Dacă sistemul de instalare nu poate accesa baza de date, veți primi un mesaj care menționează acest lucru, deci va trebui să verificați datele introduse.

Dacă aveți probleme cu acest pas, contactați găzduirea pentru a vedea care sunt datele corecte. Acestea pot fi de obicei aflate din panoul de control al găzduirii (ex: cPanel, Ensim, DirectAdmin, Plesk).

[![Verificare Baza de Date](/docs.mybb.ro/assets/images/install/database.jpg)](/docs.mybb.ro/assets/images/install/database.jpg)

### Crearea Tabelelor

În această pagină sunt introduse tabelele în baza de date. Nu e necesar decât să așteptați să apară butonul **Next** pentru a trece la următorul pas.

[![Crearea Tabelelor](/docs.mybb.ro/assets/images/install/table.jpg)](/docs.mybb.ro/assets/images/install/table.jpg)

### Inserarea Datelor

În acest pas, datele implicite sunt introduse în tabelele create anterior. La fel ca și la pasul precedent, trebuie doar să apăsați butonul **Next**.

[![Inserarea Datelor](/docs.mybb.ro/assets/images/install/populate.jpg)](/docs.mybb.ro/assets/images/install/populate.jpg)

### Instalarea Temei

Tema implicită este importată în forum. Trebuie doar acționat butonul **Next** pentru a trece la următoarea pagină.

[![Inserarea Temei](/docs.mybb.ro/assets/images/install/theme.jpg)](/docs.mybb.ro/assets/images/install/theme.jpg)

### Configurarea Forumului

Aceste setări sunt cruciale pentru forumul vostru. MyBB încearcă să completeze aceste câmpuri cu valorile corecte, însă este recomandat să le verificați. Aceste setări pot fi schimbate mai târziu dacă este necesar.

#### Forum Name

Acesta este numele forumului pe care în instalați. Implicit, este **Forums**.

#### Forum URL

Aceasta este adresa către forumul vostru. Ar trebui să fie completat automat, dar este bine să vă asigurați că URL-ul este corect. Nu uitați că nu ar trebui să conțină un slash la sfârșit (trailing slash).

#### Website Name

Acesta este numele site-ului vostru web (dacă aveți unul). Această setare este pentru link-ul **Your Website** aflat în partea de jos a forumului vostru. Numele este pur și simplu textul pe care doriți să-l folosiți pentru adresa site-ului.

#### Website URL

Acesta este URl-ul către site-ul vostru web (dacă aveți unul). Dacă nu aveți unul, puteți să lăsați acest câmp gol sau să introduceți adresa forumului.

#### Cookie Domain

Acesta este domeniul web pentru care va fi setat modulul cookie. Începând cu seria 1.4, acest câmp este completat cu datele potrivite.

#### Cookie Path

Aceasta este calea în care va fi setat modulul cookie. Dacă aveți mai mult de un forum MyBB instalat pe acest domeniu, este recomandat să schimbați valoarea câmpului către calea forumului (de exemplu, `/forum/`). Începând cu seria 1.4, acest câmp este completat cu datele potrivite.

#### Contact Email

Aceasta este adresa de email pe care membri comunității vă vor putea contacta folosind link-ul **Contact Us** aflat în partea de jos a forumului. Aceeași adresă va fi folosită și ca adresa de email a webmaster-ului, când forumul trimite email-uri.

[![Configurarea Forumului](/docs.mybb.ro/assets/images/install/config.jpg)](/docs.mybb.ro/assets/images/install/config.jpg)

### Cont Administrator

Contul de administrator este primul cont al forumului (identificat de ID-ul de utilizator #1). Acest cont are acces la toate secțiunile din Admin CP.

### Username

Acesta este numele de utilizator al contului de administrator.

### Password și Retype Password

Aceasta este parola pentru contul de administrator.

### Email Address

Aceasta este adresa de email pentru contul de administrator.

[![Cont Administrator](/docs.mybb.ro/assets/images/install/admin.jpg)](/docs.mybb.ro/assets/images/install/admin.jpg)

### Finalizare Instalare

**Felicitări!** Ați instalat cu succes forumul vostru MyBB. Puteți șterge directorul `install/` de pe server pentru a preveni rularea sistemului de instalare din nou. MyBB nu va funcționa decât dacă sistemul de instalare este șters sau blocat.

După instalare, ar trebui să existe un fișier numit `lock` în directorul `install/` care va preveni accesul la acest sistem. Dacă nu există și nu doriți să ștergeți acest director, creați fișierul.

[![Finalizare Instalare](/docs.mybb.ro/assets/images/install/finish.jpg)](/docs.mybb.ro/assets/images/install/finish.jpg)

## Instalare Rapidă SSH

Dacă aveți acces SSH pentru serverul *nix, puteți folosi una dintre metodele de mai jos pentru a sări peste pașii de preparare menționați anterior.

### Cerințe:
- *acces* - Acces la server prin Linii de comandă (Command Line Access)
- *wget, aria2 (versiunea >= 1.9.3), curl sau lynx* - Comanda folosită, depinde care o alegeți. Ar trebui să fie prezente sau instalabile pe orice server *NIX (Linux, UNIX sau Mac)
- *unzip, mv, rm sau chmod* - Toate aceste comenzi sunt necesare și ar trebui să fie prezente pe orice server *NIX.

**`wget`**
{% highlight sh %}
wget --content-disposition http://www.mybb.com/download/latest -O mybb.zip
unzip mybb.zip "Upload/*"
mv Upload/* .
rm -Rf Upload mybb.zip
mv inc/config.default.php inc/config.php
chmod -R 0777 cache uploads inc/settings.php inc/config.php
{% endhighlight %}

**`curl`**
{% highlight sh %}
curl http://www.mybb.com/download/latest -o mybb.zip
unzip mybb.zip "Upload/*"
mv Upload/* .
rm -Rf Upload mybb.zip
mv inc/config.default.php inc/config.php
chmod -R 0777 cache uploads inc/settings.php inc/config.php
{% endhighlight %}

**`aria2c`**
{% highlight sh %}
aria2c http://www.mybb.com/download/latest -o mybb.zip
unzip mybb.zip "Upload/*"
mv Upload/* .
rm -Rf Upload mybb.zip
mv inc/config.default.php inc/config.php
chmod -R 0777 cache uploads inc/settings.php inc/config.php
{% endhighlight %}

**`lynx`**
{% highlight sh %}
lynx -crawl -dump http://www.mybb.com/download/latest > mybb.zip
unzip mybb.zip "Upload/*"
mv Upload/* .
rm -Rf Upload mybb.zip
mv inc/config.default.php inc/config.php
chmod -R 0777 cache uploads inc/settings.php inc/config.php
{% endhighlight %}


[mybb-desc]: http://www.mybb.com/download
[win-zip]: http://windows.microsoft.com/en-us/windows/compress-uncompress-files-zip-files
[7zip]: http://www.7-zip.org/
[filezilla]: https://filezilla-project.org/
[win-perm]: http://technet.microsoft.com/en-us/library/bb727008.aspx
[licenta]: http://www.mybb.com/about/license
[lgnu]: http://www.gnu.org/licenses/lgpl.html
[mybb-req]: http://docs.mybb.com/1.8/install/requirements
