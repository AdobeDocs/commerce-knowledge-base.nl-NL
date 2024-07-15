---
title: Gegevens exporteren gebruiken om discrepanties vast te stellen
description: Dit artikel verstrekt oplossingen voor het oplossen van problemendiscrepanties in uw gegevens van Magento BI. De Uitvoer van gegevens is een nuttig hulpmiddel om uw gegevens van MagentoBI aan uw brongegevens te vergelijken om gegevensdiscrepanties in uw rapporten te identificeren, vooral als [de kenmerkende controlelijst van de discrepantie van de gegevensdiscrepantie] (/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md) u niet hielp het probleem te identificeren. Dit artikel zal u door een echt voorbeeld van lopen hoe de gegevensdiscrepanties kunnen worden gespeld gebruikend de Uitvoer van Gegevens.
exl-id: b42d585c-ad8c-4685-9ad4-a13686566f18
feature: Commerce Intelligence, Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 0%

---

# Gegevens exporteren gebruiken om discrepanties vast te stellen

Dit artikel verstrekt oplossingen voor het oplossen van problemendiscrepanties in uw gegevens van Magento BI. De Uitvoer van gegevens is een nuttig hulpmiddel om uw gegevens van MagentoBI aan uw brongegevens te vergelijken om gegevensdiscrepanties in uw rapporten te identificeren, vooral als de [ kenmerkende controlelijst van de gegevensdiscrepantie ](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md) u niet hielp te identificeren het probleem. Dit artikel zal u door een echt voorbeeld van lopen hoe de gegevensdiscrepanties kunnen worden gespeld gebruikend de Uitvoer van Gegevens.

Neem deze analyse, bijvoorbeeld:

![](assets/Exports_Discrepancies_1.png)

Er is een verdachte dip in november 2014. $ 500.780,94 aan inkomsten? Dat klinkt niet goed. U hebt bevestigd dat er meer opbrengst die voor de maand van November 2014 in uw brongegevensbestand toont, en u hebt gecontroleerd dat **metrische die Inkomsten** in dit rapport wordt gebruikt correct wordt bepaald. Het lijkt erop dat de gegevens in het Magento BI-gegevenspakhuis onvolledig zijn en kunnen worden bevestigd met behulp van een Data Export.

## De gegevens exporteren {#export}

Klik om aan de slag te gaan in de rechterbovenhoek van het diagram en klik vervolgens op de optie Onbewerkte export in het vervolgkeuzemenu. Hierdoor worden de gegevens achter het diagram onbewerkt geëxporteerd.

![](assets/Export_Discrepancies_5.gif)

In het menu Raw-gegevens exporteren kunt u de tabel selecteren waaruit u wilt exporteren, samen met de kolommen die u in de exportbewerking wilt opnemen. Filters kunnen ook op de resultatenset worden toegepast.

In ons voorbeeld, gebruikt metrisch van de Inkomsten **die op dit rapport wordt gebruikt het** orde \_total **gebied op de** wordt bepaald orden **lijst, gebruikend de** datum **als zijn timestamp die.** In onze uitvoer, willen wij alle **orde \_id** waarden voor November 2014 en hun **orde \_total** omvatten. De **metrische Inkomsten** gebruikt geen filters, maar wij zullen een filter aan de uitvoer toevoegen om het resultaat te beperken dat aan enkel November 2014 wordt geplaatst.

Zo ziet het menu Raw-gegevensuitvoer er in dit voorbeeld uit:

![](assets/Exports_Discrepancies_2.png)

Klik op Gegevens exporteren om het exporteren te starten. Er wordt een venster weergegeven met de details van het exporteren, inclusief de status. Prepping de uitvoer neemt een paar notulen, die nu een goede tijd maakt om een analoog extract van onze brongegevens voor November 2014, met inbegrip van **datum, orde \_id** uit te voeren, en **orde \_total**. We openen dit bestand in Excel en laten het los, want we komen er zo meteen op terug.

Wanneer de knop Downloaden wordt weergegeven in het venster Exporteren van Raw-gegevens, klikt u erop om het ZIP-bestand met het CSV-bestand te downloaden.

![](assets/Export_Discrepancies_6.png)

Op dit moment moeten we alle gegevens in één blad krijgen om het probleem te vinden. Het CSV-bestand (de export van Magento BI) wordt geïmporteerd in een ander blad van het Excel-bestand dat onze brongegevens bevat.

## Het probleem aanwijzen {#pinpoint}

Nu alle gegevens op één plaats zijn, kunnen we zoeken naar de bron van de discrepantie. Door het aantal rijen op elk blad te vergelijken, kunnen we het probleem beter identificeren. Laten we elke situatie nader bekijken.

### Beide bladen bevatten hetzelfde aantal rijen

Als beide systemen de zelfde rijtelling hebben en **metrische Inkomsten** niet de brongegevens aanpassen, dan moet **orde \_total** ergens weg zijn. Het is mogelijk dat het **orde \_total** gebied in uw brongegevensbestand is bijgewerkt en Magento BI niet deze veranderingen opneemt.

