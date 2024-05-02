---
title: 'ACSD-50116: een beheerder kan geen URL maken die herschrijft voor de subcategorieën van niveau 3 of lager'
description: Pas de ACSD-50116-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een beheerder geen URL kan maken die herschrijft voor de subcategorieën van niveau drie of lager.
exl-id: 3fa8ebc1-b55d-437e-9dc7-bf6c300b9bbe
feature: Admin Workspace, Categories
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-50116: een beheerder kan geen URL maken die herschrijft voor de subcategorieën van niveau 3 of lager

De ACSD-50116-patch verhelpt het probleem waarbij een beheerder geen URL kan maken die herschrijft voor de subcategorieën van niveau drie of lager. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 is geïnstalleerd. De patch-id is ACSD-50116. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een beheerder kan geen URL maken die herschrijft voor de subcategorieën van niveau drie of lager.

<u>Stappen om te reproduceren</u>:

1. Maak een categoriestructuur met meer dan drie niveaus subcategorieën.
1. Probeer een *[!UICONTROL URL Rewrite]* voor de categorie van niveau 4, waarbij zowel de *[!UICONTROL For Product]* en *[!UICONTROL For Category]* opties.

<u>Verwachte resultaten</u>:

In de categoriestructuur worden de subcategorieën weergegeven tot niveau vier of lager.

<u>Werkelijke resultaten</u>:

In de categoriestructuur worden slechts drie subcategorieën weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
