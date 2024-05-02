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

Dit artikel verstrekt oplossingen voor het oplossen van problemendiscrepanties in uw gegevens van Magento BI. De Uitvoer van gegevens is een nuttig hulpmiddel om uw MagentoBI gegevens met uw brongegevens te vergelijken om gegevensdiscrepanties in uw rapporten te identificeren, vooral als het [checklist voor diagnostische gegevensdiscrepantie](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md) hielp je niet om het probleem vast te stellen. Dit artikel zal u door een echt voorbeeld van lopen hoe de gegevensdiscrepanties kunnen worden gespeld gebruikend de Uitvoer van Gegevens.

Neem deze analyse, bijvoorbeeld:

![](assets/Exports_Discrepancies_1.png)

Er is een verdachte dip in november 2014. $ 500.780,94 aan inkomsten? Dat klinkt niet goed. U hebt bevestigd dat er meer opbrengst die voor de maand van November 2014 in uw brongegevensbestand toont, en u hebt dubbel-gecontroleerd dat **Ontvangsten** Metrisch die in dit rapport wordt gebruikt is correct bepaald. Het lijkt erop dat de gegevens in het Magento BI-gegevenspakhuis onvolledig zijn en kunnen worden bevestigd met behulp van een Data Export.

## De gegevens exporteren {#export}

Klik om aan de slag te gaan in de rechterbovenhoek van het diagram en klik vervolgens op de optie Onbewerkte export in het vervolgkeuzemenu. Hierdoor worden de gegevens achter het diagram onbewerkt geëxporteerd.

![](assets/Export_Discrepancies_5.gif)

In het menu Raw-gegevens exporteren kunt u de tabel selecteren waaruit u wilt exporteren, samen met de kolommen die u in de exportbewerking wilt opnemen. Filters kunnen ook op de resultatenset worden toegepast.

In ons voorbeeld **Ontvangsten** De metrisch die op dit rapport wordt gebruikt gebruikt **order\_total** veld gedefinieerd op **orders** tabel, gebruiken **date** als tijdstempel. Bij onze export willen we alle **order\_id** waarden voor november 2014 en hun **order\_total** . De **Ontvangsten** Metrisch gebruikt geen filters, maar wij zullen een filter aan de uitvoer toevoegen om het resultaat te beperken dat aan enkel November 2014 wordt geplaatst.

Zo ziet het menu Raw-gegevensuitvoer er in dit voorbeeld uit:

![](assets/Exports_Discrepancies_2.png)

Klik op Gegevens exporteren om het exporteren te starten. Er wordt een venster weergegeven met de details van het exporteren, inclusief de status. Het voorbereiden van de export neemt een paar minuten in beslag. Het is nu een goede tijd om een soortgelijk extract van onze brongegevens uit te voeren voor november 2014, inclusief **datum, volgorde\_id** en de **order\_total** . We openen dit bestand in Excel en laten het los, want we komen er zo meteen op terug.

Wanneer de knop Downloaden wordt weergegeven in het venster Exporteren van Raw-gegevens, klikt u erop om het ZIP-bestand met het CSV-bestand te downloaden.

![](assets/Export_Discrepancies_6.png)

Op dit moment moeten we alle gegevens in één blad krijgen om het probleem te vinden. Het CSV-bestand (de export van Magento BI) wordt geïmporteerd in een ander blad van het Excel-bestand dat onze brongegevens bevat.

## Het probleem aanwijzen {#pinpoint}

Nu alle gegevens op één plaats zijn, kunnen we zoeken naar de bron van de discrepantie. Door het aantal rijen op elk blad te vergelijken, kunnen we het probleem beter identificeren. Laten we elke situatie nader bekijken.

### Beide bladen bevatten hetzelfde aantal rijen

Als beide systemen hetzelfde aantal rijen hebben en als **Ontvangsten** metrisch komt niet overeen met de brongegevens, dan de **order\_total** moet ergens zijn. Het is mogelijk dat de **order\_total** is bijgewerkt in uw brongegevensbestand en Magento BI neemt deze veranderingen niet op.

Om dit te bevestigen, bekijk of al dan niet **order\_total** wordt opnieuw gecontroleerd. Ga naar de Data Warehouse Manager en klik op de ordertabel. U ziet de [frequentie opnieuw controleren](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html) weergegeven in de lijst Wijzigingen? kolom. De **order\_total** het veld moet zo vaak worden ingesteld dat het wordt gewijzigd; als dit niet het geval is, gaat u verder en stelt u het in op de gewenste frequentie voor opnieuw controleren.

### ![](assets/Export_Discrepancies_4.gif)

