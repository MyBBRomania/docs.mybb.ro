---
layout: page
title:  "Probleme Mail"
categories: faq
permalink: 1.8/faq/probleme-mail
---

# Probleme Mail
Dacă întâmpinați probleme cu primirea mail-urilor trimise de pe forumul dvs, vă rugăm să urmați pașii de mai jos înainte să solicitați ajutor.

În primul rând, verificați dacă mail-ul a fost trimis în folderul spam/junk. Asta poate să se întâmple dintr-o varietate de motive, unul dintre ele fiind aflarea serverului găzduirii folosite pe lista neagră din cauza trimiterii anterioare de spam (de obicei din cauza unui client).

## Testare PHP Mail
MyBB folosește [funcția PHP Mail][php-mail] pentru a trimite mail. De aceea, este important ca funcția PHP Mail să funcționeze.

**Script de testare:**
Creați un nou fișier `.php` cu următorul conținut:
```php
    <?php
     error_reporting(E_ALL);
       $to = 'your.email@address.com';
       if(mail($to, 'Testing mail', 'This is a mailing test to see if PHP mail works.'))
       {
        echo 'Mail was sent by PHP';
       }
       else
       {
        echo 'PHP could not send the mail';
        print_r(error_get_last());
       }
    ?>
```
Înlocuiți `your.email@address.com` cu adresa voastră de email. Încărcați acest fișier pe server și accesați-l din browser pentru a rula testul.

Ar trebui să afișeze `Mail was sent by PHP` și să nu fie afișate erori.

## Restricții Găzduire
Unele găzduiri web au anumite restricții. De exemplu, unele necesită ca adresa `From` să fie configurată pe serverul lor, iar altele dezactivează funcția PHP Mail complet. Verificați dacă găzduirea voastră a plasat niște restricții în privința trimiterii de mail prin PHP.

Dacă găzduirea voastră permite trimiterea de mail doar de la domeniul lor, editați fișierul `inc/functions.php` pentru a rezolva acest lucru.

Găsiți: `mail($to, $subject, $message, $headers);`

Adăugați înainte: `ini_set("sendmail_from", "forum@YOURDOMAIN.com");`

Rezultatul final ar trebui să fie:
```php
ini_set("sendmail_from", "forum@YOURDOMAIN.com"); mail($to, $subject, $message, $headers);
```

`YOURDOMAIN.com` trebuie să fie înlocuit cu domeniul unde este găzduit forumul.

[php-mail]: https://secure.php.net/manual/en/function.mail.php