Om dit te bevestigen, neem een blik bij al dan niet de **orde \_total** kolom opnieuw wordt gecontroleerd. Ga naar de Data Warehouse Manager en klik op de ordertabel. U zult [ recheck frequentie ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html) zien die in &quot;Veranderingen wordt vermeld?&quot; kolom. Het **orde \_total** gebied zou moeten worden geplaatst om zo vaak opnieuw te controleren aangezien het wordt verwacht om te veranderen; als het niet is, ga door en plaats het aan uw gewenste recheck frequentie.

### ![](assets/Export_Discrepancies_4.gif)

Als de frequentie voor opnieuw controleren al correct is ingesteld, is er iets anders mis. Verwijs naar de [ Contactpersoon sectie van de Steun ](#support) aan het eind van dit artikel voor volgende stappen.

## De brondatabase heeft meer rijen dan Magento BI {#morerows}

Als de brondatabase meer rijen heeft dan Magento BI en de tussenruimte groter is dan het aantal bestellingen dat u tijdens een updatecyclus binnen kunt verwachten, kan er een verbindingsprobleem zijn. Dit betekent dat Magento BI niet in nieuwe gegevens van het brongegevensbestand kan trekken, wat om verscheidene redenen kan gebeuren.

Navigeer naar de pagina Verbindingen en bekijk de status van de gegevensbron die de ordetabel bevat:

1. **als de status re-auth** is, gebruikt de verbinding niet de correcte geloofsbrieven. Klik in de verbinding, voer de juiste gegevens in en probeer het opnieuw.
1. **als het statuut** ontbroken is, kan de verbinding niet behoorlijk op de serverzijde worden opgesteld. Mislukte verbindingen komen gewoonlijk voort uit een onjuiste gastheernaam of de doelserver die geen verbindingen op de gespecificeerde haven goedkeurt.Klik in de verbinding en controleer de spelling van hostname tweemaal en dat de correcte haven is ingegaan. Aan de serverzijde, zorg ervoor dat de haven verbindingen kan goedkeuren en dat uw firewall het Magento BI IP adres (54.88.76.97/32) zoals toegestaan heeft. **als de verbinding** blijft ontbreken, verwijs naar de [ Contactpersoon sectie van de Steun ](#support) aan het eind van dit artikel voor volgende stappen.
1. **als de status Succes** is, dan is de verbinding niet het probleem en de steun RJ moet betrokken worden. Verwijs naar de [ Contactpersoon sectie van de Steun ](#support) aan het eind van dit artikel voor volgende stappen.

## De brondatabase heeft MINDER rijen dan Magento BI {#lessrows}

Als het brongegevensbestand minder rijen dan Magento BI heeft, dan is het mogelijk dat de rijen uit het brongegevensbestand worden geschrapt en Magento BI niet deze schrappingen opneemt. ** [ het Schrappen van gegevens ](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) kan tot discrepanties, langere updatetijden, en een stroom van logistieke hoofdpijnen** leiden, zodat adviseren wij u nooit gegevens zult schrappen tenzij het echt noodzakelijk is.

Als rijen echter uit de tabel worden verwijderd, bekijkt u de frequentie voor het opnieuw controleren van de primaire sleutel. Als u de primaire sleutel opnieuw controleert, wordt de tabel gecontroleerd op verwijderde rijen.

In de Manager van de Data Warehouse, worden de primaire zeer belangrijke kolommen duidelijk met een zeer belangrijk symbool. In ons voorbeeld, is de primaire sleutel **orde \_id** kolom:

![](assets/Export_Discrepancies_3.png)

Als de primaire sleutel reeds wordt geplaatst om worden opnieuw gecontroleerd of de rijen worden nooit geschrapt van deze lijst, dan zult u steun RJ nodig hebben om het probleem te identificeren. Raadpleeg de volgende sectie voor de volgende stappen.

## Contact opnemen met ondersteuning {#support}

Als u niet de bron van het probleem kunt bepalen, zult u in Steun RJ moeten herhalen. Voer de volgende handelingen uit voordat u een ticket verzendt:

* **als uw brongegevensbestand en Magento BI het zelfde aantal rijen** hebben en frequenties opnieuw controleren correct worden geplaatst, voer VLOOKUP in uw spreadsheet **uit om te vinden welke orde \_id waarden een verschillende orde \_total waarde tussen Magento BI en uw brongegevensbestand hebben.** Neem deze waarden op wanneer u uw ticket verzendt.
* **als uw brongegevensbestand MEER rijen dan Magento BI** heeft en de verbinding als Succes toont of blijft ontbreken, zullen wij de naam van de verbinding en het foutenbericht moeten kennen u ziet, als er is.
* **als uw brongegevensbestand KLEINE rijen dan Magento BI heeft,** de rijen worden niet geschrapt van de lijst, en de frequenties worden opnieuw gecontroleerd correct geplaatst, voer VLOOKUP in uw spreadsheet **uit om te vinden welke orde \_id waarden in Magento BI** maar niet in uw brongegevensbestand zijn. Neem deze waarden op wanneer u uw ticket verzendt.

## Verwante

* [Checklist voor diagnostische gegevensdiscrepantie](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md)
* [ voorleggen een kaartje van de gegevensdiscrepantie ](https://support.magento.com/hc/en-us/articles/360016506472-Submitting-a-data-discrepancy-ticket)
