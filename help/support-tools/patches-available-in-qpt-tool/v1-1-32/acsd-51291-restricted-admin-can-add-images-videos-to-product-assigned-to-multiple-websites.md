---
title: 'ACSD-51291: beperkte beheerders kunnen afbeeldingen/video''s toevoegen aan producten die zijn toegewezen aan meerdere websites'
description: Pas de ACSD-51291-patch toe om het Adobe Commerce-probleem op te lossen, waarbij beperkte beheerders met toegang tot één website afbeeldingen/video's kunnen toevoegen aan een product dat is toegewezen aan meerdere websites.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: d3cf5009-6b80-4841-95c3-75bb15c9c0a4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# ACSD-51291: beperkte beheerders kunnen afbeeldingen/video&#39;s toevoegen aan producten die zijn toegewezen aan meerdere websites

De ACSD-51291-patch verhelpt het probleem dat een beperkte beheerder met toegang tot één website afbeeldingen/video&#39;s kan toevoegen aan een product dat is toegewezen aan meerdere websites. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-51291. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een beperkte beheerder met toegang tot één website kan afbeeldingen/video&#39;s toevoegen aan een product dat is toegewezen aan meerdere websites.

<u> Stappen om te reproduceren </u>

1. Meld u aan als beheerder.
1. Maak een tweede website, sla deze op en sla de weergave op.
1. Maak een tweede beheerdersrol met alleen bronnen voor de tweede website, de tweede winkel en de opslagweergave.
1. Creeer tweede admin, en wijs het aan de nieuwe beperkte admin rol toe.
1. Maak een nieuw product en wijs dit toe aan zowel de standaardwebsite als de nieuwe website.
1. Log uit van het hoofdbeheerprofiel.
1. Meld u aan als de nieuwe beperkte beheerder.
1. Bewerk het gemaakte product dat aan beide websites is toegewezen.
1. Open de tab **[!UICONTROL Images and Videos]** .

<u> Verwachte resultaten </u>:

* Het volgende bericht wordt weergegeven:

  *Beperkte admin wordt toegestaan om acties met beelden of video&#39;s uit te voeren, slechts wanneer admin rechten op alle websites heeft waaraan het product wordt toegewezen.*

* De knop **[!UICONTROL Add Video]** is niet actief.

<u> Ware resultaten </u>:

De beperkte beheerder kan afbeeldingen en video&#39;s toevoegen, zelfs als het product is toegewezen aan een website waartoe het geen toegang heeft.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
