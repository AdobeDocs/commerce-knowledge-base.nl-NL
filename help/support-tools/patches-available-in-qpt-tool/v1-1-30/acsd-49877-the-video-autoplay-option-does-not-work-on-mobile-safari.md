---
title: 'ACSD-49877: Video autoplay werkt niet op mobiele apparaten  [!DNL Safari]'
description: Pas ACSD-49877 flard toe om de kwestie van Adobe Commerce te bevestigen waar de video autoplay optie niet op mobiele  [!DNL Safari]  werkt wanneer de video direct met een ver videodossier wordt verbonden.
exl-id: 454f7cec-29b9-485b-93be-2a4f2eb77da7
feature: CMS
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877: Automatisch afspelen van video werkt niet op mobiele apparaten [!DNL Safari]

ACSD-49877 verhelpt het probleem dat de optie Automatisch afspelen op mobiele apparaten [!DNL Safari] niet werkt wanneer de video rechtstreeks aan een extern videobestand is gekoppeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30 wordt geïnstalleerd. De patch-id is ACSD-49877. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het pakket [ !magento/quality-patches ] bij naar de nieuwste versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool]: zoek naar patches]. Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Automatisch afspelen van video werkt niet op mobiele apparaten [!DNL Safari] wanneer de video rechtstreeks is gekoppeld aan een extern videobestand en niet aan een streaming service.

<u> Eerste vereisten </u>:
[!DNL Page Builder] -modules zijn geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe CMS-pagina en bewerk de **[!UICONTROL Content Value]** met [!DNL Page Builder] .
1. Voeg a *Lusje* element aan de inhoud toe, en voeg a *VideoElement* binnen het *Lusje* toe.
1. Klik nu op de tandwielknoop om het *VideoElement* uit te geven.
1. Voeg een koppeling naar een MP4-videobestand toe aan het veld [!UICONTROL Video URL] .
1. Merk het **[!UICONTROL Autoplay]** gebied als *ja*.
1. Klik op **[!UICONTROL Save]**.
1. Open de onlangs gemaakte pagina op [!DNL Safari] met een iPhone.

<u> Verwachte resultaten </u>

De optie Automatisch afspelen werkt met [!DNL Safari] in een iPhone.

<u> Ware resultaten </u>

De optie Automatisch afspelen werkt niet bij [!DNL Safari] met een iPhone.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
