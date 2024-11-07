---
title: 'MDVA-41164: Kan bedrijf met aangepaste klantkenmerken niet opslaan of bewerken'
description: Met de MDVA-41164-patch wordt het probleem opgelost waarbij de beheerder een bedrijf met aangepaste klantkenmerken van bestanden of afbeeldingen van een willekeurig type niet kan opslaan of bewerken. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41164. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
exl-id: 24338895-68b4-404c-bedd-46cfc7e983a0
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-41164: Kan bedrijf met de attributen van de douaneklanten niet opslaan of uitgeven

Met de MDVA-41164-patch wordt het probleem opgelost waarbij de beheerder een bedrijf met aangepaste klantkenmerken van bestanden of afbeeldingen van een willekeurig type niet kan opslaan of bewerken. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 geïnstalleerd is. De patch-id is MDVA-41164. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruiker kan een bedrijf met aangepaste klantkenmerken van bestanden of afbeeldingen van welk type dan ook niet opslaan of bewerken.

<u> Eerste vereisten </u>:

B2B-module is geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Laat Bedrijf in **opslag** > **Config** > **B2B Eigenschappen** toe.
1. Creeer een klantenattribuut in **Slaat** > **Attributen** > **Klanten** > **toevoegen Nieuw Attribuut**:
   * Invoertype: Bestand (bijlage)
   * Tonen in winkelcentrum: Ja
   * Sorteervolgorde: alle
   * Forms voor gebruik in: alles selecteren
1. Creeer een nieuw bedrijf in **Klanten** > **Bedrijven** > **voeg Nieuw Bedrijf** toe en upload een dossier voor de nieuwe hierboven gemaakte attributen.

<u> Verwachte resultaten </u>:

De gebruiker kan de creatie van het bedrijf voltooien en de gehechtheid wordt geupload zonder enige fout.

<u> Ware resultaten </u>:

* U krijgt een foutenmelding: *het iets ging verkeerd terwijl het bewaren van dossier.*
* Het logboek van de uitzondering bevat een verslag als het volgende:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) in onze ontwikkelingsdocumentatie toe.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze basis van de steunkennis.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
