---
layout: page
title:  "Lipsă Editor MyCode (BBCode)"
categories: faq
permalink: 1.8/faq/lipsa-mycode
---

# Despre probleme dispariției editorului MyCode (BBCode)

Mulți dintre utilizatorii MyBB au raportat lipsa editorului. Această problemă poate avea multiple cauze, însă pentru a depista problema voastră, vom începe cu cel mai simplu caz: editorul este dezactivat.

Pentru a verifica dacă este sau nu activat, accesați: `Admin CP -> Configuration -> Settings -> Clickable Smilies and BB Code -> Clickable MyCode Editor` și bifați **ON**.

Dacă setarea de mai sus este activată însă nu puteți vedea editorul, **dar** ceilalți utilizatori pot, asigurați-vă că este activat și din User CP. Pentru activare, accesați `User CP -> Edit Options -> Other Options` și bifați **"Show the MyCode formatting options on the posting pages."**

Acum, dacă ambele setări sunt activate și tot nu puteți vedea editorul MyCode, cel mai probabil lipsește ceva. În continuare găsiți niște probleme și soluții adiționale, ordonate în funcție de probabilitatea de a cauza și rezolva problema.

## CloudFlare
**Ignorați această soluție dacă nu folosiți CloudFlare.**

	Logați-vă în panoul vostru de control CloudFlare
	Editați Setările
	Accesați tab-ul Performance
	Dezactivați Rocket Loader și/sau Auto Minify
	
## Tema Editorului
Accesați `Admin CP -> Templates & Styles -> Themes -> <Your theme> -> Editor style` Schimbați pe *Office*.

**Dacă această soluție funcționează, înseamnă că problema se află în fișerele temei editorului.**

**Reîncărcați SCEditor**

Reîncărcați întregul dosar `sceditor` în `jscripts/sceditor`.

## Problemă de Șabloane
Accesați `Admin CP -> Templates & Styles -> Templates -> <Your theme> -> New Thread Templates -> newthread` și `Admin CP -> Templates & Styles -> Templates -> <Your theme> -> New Reply Templates -> newreply`.

Asigurați-vă că există `{$codebuttons}` imediat după `<textarea id="message" name="message" rows="20" cols="70" tabindex="2" >{$message}</textarea>` în șablonul *newreply* și imediat după `<textarea name="message" id="message" rows="20" cols="70" tabindex="2">{$message}</textarea>` în șablonul *newthread*.

# Restaurarea Șabloanelor
*Această soluție este validă doar dacă editorul a dispărut în urma realizării unui upgrade / downgrade.*

Găsiți șabloanele actualizate / modificate pentru tema curentă și restaureți-le la starea inițială.

Accesați `Admin CP -> Templates & Styles -> Templates -> Find Updated Templates`

# Interogare SQL pentru reactivarea forțată a editorului
Dacă editorul apare doar pentru voi sau câțiva din membrii comunității, puteți rula următoarea interogare pentru a activa *"Show the MyCode formatting options on the posting pages"* pentru întregul forum:

	UPDATE `mybb_users` SET `showcodebuttons` = '1' WHERE `showcodebuttons` = '0'

**Asigurați-vă că realizați un backup bazei de date înainte de a rula manual orice interogare SQL, inclusiv cea de mai sus.**

**Nu uitați să schimbați prefixul tabelelor în interogarea de mai sus din `mybb_` dacă este necesar.**
