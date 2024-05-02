---
title: 'ACSD-56621: Bijgewerkte namen worden niet weergegeven in de begroetingkoptekst voor de gebruiker van het bedrijfsbeheer'
description: Pas de ACSD-56621-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de bijgewerkte voornaam en achternaam van de beheerder van het bedrijf niet worden weergegeven in de sectie met begroetingkoppen.
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 4ad9c878-b617-4e6a-939c-be15faf7124b
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56621: Bijgewerkte namen worden niet weergegeven in de begroetingheader voor de gebruiker van het bedrijfsbeheer

De ACSD-56621-patch verhelpt het probleem waarbij de bijgewerkte voornaam en achternaam van de beheerder van het bedrijf niet in de sectie van de begroetingsheader worden weergegeven. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46 is geïnstalleerd. De patch-id is ACSD-56621. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De bijgewerkte namen worden niet weergegeven in de begroetingheader voor gebruikers van bedrijfs-admin.

<u>Stappen om te reproduceren</u>:

1. Ga naar de **[!UICONTROL Admin]** deelvenster.
1. Ga naar **[!UICONTROL Stores]** en selecteert u **[!UICONTROL Configuration]**.
1. Onder de **[!UICONTROL General]** sectie, selecteert u **[!UICONTROL B2B]** om de functionaliteit van B2B-bedrijven mogelijk te maken.
1. Ga naar de **[!UICONTROL Storefront]** en een nieuwe onderneming te registreren.
1. Meld u aan als de beheerder van het bedrijf.
1. Ga naar **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** en wijzigt u de velden voor de voornaam en achternaam naar wens.

<u>Verwachte resultaten</u>:

De voornaam en achternaam van de gebruiker in de sectie van de begroetingsheader worden onmiddellijk gewijzigd.

<u>Werkelijke resultaten</u>:

De voor- en achternaam van de gebruiker worden alleen gewijzigd wanneer de gebruiker zich afmeldt en zich opnieuw aanmeldt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
