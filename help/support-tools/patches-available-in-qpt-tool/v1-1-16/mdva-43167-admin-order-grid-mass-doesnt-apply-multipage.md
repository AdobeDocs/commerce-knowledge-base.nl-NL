---
title: 'MDVA-43167: Massa van beheerdersraster is niet van toepassing op meerdere pagina''s'
description: De patch MDVA-43167 verhelpt het probleem waarbij de massaactie van het beheerderordaster niet van toepassing is op meerdere pagina's wanneer de beheerder alle bestellingen selecteert. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 is geïnstalleerd. De patch-id is MDVA-43167. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
exl-id: 58a126db-8a4f-4e20-8fe5-3ce2e25edf7e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# MDVA-43167: Massa van beheerdersraster is niet van toepassing op meerdere pagina&#39;s

De patch MDVA-43167 verhelpt het probleem waarbij de massaactie van het beheerderordaster niet van toepassing is op meerdere pagina&#39;s wanneer de beheerder alle bestellingen selecteert. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16 geïnstalleerd is. De patch-id is MDVA-43167. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De handeling Rastermassa van beheerdervolgorde is niet van toepassing op meerdere pagina&#39;s wanneer de beheerder alle bestellingen selecteert.

<u> Stappen om </u> te reproduceren:

1. Schaf drie keer een product aan om drie bestellingen te maken.
1. Navigeer aan **Net van de Orde van de Verkoop**.
1. Wijzig de paginering in een aangepaste waarde 2.
1. Selecteer alles.
1. Selecteer **Actie van de Massa van de Greep**.

<u> Verwachte resultaten </u>:

Alle drie de orden worden geplaatst op greep.

<u> Ware resultaten </u>:

Slechts worden de twee zichtbare orden geplaatst op greep.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
