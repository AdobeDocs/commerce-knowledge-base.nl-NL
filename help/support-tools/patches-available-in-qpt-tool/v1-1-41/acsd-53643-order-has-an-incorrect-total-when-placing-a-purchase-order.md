---
title: 'ACSD-53643: Het totaal van een bestelling is onjuist wanneer een inkooporder wordt geplaatst'
description: Pas de ACSD-53643-patch toe om het Adobe Commerce-probleem op te lossen waarbij het totaal van de bestelling onjuist is wanneer een inkooporder wordt geplaatst met uitgeschakelde of out-of-stock producten.
feature: B2B
role: Admin, Developer
exl-id: 9843e07a-8a17-401e-98bc-559df5148d34
source-git-commit: 2356ac10b05ae9f38e5c0ca90d9156b0fc405718
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643: het totaal van een bestelling is onjuist bij het plaatsen van een inkooporder

De ACSD-53643-patch verhelpt het probleem waarbij het totaal van de bestelling onjuist is bij het plaatsen van een inkooporder met uitgeschakelde of out-of-stock producten. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41 is geïnstalleerd. De patch-id is ACSD-53643. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het totaal van de bestellingen is onjuist wanneer u een inkooporder plaatst met een product dat uit de oorspronkelijke voorraad of een handicap bestaat.

<u>Stappen om te reproduceren</u>:

1. Installeren *[!UICONTROL B2B]* en *[!UICONTROL Inventory]*.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** en instellen **[!UICONTROL Company]** = *Ja* en **[!UICONTROL Purchase Order]** = *Ja*.
1. Wis configuratiecache.
1. Een nieuw bedrijf maken, dit activeren en inschakelen *[!UICONTROL Purchase order]* voor de onderneming.
1. Maak een nieuwe gebruiker voor het bedrijf.
1. Een *Goedkeuringsregel* alle orders van meer dan *1 USD* door de bedrijfsbeheerder.
1. Maak een extra bron.
1. Meld u aan als nieuwe bedrijfgebruiker.
1. Voeg twee producten aan de kar toe en plaats een kooporder.
1. Schakel het tweede product uit.
1. Meld u aan als bedrijfsbeheerder.
1. Open de kooporder en controleer of de kooporder zowel producten bevat als het totaal voor beide producten.
1. Goedkeuren van de kooporder.
1. Plaats de bestelling.
1. Open de bestelgegevens.

<u>Verwachte resultaten</u>:

* Kan de bestelling niet plaatsen, zelfs niet als één product in de bestelling staat *uitgeschakeld* of *uit voorraad*.
* *[!UICONTROL Place Order]* is verborgen.

<u>Werkelijke resultaten</u>:

De geplaatste order bevat alleen het eerste actieve product, maar het totale ordervolume wordt voor beide producten berekend.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
