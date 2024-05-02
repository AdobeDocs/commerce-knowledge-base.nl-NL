---
title: "ACSD-54060: Beperkte admin kan product niet opslaan als het kind van een ander product is"
description: Pas de ACSD-54060-patch toe om het Adobe Commerce-probleem op te lossen waarbij een beperkte beheerder een product niet kan opslaan als het een onderliggend product is van een ander product dat is toegewezen aan een ander bereik.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 28fa3c99-f2b6-4c6d-955a-bd6638a1b077
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54060: Beperkte admin kan product niet opslaan als het kind van een ander product is

De ACSD-54060-patch verhelpt het probleem waarbij een beperkte beheerder een product niet kan opslaan als het een onderliggend product is van een ander product dat is toegewezen aan een ander bereik. Deze pleister is beschikbaar wanneer de [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 is geïnstalleerd. De patch-id is ACSD-54060. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met Adobe Commerce-versies:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] lozingen. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beperkte beheerders kunnen een product niet opslaan als het een onderliggend product is van een ander product dat is toegewezen aan een ander bereik.

<u>Stappen om te reproduceren</u>:

1. Maak een extra website.
1. Maak een eenvoudig product en wijs dit toe aan beide websites.
1. Creeer een configureerbaar product met het eenvoudige product als enige variatie, en wijs het configureerbare product aan de standaardwebsite slechts toe.
1. Maak een beperkte gebruiker van de beheerder met alleen toegang tot de tweede website.
1. Meld u aan als gebruiker met beperkte beheerdersrechten.
1. Probeer de eenvoudige productnaam te wijzigen in het tweede websitebereik.

<u>Verwachte resultaten</u>:

De beperkte beheerder kan de productnaam wijzigen.

<u>Werkelijke resultaten</u>:

Er treedt een fout op: *Er zijn meer machtigingen nodig om dit item weer te geven*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de [!DNL Quality Patches Tool] hulplijn.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de handleiding Commerce on Cloud Infrastructure.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool], zie:

* [[!DNL Quality Patches Tool] uitgebracht: een nieuw hulpmiddel om kwaliteitspatches zelf te bedienen](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] hulplijn.