Als de frequentie voor opnieuw controleren al correct is ingesteld, is er iets anders mis. Zie de [Verbinding maken met de sectie Ondersteuning](#support) aan het einde van dit artikel voor de volgende stappen .

## De brondatabase heeft meer rijen dan Magento BI {#morerows}

Als de brondatabase meer rijen heeft dan Magento BI en de tussenruimte groter is dan het aantal bestellingen dat u tijdens een updatecyclus binnen kunt verwachten, kan er een verbindingsprobleem zijn. Dit betekent dat Magento BI niet in nieuwe gegevens van het brongegevensbestand kan trekken, wat om verscheidene redenen kan gebeuren.

Navigeer naar de pagina Verbindingen en bekijk de status van de gegevensbron die de ordetabel bevat:

1. **Als de status Opnieuw auth is** , gebruikt de verbinding niet de correcte geloofsbrieven. Klik in de verbinding, voer de juiste gegevens in en probeer het opnieuw.
1. **Als de status is mislukt** , is de verbinding mogelijk niet correct ingesteld aan de serverzijde. Mislukte verbindingen komen gewoonlijk voort uit een onjuiste gastheernaam of de doelserver die geen verbindingen op de gespecificeerde haven goedkeurt.Klik in de verbinding en controleer de spelling van hostname tweemaal en dat de correcte haven is ingegaan. Aan de serverzijde, zorg ervoor dat de haven verbindingen kan goedkeuren en dat uw firewall het Magento BI IP adres (54.88.76.97/32) zoals toegestaan heeft. **Als de verbinding blijft mislukken** , verwijst u naar de [Verbinding maken met de sectie Ondersteuning](#support) aan het einde van dit artikel voor de volgende stappen .
1. **Als de status is gelukt** , dan is de verbinding niet het probleem en de steun RJ moet worden betrokken. Zie de [Verbinding maken met de sectie Ondersteuning](#support) aan het einde van dit artikel voor de volgende stappen .

## De brondatabase heeft MINDER rijen dan Magento BI {#lessrows}

Als het brongegevensbestand minder rijen dan Magento BI heeft, dan is het mogelijk dat de rijen uit het brongegevensbestand worden geschrapt en Magento BI niet deze schrappingen opneemt. ** [Gegevens verwijderen](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html) Dit kan leiden tot discrepanties, langere updatetijden en een hele reeks logistieke problemen**. Daarom raden we u ten zeerste aan om nooit gegevens te verwijderen, tenzij dat echt nodig is.

Als rijen echter uit de tabel worden verwijderd, bekijkt u de frequentie voor het opnieuw controleren van de primaire sleutel. Als u de primaire sleutel opnieuw controleert, wordt de tabel gecontroleerd op verwijderde rijen.

In de Manager van de Data Warehouse, worden de primaire zeer belangrijke kolommen duidelijk met een zeer belangrijk symbool. In ons voorbeeld is de primaire sleutel **order\_id** kolom:

![](assets/Export_Discrepancies_3.png)

Als de primaire sleutel reeds wordt geplaatst om worden opnieuw gecontroleerd of de rijen worden nooit geschrapt van deze lijst, dan zult u steun RJ nodig hebben om het probleem te identificeren. Raadpleeg de volgende sectie voor de volgende stappen.

## Contact opnemen met ondersteuning {#support}

Als u niet de bron van het probleem kunt bepalen, zult u in Steun RJ moeten herhalen. Voer de volgende handelingen uit voordat u een ticket verzendt:

* **Als uw brongegevensbestand en Magento BI het zelfde aantal rijen hebben** en opnieuw controleren de frequenties correct worden geplaatst, voer VLOOKUP in uw spreadsheet uit **als u wilt weten welke volgorde\_id-waarden een andere volgorde\_total hebben tussen Magento BI en uw brondatabase.** Neem deze waarden op wanneer u uw ticket verzendt.
* **Als uw brondatabase meer rijen heeft dan Magento BI** en de verbinding als Succes toont of blijft ontbreken, zullen wij de naam van de verbinding en het foutenmelding moeten weten u ziet, als er is.
* **Als uw brondatabase MINDER rijen heeft dan Magento BI,** de rijen worden niet geschrapt van de lijst, en de frequenties worden opnieuw gecontroleerd correct geplaatst, voert VLOOKUP in uw spreadsheet uit **om te vinden welke orde \_id waarden in Magento BI zijn** maar niet in uw brondatabase. Neem deze waarden op wanneer u uw ticket verzendt.

## Verwante

* [Checklist voor diagnostische gegevensdiscrepantie](/help/troubleshooting/miscellaneous/diagnosing-a-data-discrepancy.md)
* [Een gegevensdiscrepantieticket indienen](https://support.magento.com/hc/en-us/articles/360016506472-Submitting-a-data-discrepancy-ticket)
