---
title: 'MDVA-44940: SQL-fout bij het opslaan van een categorie van beheerder'
description: De MDVA-44940-patch verhelpt het probleem waarbij een SQL-fout optreedt tijdens het opslaan van een categorie via de beheerder. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 is geïnstalleerd. De patch-id is MDVA-44940. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: cae6f231-3b91-441f-af56-824db0fa2d32
feature: Admin Workspace, Categories, Sales Channels
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-44940: SQL-fout bij het opslaan van een categorie van beheerder

De MDVA-44940-patch verhelpt het probleem waarbij een SQL-fout optreedt tijdens het opslaan van een categorie via de beheerder. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 geïnstalleerd is. De patch-id is MDVA-44940. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een SQL-fout op wanneer u een categorie opslaat via de beheerder.

<u> Stappen om </u> te reproduceren:

1. Voorbeeldgegevens installeren.
1. Maak een tweede website waaraan een opslaggroep is toegewezen aan de standaardcategorie.

   * Creeer een opslagmening die aan de nieuwe archiefgroep wordt toegewezen.

1. Maak voorraad en een extra bron die aan deze voorraad is toegewezen en een verkoopkanaal die aan de tweede website is toegewezen.
1. Maak een testproduct dat is toegewezen aan de tweede website.
1. Ga naar **Admin** > **Catalogus** > **Categorieën**, uitgezocht **Werkingsgebied** = **Tweede Website** en ga naar **Producten in Categorie** > **Automatisch Sorteren** > Beweging uit-van-voorraad producten aan de bodem en klik **sparen**.

<u> Verwachte resultaten </u>:

De categorie wordt opgeslagen.

<u> Ware resultaten </u>:

De volgende fout komt voor: *iets ging verkeerd terwijl het bewaren van de categorie*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
