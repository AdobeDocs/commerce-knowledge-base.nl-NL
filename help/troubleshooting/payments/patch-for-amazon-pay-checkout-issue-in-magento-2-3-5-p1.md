---
title: Probleem met afhandeling van afhandeling voor Amazon Pay in Adobe Commerce 2.3.5-p1
description: Deze patch verhelpt het probleem met het feit dat een betalingsmethode niet kan worden gewijzigd bij het afrekenen van de stap "Controleren en betalen" uit de widget voor betalingen, terwijl je kunt uitchecken met Amazon Pay in Adobe Commerce.
exl-id: a241f67f-019c-4ff2-a5ad-e7dc71639768
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Probleem met afhandeling van afhandeling voor Amazon Pay in Adobe Commerce 2.3.5-p1

Deze patch verhelpt het probleem met het feit dat een betalingsmethode niet kan worden gewijzigd bij het afrekenen van de stap &quot;Controleren en betalen&quot; uit de widget voor betalingen, terwijl je kunt uitchecken met Amazon Pay in Adobe Commerce.

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure versie 2.3.5-p1
* Adobe Commerce on-premisse versie 2.3.5-p1

## Probleem

Wanneer een winkelier uitcheckt met Amazon Pay, zich aanmeldt, naar de betalingsstap gaat en probeert zijn betaalcreditcard te wijzigen van de widget betalingen, wordt een foutbericht weergegeven. Het afrekenen kan niet worden voltooid als de winkelier de fout negeert en verder gaat met het afrekenen.

Om deze kwestie op te lossen en de fout te verwijderen, hebben wij a [ flard ](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip) gecreeerd.

<u> Stappen om </u> te reproduceren:

1. Afhandeling starten met Amazon Pay.
1. Aanmelden als Amazon Pay-klant.
1. Selecteer de verzendmethode en ga verder met de betalingsstap.
1. Probeer de creditcard te wijzigen in een andere.

<u> Verwacht resultaat </u>: Een verschillende creditcard wordt geselecteerd als betalingsmethode zonder een fout.

<u> Ware resultaat </u>: Het foutenbericht verschijnt: *&quot;Gelieve te contacteren deze handelaar voor hulp die uw orde voltooit.&quot;*

## Oplossing

[ pas het flard ](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip) hieronder toe.

## Reparatie

De patch is aan dit artikel gekoppeld. Als u het bestand wilt downloaden, schuift u omlaag naar het einde van het artikel en klikt u op de bestandsnaam of op de volgende koppeling:

[BUNDLE-2554\_EE\_2.3.5-p1.composer.patch downloaden](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)

### Compatibele Adobe Commerce-versies:

De patch is gemaakt voor:

* Adobe Commerce on cloud Infrastructure versie 2.3.5-p1
* Adobe Commerce on-premisse versie 2.3.5-p1

De patch is ook compatibel (maar lost het probleem mogelijk niet op) met de volgende Adobe Commerce-versies en -versies:

* Adobe Commerce on cloud Infrastructure versie 2.3.5
* Adobe Commerce versie 2.3.5 (ter plaatse)

## Hoe de pleister aanbrengen

Zie [ hoe te om een componentenflard toe te passen die door Adobe Commerce ](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) in onze steunkennisbasis voor instructies wordt verstrekt.

## Bijgevoegde bestanden
