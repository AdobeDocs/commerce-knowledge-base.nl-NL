---
title: 'ACSD-54060: Beperkte admin kan product niet opslaan als het kind van een ander product is'
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

De ACSD-54060-patch verhelpt het probleem waarbij een beperkte beheerder een product niet kan opslaan als het een onderliggend product is van een ander product dat is toegewezen aan een ander bereik. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-54060. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beperkte beheerders kunnen een product niet opslaan als het een onderliggend product is van een ander product dat is toegewezen aan een ander bereik.

<u> Stappen om </u> te reproduceren:

1. Maak een extra website.
1. Maak een eenvoudig product en wijs dit toe aan beide websites.
1. Creeer een configureerbaar product met het eenvoudige product als enige variatie, en wijs het configureerbare product aan de standaardwebsite slechts toe.
1. Maak een beperkte gebruiker van de beheerder met alleen toegang tot de tweede website.
1. Meld u aan als gebruiker met beperkte beheerdersrechten.
1. Probeer de eenvoudige productnaam te wijzigen in het tweede websitebereik.

<u> Verwachte resultaten </u>:

De beperkte beheerder kan de productnaam wijzigen.

<u> Ware resultaten </u>:

Een fout komt voor: *Meer toestemmingen zijn nodig om dit punt* te bekijken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
