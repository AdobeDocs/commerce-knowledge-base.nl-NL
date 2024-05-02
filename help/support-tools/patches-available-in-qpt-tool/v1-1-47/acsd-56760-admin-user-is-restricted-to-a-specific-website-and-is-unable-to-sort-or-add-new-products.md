---
title: 'ACSD-56760: Admin user is limited to a specific website and is unable to sort or add new products'
description: Pas de ACSD-56760-patch toe om het Adobe Commerce-probleem op te lossen waarbij de Admin-gebruiker die beperkt is tot een specifieke website en geen nieuwe producten in een categorie kan sorteren of toevoegen als de webwinkel een eigen hoofdcategorie heeft.
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760: Admin-gebruiker is beperkt tot een specifieke website en kan nieuwe producten niet sorteren of toevoegen

De ACSD-56760-patch verhelpt het probleem waarbij de Admin-gebruiker die beperkt is tot een specifieke website en geen nieuwe producten in een categorie kan sorteren of toevoegen als de webwinkel een eigen hoofdcategorie heeft. Deze pleister is beschikbaar wanneer de [!DNL Quality Patches Tool (QPT)] 1.1.47 is geïnstalleerd. De patch-id is ACSD-56760. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De Admin-gebruiker die beperkt is tot een specifieke website en geen nieuwe producten binnen een categorie kan sorteren of toevoegen als de webwinkel een eigen hoofdcategorie heeft.

<u>Stappen om te reproduceren</u>:

1. Maken *2* websites.
1. Een **[!UICONTROL restricted admin user]** alleen toegang tot *1* website.
1. Aanmelden als **[!UICONTROL restricted admin user]** en probeer de productposities in een categorie te wijzigen.

*Geval 1*:

* *2* winkels.
* *2* hoofdcategorieën, elke website die aan de eigen hoofdcategorie is toegewezen.

*Zaak 2*:

* *2* winkels.
* Alleen *1* de hoofdcategorie wordt toegewezen aan beide websites.

<u>Verwachte resultaten</u>:

* *Geval 1*: De beperkte beheerder moet producten binnen de beschikbare categorie kunnen sorteren.
* *Zaak 2*: De beperkte beheerder kan geen producten binnen de beschikbare categorie sorteren, omdat dit ook de beperkte opslag zal beïnvloeden.

<u>Werkelijke resultaten</u>:

* *Geval 1*: De beperkte beheerder kan geen producten binnen de beschikbare categorie sorteren.
* *Zaak 2*: Beperkte beheerders kunnen producten binnen de beschikbare categorie sorteren, wat van invloed is op de winkels waarvoor beperkingen gelden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
