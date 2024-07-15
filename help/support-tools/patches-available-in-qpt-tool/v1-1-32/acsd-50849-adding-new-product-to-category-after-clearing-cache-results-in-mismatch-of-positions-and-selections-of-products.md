---
title: 'ACSD-50849: Het toevoegen van een nieuw product na het wissen van de cache resulteert in een onjuiste overeenkomst'
description: Pas de ACSD-50849-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het toevoegen van een nieuw product aan de categorie na het wissen van de cache resulteert in een onjuiste weergave van posities en selecties van de bestaande producten.
feature: Cache, Categories, Products
role: Admin
exl-id: 3c797bf4-45da-4500-8c06-8c1007249738
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-50849: het toevoegen van een nieuw product na het wissen van de cache resulteert in een onjuiste overeenkomst

De ACSD-50849-patch verhelpt het probleem dat het toevoegen van een nieuw product aan de categorie na het wissen van de cache resulteert in een onjuiste weergave van posities en selecties van de bestaande producten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) QPT 1.1.32 is geïnstalleerd. De patch-id is ACSD-50849. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een nieuw product aan de categorie toevoegt nadat u de cache hebt gewist, komen de posities en selecties van de bestaande producten niet overeen.

<u> Stappen om </u> te reproduceren:

1. Maak twee producten.
1. Eén product aan een categorie toewijzen.
1. Open de categorie via de beheerder.
1. Maak de cache leeg `bin/magento cache:flush` .
1. Voeg het tweede product toe aan de categorie.

<u> Verwachte resultaten </u>:

De bestaande producten die in de categorie zijn toegewezen, worden niet automatisch verwijderd.

<u> Ware resultaten </u>:

Het eerste (bestaande) product wordt automatisch verwijderd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze basis van de steunkennis zelf te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
