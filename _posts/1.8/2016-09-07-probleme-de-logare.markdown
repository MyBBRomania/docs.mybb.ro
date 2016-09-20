---
layout: page
title:  "Probleme de Logare"
categories: faq
permalink: 1.8/faq/probleme-de-logare
---

# Probleme de Logare
În majoritatea cazurilor, problema apare din cauza setărilor incorecte sau nepotrivite cookies. Mai multe informații despre cookies pentru MyBB puteți găsi [aici](/).

Setările pentru cookies pot fi găsite în: **Admin CP > Configuration > Settings > Site Details**. Cele două setări sunt *Cookie Domain* și *Cookie Path*.

Implicit, MyBB sugerează ca setarea Cookie Domain să fie goală, iar Cookie Path să fie **/**. Cu toate că teoretic poate funcționa, în majoritatea cazurilor este inadecvat.

Puteți folosi [această unealtă][cookie-tool] pentru a genera setările potrivite. Aici sunt niște exemple despre cum ar trebui să arate niște setări corecte pentru cookies:

<table>
	<tr>
		<th>URL Forum</th>
		<th>Cookie Domain</th>
		<th>Cookie Path</th>
	</tr>

	<tr>
		<td>http://www.example.com</td>
		<td>.example.com</td>
		<td>/</td>
	</tr>

	<tr>
		<td>http://www.example.com/directory/</td>
		<td>.example.com</td>
		<td>/directory/</td>
	</tr>

	<tr>
		<td>http://www.subdomain.example.com</td>
		<td>subdomain.example.com</td>
		<td>/</td>
	</tr>

	<tr>
		<td>http://www.subdomain.example.com/directory/</td>
		<td>subdomain.example.com</td>
		<td>/directory/</td>
	</tr>
</table>

Aceste setări ar trebui să funcționeze pentru toate instalările de MyBB. Dacă aveți integrare cu un site, setările voastre s-ar putea să necesite o mai mare generalizare.

După ce schimbați setările pentru cookies, vă rugăm să le recomandați utilizatorilor să se delogheze și să își șteargă fișierele cookie deja salvate de către browser, astfe încât noile setări să poată funcționa.

[cookie-tool]: https://docs.mybb.com/tools/cookie-settings
