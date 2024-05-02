---
title: 'MDVA-31236: beheerders kunnen 2FA niet instellen of aanmelden'
description: De MDVA-31236-patch verhelpt het probleem dat Commerce-beheerders met aangepaste resourcetoegang niet kunnen instellen [2-factor verificatie (2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html) of aanmelden. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd.
exl-id: b75d7a19-3c17-4389-b359-7aeeb8797539
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# MDVA-31236: beheerders kunnen geen 2FA instellen of zich aanmelden

De MDVA-31236-patch verhelpt het probleem dat Commerce-beheerders met aangepaste resourcetoegang niet kunnen instellen [tweefasenverificatie (2FA)](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html) of aanmelden. Deze pleister is beschikbaar wanneer de [Kwaliteitspatches (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12 is geïnstalleerd.

## Betrokken producten en versies

**De patch wordt gemaakt voor Adobe Commerce-versie:** Adobe Commerce on cloud Infrastructure 2.4.0.

**Compatibel met Adobe Commerce-versies:** Adobe Commerce op locatie en Adobe Commerce op cloudinfrastructuur 2.4.0-2.4.1.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u de `magento/quality-patches` het pakket aan de recentste versie en controleer verenigbaarheid op [[!DNL Quality Patches Tool]: Pagina met patches zoeken](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers zonder beheerdersrechten kunnen momenteel hun persoonlijke 2FA-toegang niet instellen. 2FA zoals uitgevoerd in Adobe Commerce omvat twee ACL rollen. Één rol beïnvloedt globale systeemconfiguratie, en het is nodig slechts wanneer het vormen van het systeem. De tweede ACL rol beïnvloedt individuele gebruiker 2FA rekeningen. Een admin gebruiker moet dit tweede type van 2FA ACL vormen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [Software Update Guide > Patches toepassen](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie.
* Adobe Commerce op cloudinfrastructuur: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [Release-gereedschap Kwaliteitspatches: een nieuw gereedschap voor het zelf bedienen van kwaliteitspatches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in onze kennisbasis voor ondersteuning.
* [Controleer of er een patch beschikbaar is voor uw Adobe Commerce-probleem met het gereedschap Kwaliteitspatches](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in onze kennisbasis voor ondersteuning.

Voor informatie over andere patches die beschikbaar zijn in QPT, raadpleegt u de [Patches beschikbaar in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
