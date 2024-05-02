---
title: '''ACSD-53583: Verbeter gedeeltelijke herindexprestaties voor [!UICONTROL Category Products] en [!UICONTROL Product Categories] indexeerders'
description: Pas de ACSD-53585-patch toe om de gedeeltelijke herindexprestaties voor de indexen van de Categorieën van Producten en van de Categorieën te verbeteren.
feature: Products, Categories
role: Admin, Developer
exl-id: 1c8f7df3-379f-42d6-8b41-286d34f725d2
source-git-commit: 29c2918ccae6404f6ae87d360ac16b149de5dd0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53583: Verbeteren van de gedeeltelijke herindexeerprestaties voor de indexen van de Producten van de Categorie en van de Categorieën

De ACSD-53583-patch verbetert de gedeeltelijke herindexprestaties van *Categorieproducten* en *Productcategorieën* indexeerders. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.39 is geïnstalleerd. De patch-id is ACSD-53583. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3
* Niet compatibel met [!DNL Live Search] -module. Om deze pleister aan te brengen op [!DNL Live Search] voor de installatie een extra ACSD-55719-patch aanvragen.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gedeeltelijke herdex vergt meer tijd dan volledige herdex.

<u>Stappen om te reproduceren</u>:

1. Alle indexen inschakelen *Bijwerken op schema*.
1. Gegevens genereren met de [!DNL Performance Toolkit] (gemiddeld profiel).
1. Breng wijzigingen aan in alle producten en categorieën, zodat deze zich in de indexachterstand bevinden en alle indexen inactief zijn.
1. Gedeeltelijke herindexering uitvoeren voor *Categorieproducten* en *Productcategorieën* indexeerders.

<u>Verwachte resultaten</u>:

Gedeeltelijke herdex wordt één keer per product aangeroepen en neemt bijna dezelfde tijd in beslag als volledige herdex, omdat alle producten en categorieën zijn gewijzigd.

<u>Werkelijke resultaten</u>:

Partiële redex wordt vele malen per product aangeroepen en neemt meer tijd in beslag dan volledige redex.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
