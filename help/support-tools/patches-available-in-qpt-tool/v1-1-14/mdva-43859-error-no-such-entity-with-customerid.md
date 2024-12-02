---
title: 'MDVA-43859: Fout "Geen dergelijke entiteit met customerId ="het programma wordt geopend wanneer de geschrapte klant het programma opent'
description: De patch MDVA-43859 lost het probleem op waar fout *No zulk een entiteit met customerId =* wordt geregistreerd wanneer een geschrapte klant probeert om binnen te registreren. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43859. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
exl-id: 62c4b6ee-88a0-40b8-9eb2-37b6cefa0b83
feature: Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-43859: Fout &quot;Geen dergelijke entiteit met customerId =&quot;het programma wordt geopend wanneer de geschrapte klant het programma opent

Het flard MDVA-43859 bevestigt de kwestie waar de fout *geen dergelijke entiteit met customerId =* wordt geregistreerd wanneer een geschrapte klant probeert om binnen te registreren. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14 geïnstalleerd is. De patch-id is MDVA-43859. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De fout *geen dergelijke entiteit met customerId =* wordt geregistreerd wanneer een geschrapte klant probeert om binnen te registreren.

<u> Stappen om </u> te reproduceren:

1. Maak een klantenaccount aan de voorzijde.
1. Meld u af en meld u aan bij de klantenaccount die u in stap 1 hebt gemaakt.
1. Laad de backend in een andere browser en ga naar het klantenraster.
1. Verwijder de klant die u in stap 1 hebt gemaakt.
1. Ga terug naar de eerste browser en probeer u af te melden.

<u> Verwachte resultaten </u>:

De klant wordt zonder fout omgeleid naar de aanmeldingspagina.

<u> Ware resultaten </u>:

De klant krijgt de volgende fout: *geen dergelijke entiteit met customerId =*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar [ die flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in onze ontwikkelaarsdocumentatie.
