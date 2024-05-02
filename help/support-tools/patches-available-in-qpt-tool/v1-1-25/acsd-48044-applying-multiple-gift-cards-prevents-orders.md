---
title: 'ACSD-48044: het toepassen van meerdere cadeaukaarten voorkomt dat orders worden geplaatst'
description: Pas de ACSD-48044-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het toepassen van meerdere cadeaukaarten op één bestelling met meerdere verzendingen ertoe leidt dat bestellingen niet kunnen worden geplaatst.
exl-id: fe57063c-d69c-4b80-a59c-912c2603f6af
feature: Admin Workspace, Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-48044: het toepassen van meerdere cadeaukaarten voorkomt dat orders worden geplaatst

De ACSD-48044-patch verhelpt het probleem dat het toepassen van meerdere cadeaukaarten op één bestelling met meerdere verzendingen ertoe leidt dat bestellingen niet kunnen worden geplaatst. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25 is geïnstalleerd. De patch-id is ACSD-48044. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u meerdere cadeaukaarten op één bestelling met meerdere verzendingen toepast, kunnen geen bestellingen worden geplaatst.

<u>Stappen om te reproduceren</u>:

1. Installeer een schone versie van Adobe Commerce.
1. Maak een eenvoudig product met een prijs van $100 en een ander eenvoudig product met een prijs van $10.
1. Aanmelden bij de [!UICONTROL Admin panel] en maak twee cadeaukaarten.

   * 02KB8M0H0GRD = $50
   * 00GXM6SUGBLW = $ 25

1. Maak een klant met twee adressen.
1. Voeg twee producten aan de kar toe.

   * Voeg eerst het product $10 toe en voeg vervolgens het product $100 toe. De uitgave kan niet worden gereproduceerd als eerst het product van $100 wordt toegevoegd.

1. Ga naar het winkelwagentje en voeg de twee cadeaukaarten toe die u hebt gemaakt.
1. Klikken op **[!UICONTROL Ship to Multiple Addresses]** op de winkelwagentje.
1. Wijs elk product aan een verschillend adres toe.
1. Ga naar de **[!UICONTROL Shipping information]** pagina.
1. Ga naar de **[!UICONTROL Billing information]** pagina.
1. Ga naar de **[!UICONTROL Review Your Order]** pagina, waar u de uitgave kunt zien.
1. Plaats de bestelling.

<u>Verwachte resultaten</u>:

* Cadeaukaarten worden correct toegepast op het totale bedrag.
* Bestellingen worden geplaatst.

<u>Werkelijke resultaten</u>:

Cadeaubedragen worden gemengd met een fout *&quot;Corrigeer de code van de cadeaukaart.&quot;* wanneer u de bestelling plaatst.

* Eerste product:

   * Creditcard verwijderen (00GXM6SUGBLW) - $15.00
   * Cadeaukaart verwijderen (02KB8M0H0GRD) - $0,00

* Tweede product:

   * Creditcard verwijderen (00GXM6SUGBLW) - $ 25,00
   * Cadeaukaart verwijderen (02KB8M0H0GRD) - $ 35,00

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
